---
autore: Lorenzo Temussi
date:
fonte: slides e lezioni
---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---
# Automi a Stati Finiti non Deterministici

Abbiamo appreso come creare automi a stati deterministici, crearne uno non-deterministico è un processo simile, con una differenza significativa:

- Dati uno stato $q$ e una lettera $a$, lo stato di arrivo non è univoco.

>[!warning] Problema
>Questi automi ci interessano perché rimuovono una costrizione di design e consentono maggior libertà di progettazione a partire da una grammatica, MA gli algoritmi di recognition non sono ben supportati da strutture come questa.

Infatti, ad ogni passo sarebbe necessario valutare ogni arco associato al simbolo di input per ogni percorso ancora non fallito (bloccato in uno stato non finale), si potrebbe avere conferma dell'esito solo alla fine di tutti percorsi (per essere accettata, la parola deve condurre ad almeno uno stato finale) e la complessità del calcolo può sfuggire di mano alla svelta.

>[!check] Soluzione
>Progettiamo un automa non deterministico e poi utilizziamo un algoritmo per trasformarlo in un automa deterministico, sul quale la recognition è una passeggiata.

---

Un automa a stati finiti non deterministico è una quintupla $A= \langle Q, \Sigma , \delta ,q_{0}, F \rangle$ , dove:

- $Q, \Sigma ,q_{0}, F$ sono definiti come nell'automa deterministico
e
- $\delta : Q \times \Sigma \rightarrow P(Q)$;

E una parola $w = a_{1}a_{2}... \ ,$è accettata da $A$ se esistono stati $q_{1}, q_{2}, ... , q_{n}\ \in Q$ tali che:
$$ q_{i} \in \delta (q_{i-1}, a_i), \ 1 \leq i \leq n\ ,\ \ q_n \in F. $$

A questi automi possiamo associare un grafo diretto con frecce etichettate, con la stessa legenda degli automi del capitolo precedente.

>[!error] Media mancanti
>Non sono in grado di produrre grafi belli come quelli del prof. Carpi ancora, verranno inseriti appena lo sarò.

---
## Determinizzazione

>[!info] Teorema
>Sia $A$ un automa a stati finiti non deterministico: esiste sempre un automa a stati finiti deterministico $A'$ tale che:
>
>$$L(A) = L(A').$$

>[!tip] Proprietà
>Per produrre l'automa deterministico A' dall'automa non deterministico A:
>- L'insieme degli stati dell'automa è l'insieme Q' costituito dai sottoinsiemi di Q;
>- Lo stato iniziale è $s_0 = \{q_0\}$;
>- Gli stati finali sono tutti i sottoinsiemi di Q che contengono almeno un elemento di F;
>- la funzione di transizione $\delta^\prime:Q^\prime \times \Sigma \rightarrow Q^\prime$ è definita come:
>$$\delta^\prime(s, a) = \bigcup\limits_{q \in s}\delta(q, a), \ \ \ s \in P(Q), \ a \in \Sigma.$$


Balza subito all'occhio la enorme cardinalità di $Q^\prime$, pari a $2^{|Q|}$, ma questo è dovuto in parte all'esistenza di **stati inaccessibili**. 

>[!info] Definizione
>Uno stato è inaccessibile se non esiste un cammino dallo stato iniziale dell'automa fino ad esso.
>
>Questi stati sono inerti, foglie morte, e possono essere rimossi senza cambiare il linguaggio generato dall'automa o perdere qualsiasi sorta di proprietà dell'automa.

>[!example] Algoritmo di Determinizzazione
>1. inserisco $s_0 = \{q_0\}$;
>2. per ogni stato r della lista e ogni lettera $a \in \Sigma$;
>3. calcolo $s=\delta^\prime (r, a)$;
>4. se s non è nella lista degli stati, allora ->5
>5. appendo s alla lista degli stati;
>6. se inoltre s contiene uno stato finale di $A$, aggiungo s alla lista degli stati finali;

Alcuni automi non-deterministici generano automi deterministici molto complessi che non possono essere semplificati, come ad esempio l'automa deterministico che controlla se una parola ha $l$ come $n-ultima$ lettera su un alfabeto {a,b}, che avrebbe $2^n$ stati contro gli $n+1$ dell'automa non deterministico corrispondente.

---

>[!warning] Raccomando FORTISSIMO 
di cercare su UNISTUDIUM gli esercizi del professore e di praticare l'algoritmo di determinizzazione finché non vi risulta naturale come saltare la corda.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]
