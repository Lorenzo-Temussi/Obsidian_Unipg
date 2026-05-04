◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

## Semplificazioni nelle grammatiche non contestuali
---

Certamente ricorderete i due problemi più frequenti associati ad un linguaggio, cioè la **recognition** e il **parsing**. Questi problemi tendono ad essere una vera e propria seccatura per il caso generale, particolarmente se il linguaggio prevede:

- $\varepsilon$-produzioni;
- produzioni 1-arie (da un simbolo non-terminale ad un altro simbolo non-terminale);
- variabili inaccessibili (che non compaiono nelle forme sentenziali);
- variabili improduttive (che non producono parole prive di variabili);

## Perché non ci piacciono le produzioni vuote e unarie
---

Il corso di Algoritmi e Strutture dati (wow, interdisciplinarietà!) mira a farci un intenso lavaggio del cervello sull'importanza di scrivere funzioni con complessità di tempo bassa (la funzione che esprime il tempo richiesto all'esecuzione in funzione del numero di argomenti in entrata), e poiché le formule che usiamo ora per scrivere linguaggi $gugugaga$ (non significativi in sé, ma facili da analizzare e generalizzare) saranno utili anche a scrivere compilatori e altri programmi simili, la complessità di tempo ci interessa alquanto.

Se ci pensiamo per un minuto, in assenza di $\varepsilon$-produzioni e produzioni 1-arie, con ogni produzione $\alpha\Rightarrow\beta$, otteniamo una $\beta$ con più lettere di $\alpha$ o con lo stesso numero di lettere ma un maggior numero di caratteri terminali. Questo significa che una parola di lunghezza $n$ può essere generata in al più $2n-1$ passaggi.

>[!error] Attenzione: Algoritmi!
>La parte seguente è densa di conoscenze operative, bevete un bicchier d'acqua, fate un minuto di stretching e spegnete la musica prima di approcciarla. Potete fare pause in mezzo.


## Eliminazione delle $\varepsilon$-produzioni
---

>[!warning] Proposizione
>Ogni linguaggio non contestuale può essere generato da una grammatica non contestuale priva di $\varepsilon$-produzioni, con l'unica eccezione della produzione S$\rightarrow\varepsilon$, dove S è il simbolo iniziale e non figura a destra di alcuna produzione.

Una variabile $X$ di una grammatica $G$ si dice annullabile se $X \Rightarrow^* \varepsilon$.

#### Caso 1 - S non è annullabile:

A partire dalla grammatica G, generiamo una grammatica G' nel modo seguente.
1. Aggiungiamo tutte le produzioni ottenute cancellando nei lati destri delle produzioni di G una o più occorrenze di variabili annullabili;
2. Cancelliamo le $\varepsilon$- produzioni.

Nel beamer del professore è presente un esempio illustrato di questo processo.

#### Caso 2 - S è annullabile:

A partire dalla grammatica G, generiamo una grammatica G' nel modo seguente.
1. Aggiungiamo tutte le produzioni ottenute cancellando nei lati destri delle produzioni di G una o più occorrenze di variabili annullabili;
2. Cancelliamo le $\varepsilon$- produzioni.
(fin qui i due processi sono identici)
3. Se S non compare nei lati destri, aggiungiamo la produzione $S\rightarrow\varepsilon$;
4. Se invece S compare nei lati destri, aggiungiamo una nuova variabile S', che sarà il nuovo simbolo iniziale, e le produzioni $S'\rightarrow\varepsilon$ e $S'\rightarrow S$.

#### L'insieme delle variabili annullabili

Costruisco un insieme di variabili annullabili $W_n$ come segue:

$W_1=\{X\in N\  |\  \exists\  X\rightarrow \varepsilon \in P\}$
$W_n=\{X\in N\  |\  \exists\  X\rightarrow \gamma \in P\ con \ \gamma \in W^*_{n-1} \ \}, \ \ \ \ n\geq 2$

Questo insieme $W_n$ contiene tute e sole le variabili che si annullano entro $n$ passi. 
Abbiamo: $W_1\subseteq W_2\subseteq\ \cdot \cdot \cdot\ \subseteq W_n \subseteq \ \cdot \cdot \cdot \ \subseteq N;$
Pertanto per un qualche n, avremo $W_n = W_{n-1}=W$, dove $W$ è l'insieme di tutte le variabili annullabili della grammatica.

>[!quote] Codice per popolare W
>
W $\leftarrow$ {X $\in$ N | X $\rightarrow \varepsilon \in$ P}
 N$\leftarrow$N - W
repeat
W' $\leftarrow${X $\in$ N | $\exists$ X $\rightarrow \gamma \in$ P con $\gamma \in$ $W^*$}
W $\leftarrow$W $\cup$ W'
 N$\leftarrow$N-W'
while W' $\neq \emptyset$

## Eliminazione delle produzioni unarie
---

Espandiamo la definizione precedente.

>[!warning] Proposizione
>Ogni linguaggio non contestuale è effettivamente generato da una grammatica non contestuale priva di $\varepsilon$-produzioni ==e produzioni unarie==, con l'unica eccezione della produzione S$\rightarrow\varepsilon$, dove S è il simbolo iniziale e non figura a destra di alcuna produzione.

#### Processo di eliminazione

1. Eliminare le $\varepsilon$-produzioni con l'algoritmo precedente;
2. Per ogni coppia di variabili A, B tali che A $\Rightarrow^*$ B, aggiungiamo i lati destri delle produzioni di B a quelli delle produzioni di A;
3. Cancelliamo le produzioni unarie.

Costruiamo gli insiemi di coppie di variabili $T_n$ come segue:
$T_1=\{(X, Y)\in N \times N\ |\ \exists \ X\rightarrow Y \in P\}$
$T_n=T_{n-1}\cup \{(X, Y)\in N \times N\ |\  \exists \ Z\in N,\ (X,Z),(Z, Y)\in T_{n-1}\},\ \ n\geq2.$

Possiamo osservare che $T_n$ contiene le coppie di variabili $(X,Y)$ tc $X\Rightarrow^*Y$ in al più $2^{n-1}$ passi. 
Inoltre $T_1 \subseteq T_2 \subseteq \cdot \cdot \cdot \subseteq T_N \subseteq \cdot \cdot \cdot \subseteq N \times N$, e (come sopra) per un qualche $n$, $T_n = T_{n-1}=T$.

## Variabili Improduttive o Inaccessibili
---

Se nessuna delle conseguenze di una variabile contiene caratteri terminali, questa si dice **Improduttiva**, nel caso contrario, si dice **Produttiva**.

Se nessuna produzione ha una variabile V a destra, questa si dice **Inaccessibile**, nel caso contrario, **Accessibile**.

>[!tip] Osservazione
>Ste variabili servono quanto un posacenere su una motocicletta, ogni grammatica G da cui vengano cancellate tutte le variabili improduttive o inaccessibili e le produzioni che le contengono, resta equivalente a sé stessa.

#### Algoritmo per trovare variabili Produttive

Ancora una volta, abbiamo un processo per passi:

$W_1=\{X\in N \ |\  \exists\  X\rightarrow w \in P \ con\ w \in \Sigma^*\}$,
$W_n=\{X\in N \ |\  \exists\  X\rightarrow \gamma \in P \ con\ \gamma \in (W_{n-1} \cup \Sigma)^*\},\ \ n\geq2$,

Anche qui, $W_n$ contiene tutte e sole le variabili produttive che raggiungono la parola terminale in n passi, e, per una n sufficientemente alta, si ha che $W_n=W_{n-1}=W$.

#### Algoritmo per trovare variabili accessibili

$K_0=\{S\},$
$K_n=K_{n-1}\cup$ {variabili che compaiono a destra di una produzione delle $X \in K_{n-1}\},\ \ \ n\geq 1.$

Anche qui, $K_n$ contiene tutte e sole le variabili produttive che raggiungono la parola terminale in n passi, e, per una n sufficientemente alta, si ha che $K_n=K_{n-1}=K$.


## Procedura di riduzione completa
---

Avendo visto come svolgere i singoli passaggi, vediamo ora come combinarli per ottenere una grammatica non-contestuale priva di variabili improduttive e inaccessibili:

1. Determinare le variabili produttive (W);
2. Eliminare le variabili improduttive e le produzioni che le contengono;
3. Determinare le variabili accessibili (K);
4. Eliminare le variabili inaccessibili e le produzioni che le contengono;

>[!warning] Non-Commutatività
>Occhio che le operazioni vanno eseguite in questo ordine specifico, perché rimuovere le variabili improduttive può rendere variabili precedentemente accessibili, inaccessibili.

E questo è quanto per oggi.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]