---
autore: Lorenzo Temussi
date: 2026-02-26
---
◀️ _Back to:_ [[Ingegneria del Software]]

> [!warning] Nota Bene
> La lezione fa riferimento a contenuti presenti nei capitoli 2-3 del Sommerville

## Perché organizzare il lavoro

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



---
◀️ _Back to:_ [[Ingegneria del Software]]

[^1]: (disambiguazione, il termine in questo corso è usato per descrivere una letterale sequenza di decisioni e azioni eseguite da sviluppatori umani, non un programma in esecuzione)
	

[^2]: https://ilmiote.wordpress.com/2010/07/04/una-tazza-di-te-una-storia-zen/
	
