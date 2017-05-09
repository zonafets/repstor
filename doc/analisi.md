REPSTOR
=======

Premessa
--------
In base ad una richiesta emersa in seno ad una riunione dell'Italian Linux Society, è stato richiesto di sviluppare l'analisi per lo sviluppo di uno strumento in open source per l'archiviazione sostitutiva.

L'analisi cercherà di coprire tutto il processo vitale di un'applicazione che riguardano anche installazione e test.

Sommario
--------
* L'utility
* Esempio d'uso
* [Sintassi del comando](#sintassi)
* Configurazione
* Informazioni tecniche
* Fasi e tempi di sviluppo
* Providers supportati
* Tests

L'utility
---------
In stile Unix, l'utility, nella sua forma finale, si presterà per essere impiegabile come comando bash, demone per client web o GUI locale.

Esempio d'uso
-------------
Uso semplice:

        >repstor filename
        Archiviazioner assegnata al job 1674837
        Usare il comando status per monitorare l'avanzamento.

In questo caso vengono impiegate le specifiche di default espresse nel file di configurazione **/etc/repstor.conf**.

Questa forma, abbinata eventualmente al parametro -p, si presta alla facile implementazione di una voce di menu contestuale del file manager o di un plugin da abbinare al proprio sito web (si pensi ad esempio ad owncloud).

Uso in modalità terminale:

        >repstor
        doctype "Doc Generico"
        field documentid "pdftest"
        file filename
        group                       # raggruppa in singolo documento
        field documentid $filename  # macro
        files ".*txt|.*pdf"         # regexp
        send
        quit

Nello stadio finale dell'evoluzione, i metadati associati ai documenti, potranno essere estrapolati da un file adiacente con estensione **.repstor** o xml o incluso nel file stesso, in caso di zip o appresi dal suo interno impiegando tools di estrazione.

<a name="sintassi"></a>
Sintassi del comando
--------------------
        >repstor --help
        commands:
            -h,--help  mostra l'elenco seguente
            --settings  stampa il testo completo per la configurazione
            -i,--install
                configura o riconfigura il servizio o l'attività dello schedulatore in base alla configurazione
            -d,--doctype "tipo documento"
            -m,--field metadato valore|macro
            -f,--file "nome file"
            -F,--files "espressione regolare"
            -s,--send
            -g,--group
                l'archiviazione può avvenire per singolo file (1 file -> 1 job)
                oppure può essere comulativa (più files -> 1 zip -> 1 job);
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
                elenca lo stato dei documenti da archivio locale o da provider se possibile
            
            filters:
            questo gruppo di comandi influenza il risultato dei comandi summary e status
            --start_date    data di inizio intervallo
            --end_date      data di fine intervallo
            --days numero   numero di giorni precedenti alla data corrente
            --waiting       intervallo di archivi pendenti o in fase di archiviazione
            --stored        intervallo di archivi in conservazione
            --failing       intervallo di archivi in errore
            --csv           mostra elenco in formato csv
            --json          mostra elenco in formato json
            Anche file,files e field concorrono come filtri
        
Esempio formato di output del comando status:


|Provider|Sistema|#|Titolo|ID Job|Stato Job|ID Doc.|Stato Doc.      |Errore |Aggiornato|Inviato|
|--------|-------|-|------|------|---------|-------|----------------|-------|------------|-------|
|SIA     |eDK    |1|pdftst|      |         |       |                |Srv.N/D|11.11.16 00:13:20|
|SIA     |eDK    |1|pdftst|123221|completo |0000001|In conservazione|       |11.11.16 11:32:39|11.11.16 11:32:39|


Configurazione
--------------
Prototipo d'esempio del contenuto del file /etc/repstor.conf:

    [service]
    update_times =              # formato cron
    
    [providers]
    acme = "Descrizione"
    #default =                  # in caso di più provider 
    
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
    
    
    
Informazioni tecniche
---------------------
Il codice sorgente sarà prodotto in C# o Python. Si cercherà di mantenere linearità tra i parametri del comando, i comandi da terminale e le web api.

Fasi e tempi di sviluppo
------------------------
Le fasi(Fs) di sviluppo sono suddivise per blocchi di lavoro di circa un mese ciascuno. Tranne per le fasi cruciali, le opzionali possono essere eseguite in ordine differente, in parallelo e da team differenti. Alcune fasi opzionali possono anche durare meno, in relazione alla conoscenza diretta dello sviluppatore dell'ambiente di riferimento.

|Fs |Attività                                               |Importanza|
|---|-------------------------------------------------------|----------|
|0  |analisi                                                |principale|
|1  |libreria e comandi file,files,doctype,doctypes,field   |basilare  |
|   |send, status, update, help, settings                   |          |
|2  |comandi install,summary,start_date,end_date,days,      |basilare  |
|   |waiting,stored,failing,csv,json                        |          |
|3  |modalità terminale, comando group,                     |opzionale |
|   |modalità webservice (integrata)                        |          |
|4  |script o plugin per gnome,mate,owncloud etc.           |opzionale |
|5  |interfaccia minimale web bootstrap+knockout,           |opzionale |
|   |con dashboard,filtro per comandi summary e status      |          |
|6  |tests per funzionalità base, su vari sistemi           |opzionale |
|   |e providers                                            |          |
|7  |estensione ad più providers                            |opzionale |
|8  |supporto man e pacchettizzazione (deb,pip,nuget,altro) |opzionale |

Providers supportati
--------------------
* Gruppo SIA(accreditato Agid)
    * sistema [eDK]: archiviazione sostitutiva
    * sistema eIS: fatturazione elettronica
    
Tests
-----
I tests riguardano sia il controllo delle funzionalità per singolo provider, sia il buon funzionamento nel sistema operativo d'uso.

Attualmente sono supportati i seguenti sistemi operativi:

    * Ubuntu (probabilmente funzionante anche su Debian e derivate)


----------------------------------------------------------------------------------
[eDK]: https://www.sia.eu/it/soluzioni/gestione-documentale/conservazione-digitale/conservazione-digitale
[ILS]: https://www.ils.org/