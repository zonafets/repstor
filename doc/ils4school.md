# Software libero per la gestione scolastica

### Revisioni
| AAMMGG | N.Cognome       | Modifica                                         |
|--------|-----------------|--------------------------------------------------|
| 170518 | S.Zaglio        | Mod. a “Perchè software libero e aperto”         |
| 170516 | S.Zaglio        | Revisione ortografica                            |
| 170421 | S.Zaglio        | Bozza                                            |

### Gestione segreteia scolastica

### Scopo
L'evoluzione informatica italiana, porta la scuola a doversi dotare di strumenti più complessi che riguardino anche la gestione della segreteria. Oltre al registro elettronico open source, altri strumenti sono necessari:

  * firma elettronica
  * archiviazione sostitutiva
  * gestione segreteria
  	* workflow
  	* fatturazione
  	
### Perché software libero e aperto
La primaria funzione di una scuola è l'apprendimento. Mentre ad oggi quasi nessun individuo si porta appresso taccuino e penna, sempre più giovani sono dotati di smartphone. L'informatica non è più una conoscenza riservata ai tecnici. Il software a codice aperto e quindi studiabile, non è preconfezionato ma allo stesso tempo non è fortemente dipendente da una specifica linea di condotta personale. Il software proprietario obbliga, oltre al costo di licenza, anche a quello per l'installazione e manutenzione. Vi si aggiunge eventuale costo per personalizzazione oppure all'adeguamento. Può obbligare all'acquisto di funzionalità non richieste. L’installatore diventa rivenditore. Il software libero comporta necessariamente auto formazione. Con ciò l'attività viene equamente ripartita tra tecnico e utente, valorizzandone il lavoro. Nel software proprietario il maggior valore è dato al prodotto  e diviene sempre più questione di brand. Poiché il valore è anche un costo, nel caso del OS ha un ritorno diretto.
La crescita costante del software libero e la sua adozione da parte dei grandi produttori, anche del settore informatico, dimostra che quando la valorizzazione del prodotto supera la sua reale utilità, non c'è benefico.
Le comunità di sviluppo rappresentano poi esempi di applicazione di organizzazioni democratiche e dei relativi vantaggi economici.
Linux si pone, nel suo modo si essere, come un engine for state machine workflow. Non è facile, ma può essere personalizzato a piacere. Non è caso è divenuto cuore e cervello di molti dispositivi casalinghi come le smarttv.
Il suo impiego nei pubblici uffici ha un potenziale ben superiore a quello del software proprietario. Ha solo bisogno di essere scoperto. 
Il maggior ostacolo è dato dal fatto che la libertà non è un bene che si possa vendere con l’idea di trarre facile profitto.

### Pagina wiki(pedia) per la scuola
Quando si cerca un software specifico, ad esempio per l'editig video, sono apprezzabili le pagine schematiche che mettono a confronto i prodotti esistenti. Sarebbe utile, anche come ricerca per uno o più studenti, cooperando magari tra più scuole, creare una knowledge base simile per i software utili alla didattica.
Si può partire dal seguente elenco:

* https://github.com/Kickball/awesome-selfhosted

da cui la parte forse ancor più utile:

* https://github.com/Kickball/awesome-selfhosted#task-managementto-do-lists 

### Linuxschool (korishi server) e Sodilinux
Questi specifici strumenti hanno un limite proprio nella loro specializzazione. Sebbene sarebbe bello avere una distribuzione nostrana, utile anche a capitalizzare di più, rimanere al passo con la crescente complessità rende difficile competere con grandi organizzazioni supportate da grandi comunità.

### Perché Ubuntu Friendly
Linux è free, non gratis.
La natura "aperta" ottimizza i costi distribuendoli e riciclando il più possibile, ma non li azzera. Apple fa largo uso di prodotti OS, lo si legge nei credits dell'iPhone. Ubuntu ha un certo successo nel mondo desktop perchè è "windows friendly" ma anche perchè i prodotti presenti nel software center sono certificati per la sicurezza e qualità.
Ci sono altre distribuzioni che, come Ubuntu sono basate su Debian o addirittura su Ubuntu, ma con una veste grafica che ha un maggior appeal estetico. Ma quanto può durare?
In caso di problemi, una semplice ricerca su google con i termini
tutorial o solved o “apt-get” o copiando e incollando il messaggio d'errore, portano ad un veloce soluzione, anche semplicemente quando la soluzione non c'è.
Per piccole stazioni, l'ambiente Windows può essere virtualizzato in maniera trasparente tramite emulatori come wine o virtualbox.
Specifiche workstation, come il server, avranno invece un'assistenza specializzata. Windows e Linux possono convivere nello stesso ufficio o sulla stessa macchina oppure sul server come macchine virtuali.
Le soluzioni sono tante e non ci si può soffermare solo su questioni estetiche.

### La leggerezza di Linux
Scaricare una ISO per testarla in una virtual machine da far regredire velocemente è quasi all'ordine del giorno. Le esigue richieste di risorse di linux lo rendono comodo da manutenere in un ambiente virtuale. In alternativa la stratificazione come quella operate da docker o snap sembra la direzione da prendere e da ulteriore valore.

## Perché non RedHat o altro?
Perché non zOS per i super computer dell'IBM? Perchè sono aziendali. Vanno bene per una struttura come un Comune, ma non per una piccola attività come una scuola. Comunque ogni grande struttura si organizza necessariamente in divisioni, reparti o filiali, spesso anche autonome.
Ciò non toglie che ognuno decida in autonomia, purché la conoscenza venga condivisa.

### Knowledge sharing e tutorials sul software per la scuola
Siti del tipo Q&A mostrano che il caos del forum può essere focalizzato al risultato pur in autogestione. Quando c'è un buon tutorial da seguire, la linea di comando non è più ostacolo ma anzi mezzo propulsivo.
Un grande progetto condiviso tra le scuole con radice negli istituti tecnici, potrebbe essere quello di manutenere un sito web o un progetto github con i tutorials.

### Una collaborazione nazionale
Sarebbe auspicabile una collaborazione tra itis, università e operatori esperti, reperiti nei LUGs. Scegliendo un docente come project manager e un consulente esterno come program manager, diverrebbe esperienza di lavoro più utile di uno stage, per lo o gli studenti coinvolti nel progetto, utile a divenire anche tesi di diploma. Poiché con il movimento CoderDojo nato in Irlanda, si diventa programmatori a cinque anni, sarebbe oneroso per l'evoluzione civile, far attendere una risorsa per dieci anni, più altri cinque di apprendistato, prima di considerarla produttiva.

### Quale soluzione server in definitiva?
A mio avviso, la miglior proposta per una scuola è adottare una distribuzione server standard e corredarla di tutorials per l'installazione dei prodotti, soprattutto per:

	* gestione gli assets
	* ERP adeguato all'Italia (o l'italiano invoicex ad esempio)
	* web manager per le operazioni più semplici demandandoli ad un utente avanzato
	* registro elettronico
	* firma digitale
	* gestione workflow
	* soluzione cloud
	* archiviazione sostitutiva
	* compilazione pdf
	* print server

### Gestione assets
Nelle piccole realtà, questa attività si fa generalmente con un foglio Excel/Calc. La facilità con cui si modificano accidentalmente le tabelle o la difficoltà a rendere bloccate o auto-compilate alcune celle, li rende vulnerabili. Non poter approntare poi una app o una maschera accessibile da dispositivo mobile, limita poi la tracciabilità. Sharepoint rappresentava uno strumento più ideale da questo punto di vista e sarebbe utile cercare una alternativa. Tuttavia assegnarne lo sviluppo come attività di laboratorio avrebbe diversi benefici.

### ERP adeguato all'Italia
ERPNext ha una configurazione specifica per la scuola. E' da verificare se questa possa essere completa per l'ambito italiano. Vi è una società milanese che lo segue come prodotto. Sarebbe utile una collaborazione con le segreterie scolastiche. Ciò può anche solo produrre una richiesta di miglioramento agli sviluppatori e una raccolta di fondi comune.
In alternativa si parla spesso di un prodotto free, non opensource di un'azienda italiana, scritto in Java e multi-piattaforma, di nome Invoicex.

### Web manager
Aspetti come la creazione degli utenti, può essere demandata ad un utente avanzato, formato da un tutorial specifico. Sarebbe uno spreco di risorse pagare più volte un consulente esterno per questo ripetitivo  tipo di attività.

### Registro elettronico
Il registro (LampSchool) messo a disposizione dall'ITIS Di Maggio. è già un'ottima soluzione. Sarebbe utile come progetto per lo stesso o altri ITIS, la creazione del pacchetto DEB e lo spostamento su GitHub.
In oltre contattare la comunità italiana di Ubuntu per valutare se e come poter
sottoporlo poi al distributore.
Donazioni interscolastiche renderebbero poi più proficua la spesa pubblica. 

### Firma digitale e marca temporale
La firma digitale, per natura del dispositivo, non è delegabile ad un sistema 
centralizzato, a meno di non poter collegare remotamente la porta usb locale.
Esistono dei client Rdp che forniscono questa funzionalità, anche se perde in
sicurezza.
Comunque la soluzione in cloud (o samba) può sopperire al limite.

### Gestione workflow
Le soluzioni free e open per il WF ci sono e sono anche molto complesse. Oltre a risultare complicate per un utente avanzato, sono spesso astratte. I prodotti permettono infatti di disegnare la soluzione e generare scheletri di codice che comunque prevede il completamento con dettagli tecnici che non riescono ad essere a portata di un impiegato. Una scuola non richiede poi quella complessità che richiede una multinazionale.<br>
Per questo si può pensare ad una soluzione da integrare nel file system, che già di per sè è uno strumento per l'organizzazione di archivi. Il cloud estende poi l'archiviazione con la distribuzione.

Soluzione cloud (come estensione WF)
------------------------------------
Il cloud, corredato di un'interfaccia web, fornisce un ambiente unico di accesso e garantisce l'accesso anche a chi non ha un mezzo potente o a chi non vuole doversi dotare di un client.
Se guardiamo a come funzionano i media server come Kodi, notiamo che accando al file originale, si possono far generare automaticamente con opportune utility, i files INFO (.NFO). Questi sono files di testo, in stile INI (non complessi XML), che rappresentano spesso un estratto dei metadati.<br>
Si potrebbe usare lo stesso principio per istruire il processo che sovrintende il workflow, quello che di fatto supporta il personale addetto.<br>
Se per ipotesi si creasse nell'area utente di riferimento, una cartella 
"DA FIRMARE DIGITALMENTE", l'utente, opportunamente informato via email o sms, whatsapp o telegram, tramite utility già esistenti (sendmail, ..), firmerebbe la propria copia locale. A questo punto il processo WF sul server, accorgendosi della modifica potrebbe proseguire il ciclo, spostandolo in un'altra cartella.<br>
Lo stesso processo si potrebbe occupare della compilazione di files LEGGIMI con il log delle operazioni svolte.<br>
Per istruire il processo WF (PWF) si potrebbe utilizzare files che abbiano lo stesso nome dell'archivio con estensione ".workflow.txt".
Questo file conterrebbe macro istruzioni basiche come "EMAIL_TO:...", 
teoricamente compilabili da una tabella a due colonne, una pagina facilmente realizzabile da un programmatore junior.<br>
In caso di errore, PWF può corredare lo stesso file con una riga commento contenente il messaggio d'errore e l'indicazione per la sua correzione o un link alla documentazione web di riferimento.
In questo modo si rende il tutto un sistema ad apprendimento per approssimazioni successive e modellabile sulle esigenze specifiche, senza richiedere l'apprendimento di complesse conoscenze alla UML.
Python è un linguaggio molto lineare. Non a caso è molto impiegato per lo sviluppo degli addon per Kodi.

### Archiviazione sostitutiva
L'A.S., vero obiettivo di questo documento, consiste sostanzialmente nel caricare il file su un server abilitato. Anche questa attività si svolge con una banale utility molto diffusa nel mondo Linux come CURL. Questo dopo essersi registrati sul sito a cui poi si pagherà la tariffa per ogni documento o per il rilascio della marca temporale. Si parla di alcuni centesimi.

L'aspetto a corredo di quest'attività è la consultazione dell'elenco dei documenti o della copia locale. Sostanzialmente un documento già archiviato va marcato localmente o semplicemente rimosso. La marcatura può avvenire inserendo il log nel file LEGGIMI e/o rinominando il file con estensione ".archiviato".

La creazione di una pagina internet riassuntiva di consultazione costerebbe nello sviluppo di uno scanner, ulteriore attività che un programmatore junior, sempre studente, potrebbe svolgere come tesi di diploma, con la supervisione del docente project manager, coordinato con il consulente senior e program manager.

### Compilazione pdf
Un modo per liberarsi dalla dipendenza di DOCX, ODT e compagnia, è ricondurre i documenti alla forma PDF. Saper compilare documenti complessi è abilità di un utente esperto a cui non fa differenza l'uso di uno strumento come MSOffice o LibreOffice, di cui, per applicazioni più utili, bisogna usare ad esempio la stampa unione. Il WYSIWYG non ha poi impedito la formazione di formati come il markdown e i relativi strumenti. 

In un sistema formalizzato poi, i dati dovrebbero risiedere teoricamente
su un database e da qui riprodursi in "cartaceo" digitale o fisico, 
solo per compatibilità con un sistema che teoricamente è in obsolescenza.

Un pdf può essere quindi generato da una regola PWF, a partire da un record di un db, da un DOCX o un ODT ed essere compilato da un utente esterno (genitore, studenti o altro) e/o firmato digitalmente. Tramite un link può essere scaricato o compilato online a seconda delle esigenze.

### Print server
Questo paragrafo a solo lo scopo di portare a coscienza due problemi. Uno è la necessità di avere un sistemista di riferimento, l'altro è che la carta e la stampa condivisa spariranno, in un sistema completamente digitale.

