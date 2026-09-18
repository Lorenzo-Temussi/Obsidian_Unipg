---
autore: Davide Maracaglia
date: 2026-02-26
---

◀️ *Back to:* [[Linguaggi Formali e Compilatori]]

---

## I. Introduzione: Compilatori e Interpreti

La traduzione del codice sorgente in un linguaggio comprensibile dalla macchina può avvenire in modalità differenti. (È anche possibile la traduzione da un linguaggio di programmazione a un altro).

* **Compilatore:** Esegue la traduzione in blocco *prima* dell'esecuzione. Prende in input il **codice sorgente** e, tramite il traduttore, restituisce il **codice oggetto** (oppure delle notifiche di errore).
* **Interprete:** Esegue la traduzione *istruzione per istruzione*, simultaneamente all'esecuzione del programma. Prende in input sia il **codice sorgente** sia l'**input** dell'utente, producendo direttamente l'**output**.

### Compilatori Ibridi (Es. Java)
I sistemi ibridi combinano i due approcci:
1. Il traduttore analizza il codice sorgente e lo traduce in un **programma intermedio** (ad esempio, il *Java bytecode*).
2. Successivamente, una **macchina virtuale** (ad esempio, la JVM) riceve gli input dell'utente e *interpreta* il codice intermedio per produrre l'output finale.

---

## II. Le Fasi della Compilazione: Dall'Analisi alla Sintesi

La compilazione si divide concettualmente in due macro-fasi principali:
* **Fase Analitica (Analisi):** Riguarda la comprensione del codice in ingresso. Ha lo scopo di costruire l'**Albero Sintattico Astratto (AST)** partendo dal codice sorgente.
* **Fase Sintetica (Sintesi):** Riguarda la generazione dell'output. Si occupa di produrre il codice oggetto finale a partire dall'AST generato.

---

## III. Le 8 Fasi del Sistema di Compilazione
Il passaggio dal codice sorgente al codice macchina attraversa stadi sequenziali, che comunicano tra loro avvalendosi di strutture condivise come la **tabella dei simboli** e il modulo di **gestione degli errori**.

### FASE DI ANALISI
1. **Gestione Input (Preprocessore / Lettura):** Prende in ingresso il codice sorgente puro.
   > [!NOTE] Nota del Prof
   > Il codice sorgente è tipicamente un file di testo che deve essere letto e processato sequenzialmente dal sistema.

2. **Analisi Lessicale (Scanner):** Il file in ingresso è una sequenza di caratteri. Lo scanner raggruppa questi caratteri in sequenze elementari chiamate **lessemi**. A ogni lessema viene associata una classe lessicale (**token**) e un **attributo** (che viene registrato nella tabella dei simboli).
   * *Esempio sull'espressione `position = initial + rate * 60`:*
     * `position` $\rightarrow$ Token: *id*, Attributo: *1*.
     * `=` $\rightarrow$ Token: *assign*.
     * `initial` $\rightarrow$ Token: *id*, Attributo: *2*.
     * `60` $\rightarrow$ Token: *number*, Attributo: *4*.
   > [!EXAMPLE] La scelta dei token
   > L'assegnazione dei token e degli attributi segue regole specifiche che cambiano da linguaggio a linguaggio. La scelta dei token è a discrezione del progettista del linguaggio (ad esempio, nel Fortran, la sintassi e gli spazi richiedono regole di scansione particolari).

3. **Analisi Sintattica (Parser):** Stabilisce le regole grammaticali. Il parser prende la sequenza di token prodotta dallo scanner e la organizza in un **Albero Sintattico Astratto (AST)**.
   * I *nodi interni* dell'albero rappresentano le operazioni.
   * I *nodi figli* rappresentano gli argomenti di tali operazioni.
   > [!EXAMPLE] Struttura dell'AST
   > Confrontando una funzione scritta in 3 linguaggi diversi (Pascal, ML, Java) con 3 parametri reali, una variabile locale e un'operazione, la struttura ad albero logica rimane la stessa. Il nodo principale (radice) viene identificato come `FuncDef`.

4. **Analisi Semantica Statica:** Utilizza l'albero sintattico astratto e la tabella dei simboli per verificare che il programma sorgente sia semanticamente coerente con la definizione del linguaggio.
   * **Type checking:** Verifica che ogni operatore abbia tutti gli operandi del tipo corretto. Se necessario, può eseguire la **coercizione** (conversione forzata del tipo).
   * *Esempio in C:* È permesso moltiplicare un intero per un reale; il compilatore converte silenziosamente l'intero in un reale.
   * *Esempio in Pascal:* Il costrutto `WHILE` richiede obbligatoriamente un valore `BOOLEAN`. L'espressione `WHILE X DO X := X - 1 ;` farà segnalare un errore all'analizzatore semantico.

### FASE DI SINTESI
5. **Generazione del Codice Intermedio:** Dall'AST e dalla tabella dei simboli si ottiene un codice intermedio basato su istruzioni elementari, facili da tradurre in codice macchina. È **indipendente dall'architettura** (non specifica gli indirizzi fisici in memoria né i registri).
   * *Esempio pratico:* L'espressione precedente viene scomposta in operazioni atomiche: `t1 = inttofloat(60)`, `t2 = id3 * t1`, `t3 = id2 + t2`, `id1 = t3`.
6. **Ottimizzazione:** L'ottimizzatore elabora il codice intermedio per ridurre il tempo o lo spazio necessario all'esecuzione.
   > [!NOTE] Taglio delle Istruzioni
   > L'ottimizzatore snellisce il codice eliminando passaggi inutili. Nel nostro esempio, riduce le operazioni accorpando i calcoli: `t2 = id3 * 60.0` e `id1 = id2 + t2`.
7. **Generazione del Codice Oggetto:** È la parte più complessa e dipende strettamente dall'architettura della piattaforma hardware. Il compilatore genera codice assembly o file oggetto rilocabili. I passaggi chiave sono:
   * Fissare le locazioni di memoria esatte per i dati.
   * Generare il codice di basso livello per accedere a tali dati.
   * Selezionare i registri fisici della CPU per i calcoli intermedi.
   > [!IMPORTANT] Il ruolo dell'Assemblatore e del Linker
   > A rigore, l'Assemblatore (se il compilatore emette assembly) e il Linker sono strumenti esterni che intervengono al termine della compilazione. Il Linker si occuperà di collegare il codice oggetto generato in questa fase con eventuali librerie esterne, producendo il file eseguibile finale.
8. **Ottimizzazione Peep-hole:** Un'ulteriore e ultimissima fase di ottimizzazione legata alle specificità e ai "trucchi" dell'architettura hardware di destinazione.

---

## IV. L'Architettura Software del Compilatore

L'organizzazione interna del compilatore definisce come i moduli comunichino effettivamente tra loro durante il processo di traduzione.

* **Il Nucleo Centrale (Parser & Semantica):** la parte centrale di tutto il processo è l'**analizzatore sintattico**. In questa architettura, esso realizza contestualmente anche l'**analisi semantica statica**.
   > [!IMPORTANT] Avanzamento Parallelo
   > Dato che le due funzioni sono accorpate nel nucleo, l'analisi sintattica e l'analisi semantica avanzano parallelamente.
* **Gestione Input e Lettura:** Il sistema inizia con il modulo **gestore input**, che riceve il codice sorgente e può generare un "listato sorgente". Per formare i token, l'analizzatore lessicale deve leggere il codice un carattere alla volta invocando la funzione `readChar()` direttamente sul gestore input.
* **Dialogo Scanner-Parser:** L'analizzatore sintattico coordina il lavoro chiedendo i dati all'analizzatore lessicale tramite la chiamata alla funzione `prossimoToken()`. Questa funzione, implementata nello scanner, restituisce il `token` richiesto per continuare a costruire l'albero.
* **Gestione degli Errori:** Il **notificatore degli errori** riceve comunicazioni dirette e incrociate dal gestore input, dall'analizzatore lessicale e dal blocco sintattico/semantico ogni volta che viene rilevata un'anomalia. Alla fine, produce in output la "lista degli errori".
* **Generazione del Codice Finale:** Completata l'analisi senza errori bloccanti, è sempre l'analizzatore sintattico ad attivare la sintesi. Tramite chiamate a funzioni opportune, innesca il **generatore del codice**, che a sua volta emetterà il **codice oggetto** definitivo.