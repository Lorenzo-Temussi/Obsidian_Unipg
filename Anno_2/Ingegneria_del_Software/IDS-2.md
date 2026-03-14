---
autore: Lorenzo Temussi
date: 2026-02-26
fonte: slides
---
◀️ _Back to:_ [[Ingegneria del Software]]
## Perché organizzare il lavoro

> [!warning] Nota Bene
> La lezione fa riferimento a contenuti presenti nei capitoli 2-3 del Sommerville

La collaborazione di professionisti è una risorsa eccellente che però ha bisogno di direzione:
- L'ordine di sviluppo delle funzioni
- La depth richiesta ad ogni funzione in un dato momento
- Quando fermarsi e rivalutare le decisioni prese in precedenza

Un team organizzato non deve mai tirare il cappello sul prossimo step da eseguire, e ridurre il caos significa aumentare la prevedibilità del flusso di lavoro.

Possiamo definire un processo software [^1] come un insieme strutturato di attività, ruoli e artefatti che guidano la costruzione e l'evoluzione di un sistema. Le limitazioni portate dall'impiego di un sistema dovrebbero essere mirate alla riduzione dell'incertezza, dell'ambiguità e dell'incoerenza nel corso del lavoro, il di più è burocrazia che rallenta il team.

In ogni processo troveremo quattro attività fondamentali:

- *specifica:* la funzione attesa del sistema e i vincoli che deve rispettare
- *sviluppo:* progettare e implementare la soluzione
- *validazione*: verifica che il sistema segua i principi stabiliti
- *evoluzione:* modificare e mantenere il sistema nel tempo

Non sempre sono combinate e bilanciate nello stesso modo, ma sono sempre presenti.

Come si può intuire a questo punto, non esiste un solo modello per il processo software, ma una varietà, ciascuno con le proprie caratteristiche, e le proprie variazioni, che sono adatti a far fronte a esigenze diverse. 

#### Modello Waterfall:

###### Principi:
- Lo sviluppo è organizzato in una sequenza di fasi ben definite e ordinate.
- Le fasi si susseguono linearmente e il prodotto della precedente diventa l'input della successiva.
- L'obiettivo è ridurre al minimo i ripensamenti, avanzando di fase in fase solo dopo che la precedente è completamente sviluppata.
##### Vantaggi:
- La struttura è facile da comprendere per gli investitori
- La forte attenzione alla documentazione favorisce l'allineamento fra team e la tracciabilità delle decisioni
- Adatto ad ambienti in lenta evoluzione e progetti ben delineati dal principio.
##### Svantaggi:
- Eventuali cambi di programma, o di normativa vigente, o di scope o davvero di ogni genere costringono a tornare indietro, e il processo è strutturato per muoversi in una sola direzione.
- In generale il costo del cambiamento cresce sempre di più con il passare delle fasi.
- Il prodotto è utilizzabile solo alla fine del processo.


#### Modello Incrementale:

###### Principi:
- Il progetto viene costruito a passi successivi, come una scultura o un dipinto, che passano attraverso una prima fase di abbozzo e numerose fasi di raffinamento.
- Ogni incremento produce una versione utilizzabile del sistema con sempre più funzioni e polish.
- L'utente può utilizzare il servizio e offrire feedback durante il processo di sviluppo.
##### Vantaggi:
- Il feedback istantaneo degli utenti è una risorsa impagabile e spesso gratuita.
- Una versione grezza del progetto è disponibile molto presto nel processo.
- I cambi di rotta sono più agevoli da implementare.
##### Svantaggi:
- Possibile perdita di vista dello scope.
- Le soluzioni veloci talvolta necessarie per mantenere il passo tendono ad essere più costose da manutenere, e richiedere rifattorizzazione più in là nel tempo.
- Il design deve mantenere attivamente lo "spazio vuoto" della famosa storia zen del maestro del tè[^2], in cui aggiungere le implementazioni successive, che non sono semplici estensioni ma parte di un disegno ben definito dall'inizio.

#### Modello Spirale:

##### Principi:
- Serie di cicli successivi, che si avvicinano al progetto finito come una spirale si avvicina al suo centro.
- Assume che il progetto non sia ben definito fin da subito e lo sviluppo debba procedere con una carenza di informazioni.
- Lo sviluppo è controllato con ogni ciclo, le varie soluzioni trovate dal team sono spesso innovative, e vanno testate e affinate con il dissiparsi dell'incertezza.

##### Vantaggi:
- Consente di ridurre l'incertezza un giro di vite alla volta, anche per progetti non chiaramente delineati dall'inizio
- Produce numerosi prototipi a testimonianza della fase dello sviluppo più recente.
- Adatto all'introduzione di features poco familiari.

##### Svantaggi:
- La flessibilità, innovazione e versatilità del metodo cagionano un dispendio di risorse e budget che non sono necessari per ogni progetto.


### Gli Approcci Agili

Con il termine si indicano tutti gli approcci con rilasci ravvicinati, adatti ad ambienti di lavoro molto dinamici, in cui l'adattamento è una necessità indispensabile, e la disponibilità immediata del prodotto in qualche forma è fondamentale. 

In questi approcci viene valorizzata la comunicazione efficace fra collaboratori, investitori, e team di sviluppo. 

Se nel modello tradizionale si parte da un progetto e si alloca tempo e risorse finché esso non è completo, nel modello agile si fissa un budget e un limite di tempo per lo sprint, mentre lo scope resta flessibile.

## Lo Scrum

A Perugia si dice lo "scrumo", è un framework organizzativo che definisce un modello di processo con ruoli definiti, cicli brevi e uso estensivo di backlog. Per gli interessati, consultare la [Guida allo Scrumo](https://www.scrum.org/resources/scrum-guide) online, che arrivo molto più in depth di questa lezione.

### I Ruoli:

#### Product Owner:
Rappresentante degli interessi degli stakeholders e utenti, stabilisce le priorità lato utente e le funzioni effettive del prodotto finito.

#### Scrum Master:
Coordinatore del team, agevola la collaborazione e rimuove eventuali ostacoli non meglio definiti.

#### Development Team:
Realizza concretamente il sistema un incremento alla volta. Responsabile della qualità tecnica del prodotto.

>[!Example]
>**ProjOwn**: Il nostro sistema informatico consente di tracciare il volo dei piccioni usando dei satelliti
>
>**ScruMster**: Telefono ad un ornitologo e ad un avvocato per capire se è possibile fare questa cosa, e sento se al team serve qualche subscription o strumentazione apposita
>
>**DevTeam**: Creo in Java un oggetto Piccione per modellare i piccioni reali, e vado a cercare documentazione per progetti simili nel passato

### Il Backlog:

Una lista ordinata e dinamica delle priorità di sviluppo scritte in forma di User Stories, ovvero breve frasi che descrivono una necessità o un problema dl punto di vista dell'utente. Viene modificata spesso per rispecchiare i risultati dei feedback e dei risultati degli sprint.

>[!Example]
>**Story1:** Ieri un piccione è sparito dalla mappa mentre lo tracciavo
>
>**Story2**: Voglio tracciare anche le anatre oltre ai piccioni...
>
>**Story3**: L'interfaccia è gialla, vorrei che fosse color grigio piccione
>
>Ordinate realisticamente per priorità: il team presterà attenzione prima alla 1, poi alla 2 e infine alla 3.

### Gli Sprint:

Uno sprint è un intervallo di tempo breve e regolare, con obiettivi limitati e chiari. L'aspettativa è che ogni sprint apporti incrementi, seppure piccoli, nella direzione giusta, da usare per valutare il progresso e coinvolgere gli stakeholders.

>[!Example]
>
>**Sprint da 2 marzo a 16 marzo:** Aggiungere all'oggetto Piccione una immagine placeholder e un campo booleano chiamato is_sex_known.
>
>**Sprint da 17 marzo a 31 marzo:** Aggiungere all'oggetto Piccione un campo booleano chiamato is_male che viene letto quando is_sex_known vale 1. Adattare la funzione individua_velivolo() dalla libreria elicotteri.lib in funzione individua_piccione(). 

### Le Epic:

Una epica è una macro area funzionale che include numerosi servizi. Queste sono troppo grandi per essere sviluppate in uno sprint e spesso sono sviluppate un pezzo alla volta in parallelo.


### Al diavolo i piccioni, applichiamo Scrum ad UniManager

Possiamo individuare tre **epic principali:**
- Gestione Studenti
- Gestione Corsi
- Gestione Esami

Nel contesto di una epica, possiamo produrre delle **user stories:**
- Sono uno studente 'e' voglio iscrivermi ad un esame 'per' partecipare alla prova
- Sono un segretario 'e' voglio aggiungere uno studente ad un corso 'per' consentirgli di seguire le lezioni
- Sono un professore 'e' voglio pubblicare un messaggio diretto a tutti gli studenti 'per' informarli che c'è una scadenza a breve.

Durante uno **sprint** possiamo lavorare in base alle storie:
- S2: Creare una funzione per aggiungere uno studente al database
- S1: Creare una funzione per aggiungere uno studente presente sul database alla lista di un esame.

>[!Abstract] In Conclusione:
> - Un processo software non produce competenza tecnica dal nulla ma organizza quella disponibile in modo ripetibile, verificabile e coordinabile.
> - I modelli di processo sono ognuno pensato per delle necessità di progetto differenti.
> - I principi agili in particolare sono focalizzati su cicli di sviluppo brevi, e frequenti raccolte di feedback.
> - Scrum fornisce una struttura operativa semplice per organizzare lavoro, priorità e verifiche.
> - Backlog, stories, e epic organizzano il lavoro e aiutano gli stakeholders a seguire il processo.
---

◀️ _Back to:_ [[Ingegneria del Software]]

[^1]: (disambiguazione, il termine in questo corso è usato per descrivere una letterale sequenza di decisioni e azioni eseguite da sviluppatori umani, non un programma in esecuzione)
	

[^2]: https://ilmiote.wordpress.com/2010/07/04/una-tazza-di-te-una-storia-zen/
	
