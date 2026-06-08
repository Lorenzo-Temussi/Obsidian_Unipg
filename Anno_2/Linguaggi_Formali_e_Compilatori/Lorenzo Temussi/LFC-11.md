◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

## Grammatiche Regolari
----

La definizione precedente di Grammatica Regolare è molto accurata, ma la emendiamo con una clausola:

>[!tip] Definizione:
>Le grammatiche di tipo 3, dette anche "regolari", sono una sottoclasse del tipo 2, e producono linguaggi regolari.
>
>L'insieme P di una grammatica di tipo 3 contiene solo elementi del tipo:
>$$X \ \rightarrow aY \ \ oppure \ \ X \ \rightarrow \ a, \ \ con \ X,\ Y\ \in \ N ,\ \ \   a \ \in \ \Sigma \ \ $$

>[!note] Inoltre
>Nel caso in cui lo stato iniziale $S$ non sia presente nel lato destro di alcuna produzione, può essere inclusa la produzione $S\rightarrow\varepsilon$ 

## Dalla Grammatica all'Automa
---

Possiamo costruire un automa non deterministico $A$ a partire da una Grammatica Regolare G:
- Gli stati sono le variabili di $G$, e $\varepsilon$;
- Lo stato iniziale è $S$, lo stato finale è $\varepsilon$;
- Ogni produzione $X\rightarrow aY$ corrisponde ad un lato $X \overset {a} \longrightarrow Y$;
- Ogni produzione $X\rightarrow a$ corrisponde ad un lato $X \overset {a} \longrightarrow \varepsilon$;

Se la parola vuota è inclusa nel linguaggio, allora anche $S$ deve essere uno stato finale.

## Dall'Automa alla Grammatica
---

Possiamo costruire una Grammatica Regolare G a partire da un automa non deterministico $A$:
- le variabili di $G$ sono gli stati di $A$;
- Il simbolo iniziale è $q_0$ ;
- Ogni lato $X \overset {a} \longrightarrow Y$ corrisponde ad una produzione $X\rightarrow aY$ ;
- Se Y è uno stato finale, allora aggiungiamo a $G$ anche la produzione $Y\rightarrow aY$;

Se $\varepsilon$ è contenuta nel linguaggio generato da $A$, sarà bene modificare la Grammatica $G$ di conseguenza:
- Se S non compare nel lato dx di una produzione, aggiungo $S\rightarrow \varepsilon$;
- Altrimenti, introduco la variabile $S'$ le cui produzioni hanno gli stessi lati dx delle produzioni di S, la rendo il nuovo stato iniziale e poi aggiungo $S'\rightarrow \varepsilon$.

## Grammatiche Lineari
---
>[!tip] Definizione
>Una Grammatica Lineare ha tutte e sole produzioni del tipo:
>$$X\rightarrow uYv \ \ o\ \ X\rightarrow u\ ,$$
>con $X, Y \in N$ e $u,v\in \Sigma^*$.
>
>Un sottotipo detto Lineare Destra ha sole produzione di tipo:
>$$X\rightarrow uY\ \ o\ \ X\rightarrow u\ ,$$
>con $X, Y \in N$ e $u\in \Sigma^*$.

Le Grammatiche Regolari viste finora sono lineari destre, inoltre
Le Grammatiche Lineari Destre generano Linguaggi Lineari, e dunque:

>[!warning] Teorema
>Un linguaggio è accettato da un ASF sse è generato da una grammatica lineare destra.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]
