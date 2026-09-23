---
autore: Lorenzo Temussi
fonte: slides e lezioni
date: 21/09/26
---
Da [[Programmazione Web e Mobile]], in data 21/09/2026.


Per avere la certezza di metabolizzare correttamente i contenuti del programma, partiamo con una piccola sessione di vocabolario.

>[!info] Internet
>Rete che include milioni di dispositivi globalmente, con una infrastruttura composta di cavi metallici, fibra ottica, onde elettromagnetiche e quant'altro.

> [!IMPORTANT]  World Wide Web
 Trattasi di un servizio di Internet che connette dispositivi nella rete, e consente di navigare, ovvero visitare diverse risorse, tramite un sistema ipertestuale.

---

All'interno dell'ambiente web, dato il grande volume di operazione svolte in ogni dato momento, e la natura sensibile di molti dati condivisi, sorge la necessità di seguire dei protocolli e degli standard per virtualmente ogni operazione.

---

Ad esempio, la totalità delle pagine web propriamente intese impiegano lo stesso linguaggio di markup, supportato da ogni browser, chiamato [HTML](https://boolean.careers/blog/html-cose-come-funziona-e-a-cosa-serve).

>[!info] HTML
>HyperText Markup Language, un linguaggio di markup che determina la struttura dei contenuti in una pagina, simile a come un insieme di istruzioni umane determina l'impaginazione di un quotidiano.
>La sintassi è stabilita dal WWW Consortium, e al momento è nella sua quinta installazione.

>[!info] Browser
>Applicazione client-side che si occupa di organizzare l'interazione con la rete. Può eseguire codice (javascript), spedire chiamate di rete HTTP, e renderizza automaticamente tutte le risorse in base al codice HTML associato.

>[!info] Client-Server
>Rapporto asimmetrico in cui si trovano due (o anche non due) macchine.
>Il Client è dotato di una interfaccia per inviare richieste al Server, il Server è dotato di dati da inviare in base alla richiesta ricevuta.

---

Allo stesso modo, per gestire le chiamate di rete, ovvero le varie richieste che un client invia la server c'è un protocollo di riferimento chiamato [HTTP](https://devacademy.it/che-cos-e-http-la-guida-per-programmatori-e-sviluppatori-web/).

>[!question] HTTP
>Un protocollo che gestisce l'invio e la risposta di richieste client-server.
>Le Chiamate hanno la seguente anatomia:
>
>*Metodo* : Definisce quale operazione eseguire;
>*Path* : La posizione in rete della risorsa da reperire;
>*Header* : Informazioni aggiuntive miscellanee da inviare;
>*Body* : Contiene una risorsa da inviare (solo per Chiamate speciali, come ad esempio POST).
>
>Quando una Chiamata viene ricevuta dal server, questo replica con una Risposta che contiene, a sua volta:
>
>*Status Code* : codice a tre cifre che indica se l'operazione ha avuto successo, o dove c'è stato un fallimento, in caso contrario;
>*Body* : Contiene la risorsa da restituire (solo per Chiamate speciali, come ad esempio GET).

>[!question] TLS
>Transport Layer Security è un protocollo eseguito fra client e server prima di qualsiasi chiamata HTTPS (versione sicura di HTTP) che si assicura che gli scambi a seguire siano criptati.

>[!question] TCP
>Transmission Control Protocol è a sua volta eseguito prima del TLS per connettere i due host e assicurare il corretto ordinamento dei pacchetti in arrivo e in partenza.

Il Protocollo HTTPS è stateless, ovvero nessuna chiamata influenza le chiamate successive. Per evitare alcuni drawback di questo design, molte pagine web fanno uso di cookies: risorse che restano nella cache dopo la visita del sito e informano il comportamento dello stesso quando l'utente ritorna.

HTTP è ora giunto alla terza versione (HTTP/3) che funziona su protocollo di rete QUIC e utilizza UDP come protocollo di trasporto.

---

Infine, l'URL identifica univocamente l'indirizzo di una risorsa in rete. 

La logica è simile a quella per cui un indirizzo stradale punta direttamente a due specifiche coordinate terrestri, ovvero è presente una rubrica (DNS) che contiene gli indirizzi IP di ogni URL registrata, e in seguito alla richiesta dell'utente, restituisce l'IP della macchina associata all'URL in questione.

Per sveltire il processo, alcuni IP sono salvati con le rispettive URL nella cache locale, a formare una minuscola rubrica rapida privata.

Quando il server si connette all'indirizzo IP ottenuto, procede poi a scaricare e analizzare il suo HTML, per poi costruire il DOM (Document Object Model), applicare il CSS (che sarebbe lo stile, ovvero il design delle singole parti), ed esegue il javascript della pagina, che serve ad interagire con il server e manipolare il DOM dinamicamente.

---

### Ere del Web

Il Web 1.0 era una vasta distesa di pagine statiche, prive di strumenti che consentissero agli utenti di inviare input.

Il Web 2.0 (noto anche come il World Wild West) introduce tutte le feature dinamiche che gli utenti amano, come i social media, i marketplace, le imageboard, è dinamico e interattivo.

Il Web 3.0 (noto anche come il Dead Internet) è caratterizzato da elaborati algoritmi per l'interpretazione dei contenuti (sì il tuo provider sa cosa significa "keep yourself safe"), una quantità near-infinite di sciami di bot, scammer del sud-est asia che si deepfakano per fingere di essere tua nonna (per truffare tua nonna), e maggiore integrazione fra piattaforme e servizi.

---

## Prova d'esame

Il progetto sarà personale e consisterà una pagina web da decidere con il professore, seguirà un orale in cui dovrete convincerlo di non averla vibe-codata e di non aver giocato a Wild Rift durante le lezioni.

---
Da [[Programmazione Web e Mobile]], in data 21/09/2026.