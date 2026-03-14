---
autore: Lorenzo Temussi
date: 2026-02-25
---
◀️ _Back to:_ [[Ingegneria del Software]]

# Introduzione

> [!note] Libro di testo principale:
>  I. Sommerville, Software Engineering, 9th ed.

> [!note] Menzioni d'onore:
• C. Larman, Applying UML and Patterns, 3rd ed.
• A. Shvets, Dive Into Design Patterns
• R. C. Martin, Clean Architecture
• M. Fowler, Refactoring, 2nd ed.

> [!warning] Nota Bene
> La lezione fa riferimento a contenuti presenti nel capitolo 1 del Sommerville


L'esame richiederà la creazione di un progetto e successiva presentazione e discussione ad opera di un team di non più di tre studenti. Idealmente andrebbe accompagnato da una presentazione in beamer {link} Latex.

L'utilizzo di IA è consentito, ma va adoperata con saggezza.

### Il corso è suddiviso in 4 moduli

1.  Sguardo d'insieme sulla materia e alcune definizioni per iniziare
2.  Modellazione UML
3.  Architettura, design e qualità
4.  Testing, GIT, Continuous Integration e Evoluzione del progetto

Il filo conduttore di questo esame sarà una fantomatica app chiamata UniManager, simile alla reale UniStudium, ma semplificata.

## Il Software

Al momento e per buona parte del futuro prevedibile, il software è la struttura portante di gran parte dei sistemi moderni, necessario per fornire servizi di ogni tipo. 

Per questa ragione è importante che il programmatore sia formato come ingegnere del software, capaci di instaurare, riparare e manutenere sistemi resilienti e adatti al compito.

Con il crescere della scala del progetto, il codice che funziona in maniera non ottimale è più pericoloso dei bug.  Architetture non scalabili, allocazioni insufficienti di risorse, testing scarso gestione errori approssimativa possono portare un sistema in ginocchio.

Chiameremo questi problemi strutturali che si presentano nei sistemi reali, e non nei piccoli, semplicistici sistemi accademici, MACRO - PROBLEMI.

Sistemi del genere richiedono la collaborazione efficace di molti individui, un mantenimento up-to-date attraverso le ere informatiche,  e una quantità di manutenzione che spesso viene a costare quattro volte il budget di sviluppo.

Per garantire una serie di buone scelte progettuali, che allungano la vita del software, si raccomanda di seguire un ciclo di:

Raccolta requisiti ->
Progettazione soluzioni ->
Implementazione ->
Verifica ->
Rilascio ->
Manutenzione ---^

Si comincia da una reale comprensione del problema da risolvere, e le esigenze degli utenti, dedicando all'analisi il tempo necessario a produrre dati chiari.

Nel caso emergano nuove esigenze durante questo processo, vanno esaminate anche esse.

Per quanto riguarda la relazione fra il backend (comunicazione con i server) e il frontend (interfacce utente) del software, è bene ricordare che il primo è il vero nocciolo del programma, ma non curare il secondo comporta la mancata espressione dei pieni benefici del primo.

### La guerra contro l'entropia

> "If debugging is the act 
> of removing software bugs, 
> then programming must be 
> the process of putting them in."[^1]

La regola più saggia per scrivere codice con una lunga vita è non scriverlo affatto. Montagne di codice compattate a cubo iniziano a marcire nel momento in cui lasciano la mente del loro autore, un Ingegnere del Software rispettabile lotta contro la complessità non necessaria:

- le architetture modulare consentono di operare su parti del codice senza compromettere le altre
- modelli chiari sono necessari per mantenere una struttura definita nel tempo
- ai moduli vanno assegnate responsabilità definite e separate, per aiutare nel processo diagnostico e di aggiornamento
- è buonissima pratica produrre documentazione intelligente e mirata per consentire a colleghi e tecnici esterni di navigare il prodotto 

Se non si prendono le dovute precauzioni, è bene ricordare che la complessità ha una tendenza a scalare esponenzialmente con il tempo, e costringere a frequenti e dispendiose riformattazioni più in là nel percorso, quando il tempo è poco.

---
◀️ _Back to:_ [[Ingegneria del Software]]

[^1]:  haiku di Esdger W. Dijkstra
