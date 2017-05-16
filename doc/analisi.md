# REPSTOR

## Premessa
In base ad una richiesta emersa in seno ad una riunione dell'Italian Linux Society, è stato richiesto di sviluppare l'analisi per lo sviluppo di uno strumento in open source per l'archiviazione sostitutiva.

## Sommario
* [L'utility](#utility)
* [Esempio d'uso](#esempio)
* [Sintassi del comando](#sintassi)
* [Configurazione](#configurazione)
* [Variabili d'ambiente](#macro)
* [Informazioni tecniche](#informazioni_tecniche)
* [Fasi e tempi di sviluppo](#fasi)
* [Providers supportati](#providers)
* [Tests](#tests)

<a name="utility"></a>
## L'utility
In stile Unix, l'utility, nella sua forma finale, si presterà per essere impiegabile come comando bash, demone per client web o GUI locale.

<a name="esempio"></a>
## Esempio d'uso
Uso semplice:
```text
        >repstor filename
        Archiviazione assegnata al job 1674837
        Usare il comando status per monitorare l'avanzamento.
```
In questo caso vengono impiegate le specifiche di default espresse nel file di configurazione **/etc/repstor.conf**.

Questa forma, abbinata eventualmente al parametro -p, si presta alla facile implementazione di una voce di menu contestuale del file manager o di un plugin da abbinare al proprio sito web (si pensi ad esempio ad owncloud).

Uso in modalità terminale:
```text
        >repstor
        provider acme               # sceglie destinazione
        doctype "Doc Generico"
        field documentid "pdftest"
        file filename
        group                       # raggruppa in singolo documento
        field documentid @filename  # macro
        files ".*txt|.*pdf"         # match tramite regexp
        send
        quit
```
Nello stadio finale dell'evoluzione, i metadati associati ai documenti, potranno essere estrapolati da un file adiacente con estensione **.repstor** o xml o incluso nel file stesso, in caso di zip o appresi dal suo interno impiegando tools di estrazione.

<a name="sintassi"></a>
## Sintassi del comando
```text
-h,--help
    mostra l'elenco seguente
--settings  
    stampa il testo completo per la configurazione
-i,--install
    configura o riconfigura il servizio o l'attività dello schedulatore in base alla configurazione
-d,--doctype "tipo documento"
-m,--field metadato valore|macro
-f,--file "nome file"
-F,--files "espressione regolare"
-s,--send
-g,--group
    l'archiviazione può avvenire per singolo file (1 file -> 1 job)
    oppure può essere cumulativa (più files -> 1 zip -> 1 job);
    nel caso di accumulo, il provider può avere dei limiti di 
    dimensione
-p,--provider nome_del_provider|nome_del_profilo
--doctypes
    elenca i tipi di documento (possibilmente filtrati per tipo supportati dal contratto con il provider)
--fields "tipo documento"
    elenca i metadati associabili al tipo di documento
-S,--summary
    mostra una tabella numerica riassuntiva dei documenti inviati, da conservare, in conservazione e falliti
-u,--update
    aggiorna l'archivio locale dello stato dei documenti
--status
    elenca lo stato delle spedizioni da archivio locale o da provider se possibile, eventualmente filtrato

filters:
questo gruppo di comandi influenza il risultato dei comandi summary e status
--start_date    data di inizio intervallo
--end_date      data di fine intervallo
--days numero   numero di giorni precedenti alla data corrente
--waiting       intervallo di archivi pendenti o in fase di archiviazione
--stored        intervallo di archivi in conservazione
--failing       intervallo di archivi in errore
--jobid         filtra una specifica spedizione e modifica l'output di --status
--docid         filtra uno specifico documento e modifica l'output di --status
--csv           mostra elenco in formato csv
--json          mostra elenco in formato json
Anche file,files e field concorrono come filtri
```

Esempio formato di output del comando status:


|Provider|Sistema|#|Titolo|ID Job|Stato Job|Errore |Aggiornato       |Inviato          |
|--------|-------|-|------|------|---------|-------|-----------------|-----------------|
|SIA     |eDK    |1|pdftst|      |         |Srv.N/D|11.11.16 00:13:20|                 |
|SIA     |eDK    |1|pdftst|123221|completo |0000001|In conservazione |11.11.16 11:32:39|11.11.16 11:32:39|

Esempio formato di output del comando status modificato da jobid e docid

|Provider|Sistema|JobId |DocId|field01|field02|...|
|--------|-------|------|-----|-------|-------|---|
|SIA     |eDK    |123221|    1|       |       |   |


<a name="configurazione"></a>
## Configurazione
Prototipo d'esempio del contenuto del file /etc/repstor.conf:
```INI
    [service]
    update_times =              # formato cron
    daemon =                    # abilita/disabilita il servizio di sistema
    webservice =                # abilita/disabilita il servizio web
    webinterface =              # abilita/disabilita l'interfaccia web
    
    [providers]
    acme = "Descrizione"
    
    [acme]                      # specifiche provider
    storage_ws =                # url webservice archiviazione
    storage_monitor_url =
    storage_user =
    storage_password =
    storage_farm_code =
    
    time_stamp_ws =
    time_stamp_user =
    time_stamp_password =
    
    notify_type =               # smtp|file|sms|wapp|telegram|url|pec|db
    notify_server =
    notify_port =
    notify_user =
    notify_password =
    notify_protection_type =
        
    #
    # parametri configurazione documenti
    # completano eventuale elenco fornito da provider
    #

    doctype_01_code = "001"
    doctype_01_description = "Doc generico" 
    # assegnazione tipo di documento in base al nome dell'archivio
    doctype_01_match= ".*"      # regexp sul nome dell'archivio
    doctype_01_parser=
    field_01_01_name =
    field_01_01_value =
    # ...

    # parametri avanzati per gestione temporanei, log, db

    temp_path =
    log_path =
    db_origin = # user:password@server:ip/database
    
    #
    
```
<a name="macro"></a>
## Variabili d'ambiente
Le variabili d'ambiente, identificate dal simbolo @, sono impostate dal programma,
acquisendo i valori dalla configurazione o dai parser esterni.

* **@filename**             nome archivio
* **@doctype**              tipo documento
* **@doctype_code**         codice tipo documento
* **@field_01_name**        il relativo valore dai settings
* **@field_01_value**       il relativo valore dai settings
* **@field_value(name)**    valore campo specificato tra parentesi tonde, impostato nella configurazione o ottenuto dal parser esterno

<a name="informazioni_tecniche"></a>
## Informazioni tecniche
Il codice sorgente sarà prodotto in C# o Python. Si cercherà di mantenere linearità tra i parametri del comando, i comandi da terminale e le web api.

<a name="fasi"></a>
## Fasi e tempi di sviluppo
Le fasi(Fs) di sviluppo sono suddivise per blocchi di lavoro di circa un mese ciascuno. Tranne per le fasi cruciali, le opzionali possono essere eseguite in ordine differente, in parallelo e da team differenti. Alcune fasi opzionali possono anche durare meno, in relazione alla conoscenza diretta dello sviluppatore dell'ambiente di riferimento.

|Fs |Attività                                                                                      |Importanza|
|---|----------------------------------------------------------------------------------------------|----------|
|   |analisi                                                                                       |principale|
|1  |libreria e comandi file, files, doctype, doctypes, field, send, status, update, help, settings|basilare  |
|2  |comandi install, summary, start_date, end_date, days, waiting, stored, failing, csv, json     |basilare  |
|3  |modalità terminale, comando group,modalità webservice (integrata)                             |opzionale |
|4  |script o plugin per gnome,mate,owncloud etc.                                                  |opzionale |
|5  |interfaccia minimale web bootstrap+knockout,con dashboard,filtro per comandi summary e status |opzionale |
|6  |tests per funzionalità base, su vari sistemi e providers                                      |opzionale |
|7  |estensione ad più providers                                                                   |opzionale |
|8  |supporto man e pacchettizzazione (deb,pip,nuget,altro)                                        |opzionale |
|9  |parametri configurazione avanzati e file .repstor                                              |opzionale |

<a name="providers"></a>
## Providers supportati
* Gruppo SIA(accreditato Agid)
    * sistema [eDK]: archiviazione sostitutiva
    * sistema eIS: fatturazione elettronica

<a name="tests"></a>
## Tests
I tests riguardano sia il controllo delle funzionalità per singolo provider, sia il buon funzionamento nel sistema operativo d'uso.

Attualmente sono supportati i seguenti sistemi operativi:

    * Ubuntu (probabilmente funzionante anche su Debian e derivate)


----------------------------------------------------------------------------------
[eDK]: https://www.sia.eu/it/soluzioni/gestione-documentale/conservazione-digitale/conservazione-digitale
[ILS]: https://www.ils.org/
