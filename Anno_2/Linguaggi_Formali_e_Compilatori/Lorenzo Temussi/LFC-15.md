◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

## Forma Normale di Chomsky
---

>[!info] Definizione
>Una grammatica non contestuale si dice in **forma normale di Chomsky** se ha solo produzioni dei tipi:
>- $X\rightarrow YZ$, con $X,\ Y,\ Z\ \in \ N$,
>- $X\rightarrow a$, con $X\in N,\ a \in \Sigma$,
>- $S \rightarrow \varepsilon$, solo se $S$ non compare nei lati destri delle produzioni.

Questa forma è carina perché l'insieme dei nodi interni può essere rappresentato con un albero binario completo, e le foglie sono figli unici.


## Lo sapevi già che lo avremmo fatto
---

Ovviamente, abbiamo un teorema che consente di derivare ogni linguaggio generato da una grammatica non contestuale in forma normale di Chomsky.

>[!tip] Procedura:
>1. Eliminare $\varepsilon$-produzioni e produzioni unarie;
>2. Ridursi al caso $\gamma \in N^*$ (in cui ogni produzione ha a destra alternativamente un carattere terminale o una lista di variabili);
>3. Per ogni produzione che abbia a destra più di due variabili, si crei una nuova variabile Z, si modificano le due produzioni più a destra (da X a $X_{k-1}$ e a $X_k$) in modo che abbiano Z e non X a sinistra, e si aggiunga la produzione $X\rightarrow X_{1} X_{2}\ ... \ Z$. 

## Forma Normale di Greibach
---

>[!info] Definizione:
>Una grammatica non contestuale G si dice in forma normale di Greibach se ha solo produzioni del tipo:
>- $X \rightarrow a\gamma$,  con $a\in\Sigma$ e $\gamma\in N^*$;
>- $S\rightarrow \varepsilon$, solo se S non compare nei lati destri delle produzioni.

Questa forma normale ha una proprietà molto simpatica, ovvero: ogni derivazione di una parola di lunghezza $n$ richiede esattamente $n$ passi.


## Do you know what is funnier than 25?
---

>[!tip] Teorema
>Ogni linguaggio non contestuale è effettivamente generato da una grammatica non contestuale in forma normale di Greibach.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]