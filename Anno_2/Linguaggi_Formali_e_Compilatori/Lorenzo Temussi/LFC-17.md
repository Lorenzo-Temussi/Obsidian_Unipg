◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

## Algoritmo di Cocke-Kasami-Younger
---

Certamente ricorderete i nostri amati problemi sulle grammatiche. Li riporto sotto per la settima volta:

- **Recognition** chiede: a partire da una grammatica G e una parola $w \in \Sigma^{*}$, di determinare se $w \in L(G)$.
- **Parsing** chiede: a partire da una grammatica G e una parola $w \in L(G)$, di individuare una derivazione (la serie di conseguenze dirette) che eseguite su S, portano a $w$.

Abbiamo visto che esistono algoritmi efficaci per risolvere questi problemi in una grammatica/linguaggio regolare, ma magari ci serve di applicarli su di un linguaggio di tipo 2, cosa possiamo fare?

#### L'algoritmo CYK
---

Poste:
- $G$ grammatica in forma normale di Chomsky;
- $w$ parola al suo interno, scrivibile come stringa di lettere $w=a_1a_2\cdot\cdot\cdot a_n$;

vogliamo calcolare, per $0 \leq i < j \leq n$, tutte le variabili da cui si può derivare il fattore $a_{i+1}a_{1+2}\cdot \cdot \cdot a_{j}$ ;

Per $i=0,\ j=n$, avrò le variabili da cui si può derivare $w$ ; quindi $w \in L(G)$ sse il simbolo iniziale $S$ è una di tali variabili.


>[!bug] Stumpo
>Questo articolo NON è finito. Devo tornare a sistemarlo. TODO e tutto il resto.



---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]