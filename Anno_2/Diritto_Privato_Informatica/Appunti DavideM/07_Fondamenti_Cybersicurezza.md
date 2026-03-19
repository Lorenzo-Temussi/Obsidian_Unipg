---
date: 2026-03-02
subject: Diritto dell'Informatica e Data Protection
tags:
  - Diritto
type: lezione
---
# Fondamenti di Cybersicurezza, Gestione del Rischio e Normativa


## Il Rischio Cyber e il Ruolo del DPO
La sicurezza informatica è intrinsecamente associata al concetto di rischio. In Italia, istituzioni e associazioni come l'Agenzia per la Cybersicurezza Nazionale (ACN) e il CLUSIT (attraverso l'annuale Rapporto Clusit) monitorano costantemente le tendenze e l'andamento delle minacce in ambito cyber a livello nazionale e globale. I rischi informatici sono in continua ed esponenziale espansione, con un boom significativo registrato durante la pandemia da COVID-19, portando a una chiara partizione percentuale dei tipi di attacco.

Nell'ambito del GDPR, l'articolo 39 stabilisce i compiti del Data Protection Officer (DPO), il quale ha il ruolo di supportare il Titolare del trattamento nell'attribuire le responsabilità interne e nel sensibilizzare e formare il personale sui rischi connessi al trattamento dei dati personali. Ciò significa che il DPO e le figure preposte devono conoscere approfonditamente le minacce informatiche più comuni (es. accesso abusivo, malware) per poter adeguare procedure e adottare adeguate misure tecniche e organizzative.

> [!LAW] Articolo 39 GDPR
>  Definisce i compiti del DPO, tra cui la sorveglianza dell'osservanza del regolamento e la sensibilizzazione e formazione del personale che partecipa ai trattamenti.

> [!INFO] È fondamentale la collaborazione e l'interscambio tra informatici, tecnici e giuristi per una corretta compliance aziendale.

> [!INFO] Al giorno d'oggi vi è un preciso obbligo di possedere competenze informatiche anche per le professioni legali e gli avvocati (es. caso Panama Papers).

## Standard Internazionali e Valutazione del Rischio
Un elemento centrale nella gestione aziendale è l'approccio basato sul rischio (Risk Management). Lo standard ISO 31000 fornisce lo scheletro e le linee guida per un corretto impianto normativo e di processo.

> [!INFO] Rivedere la struttura e i requisiti dell'impianto normativo ISO 31000.

La formula fondamentale per la valutazione del rischio, utile a individuare le vulnerabilità più urgenti e ad applicare le corrette misure tecniche e organizzative, è **R = P x D** (Rischio = Probabilità x Danno/Impatto). Lo schema di valutazione si appoggia a modelli ciclici come il Ciclo di Deming (Plan-Do-Check-Act) per valutare scenari ad alta probabilità/basso impatto oppure a bassa probabilità/basso impatto.

La resilienza informatica è diventata un pilastro strategico. In Unione Europea si pone forte accento sulla "sovranità digitale" per ridurre la dipendenza da tecnologie e software extra-UE (es. software americani o asiatici), come testimoniato dall'adozione di normative quali l'European Chips Act.

## Fondamenti di Sicurezza: La Triade CIA
I reati informatici e le violazioni di sicurezza incidono quasi sempre su almeno uno dei tre elementi fondamentali della sicurezza delle informazioni.

> [!INFO] CONCETTO IMPORTANTE: La Triade CIA.

La Triade CIA si compone di:
- **Confidentiality (Confidenzialità):** i dati devono poter essere letti ed elaborati esclusivamente da figure specifiche e autorizzate.
- **Integrity (Integrità):** l'informazione non deve subire alterazioni; se un soggetto non abilitato modifica i dati, l'integrità è compromessa.
- **Availability (Disponibilità):** i dati devono essere prontamente accessibili ai soggetti autorizzati, impedendone l'esposizione ai non autorizzati.

## Evoluzione Storica della Cybersicurezza
La sicurezza informatica non è nata contemporaneamente all'informatica: i primissimi sistemi non contemplavano il concetto di "sicurezza by design". Oggi, la cybersecurity riguarda e tutela sia le componenti hardware (es. mitigazione di vulnerabilità delle CPU come *Meltdown* basate su segnali anomali) sia quelle software.

> [!INFO] Fun fact
>  la derivazione del termine "bug" ha origine al MIT (e poi ad Harvard sul Mark II) per via di un insetto reale incastrato nei circuiti della macchina, il primo vero "bug" della storia dell'informatica.

Negli anni '50, i primi Big Mainframe come l'UNIVAC (1951) non avevano cyber-sicurezza. La protezione dell'hardware era esclusivamente fisica, volta a prevenire il danneggiamento più che il furto. La programmazione avveniva in linguaggio macchina (0 e 1), esponendo i sistemi a frequenti errori umani. In assenza di connessioni esterne, l'accesso fisico alla sala server fungeva da unica vera "autenticazione". Successivamente, con calcolatori come il Mark 1 (Harvard) basato su componenti meccanici (e con antenati come il Meccanismo di Anticitera di Archimede per calcoli astronomici), l'informatica si è evoluta. 
Con la nascita di ARPANET prima di Internet (anni '70), sono emerse le fondamenta della cybersicurezza moderna. 

> [!INFO] Esempio storico-culturale 
> Il film "WarGames" e lo spavento del Presidente Reagan, che diede impulso alle primissime policy governative di sicurezza informatica negli USA.

Poiché i profili di rischio evolvono continuamente, è essenziale comprendere che la "sicurezza assoluta" in informatica non esiste.

## Il Quadro Normativo Nazionale e la Direttiva NIS
Una violazione di sicurezza che comporta accidentalmente o in modo illecito la distruzione, la perdita, la modifica, la divulgazione non autorizzata o l'accesso ai dati personali trasmessi, conservati o comunque trattati, configura giuridicamente un Data Breach (violazione dei dati personali).

Il legislatore interviene costantemente per arginare tali minacce. A livello europeo, la materia è presidiata dalla Direttiva NIS (e successive evoluzioni). A livello nazionale, il quadro include la Legge 90/2024 (che consolida le attribuzioni dell'Agenzia per la Cybersicurezza Nazionale - ACN), il Decreto Legge 105/2019 sul Perimetro di Sicurezza Nazionale Cibernetica e il Decreto Legge 138/2024. Per la Pubblica Amministrazione è raccomandata l'implementazione di algoritmi crittografici sicuri (come SHA-256).

> [!LAW] Decreto Legge 20/2021
>  Introduce raccomandazioni cogenti per la Pubblica Amministrazione, suggerendo fortemente di dismettere l'utilizzo di software russi (come gli antivirus Kaspersky) per arginare il rischio concreto di "backdoor" governative.

## Minacce, Fattore Umano e Social Engineering
L'anello debole della catena di sicurezza rimane l'utente. Spesso ci si riferisce al fattore umano con l'espressione "Problem Exists Between the Keyboard And the Chair" (PEBKAC). Aggiungendo specifiche motivazioni psicologiche, è possibile manipolare l'output e il comportamento delle persone.

Questa tecnica prende il nome di **Ingegneria Sociale (Social Engineering)**, che sfrutta le debolezze cognitive per ottenere accessi o informazioni riservate. Le caratteristiche e leve principali sfruttate sono:
- Autorevolezza
- Senso di colpa
- Panico
- Ignoranza
- Desiderio
- Avidità
- Compassione

> [!INFO] Lettura consigliata
> "The Art of Deception" (L'arte dell'inganno) di Kevin Mitnick, testo fondamentale sulle tecniche di Social Engineering.

## Tipologie di Attacchi e Malware
Le reti sono esposte a diverse categorie di software malevolo, comunemente note come Malware. Una delle minacce più perniciose è il **Ransomware**, che cifra i dati dell'interessato e delle aziende estorcendo un riscatto economico. Le tipologie includono:
- **Locker:** blocca completamente l'accesso al sistema.
- **Crypto:** cifra specificamente i file rendendoli illeggibili.
- **Double Extortion:** oltre a cifrare, minaccia la divulgazione pubblica dei dati esfiltrati.
- **Ransomware as a Service (RaaS):** un modello criminale in abbonamento per l'utilizzo di ransomware da parte di terzi.

Ulteriori tipologie di attacchi includono attacchi per intercettazione, come il *Man in the Middle* o il *Man in the Mail* (es. Business Email Compromise), spesso orchestrati da grandi organizzazioni criminali. A livello di cyber-warfare governativo, si ricorda il celebre virus *Stuxnet*, creato ad hoc per distruggere le centrifughe del sistema di arricchimento dell'uranio in Iran.
Tra le nuove minacce emergenti, manipolazioni tramite intelligenza artificiale o minacce fisiche:
- **Deepfake**
- **BadUSB**
---
## ⏭️ Navigazione

- **Index:** [[Diritto Privato dell'Informatica]]