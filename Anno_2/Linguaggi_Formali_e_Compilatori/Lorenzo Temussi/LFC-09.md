◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

Quindi, abbiamo il nostro algoritmo che trasforma un automa a stati finiti nell'equivalente una espressione regolare e vice versa, siamo contenti? Quasi, perché talvolta l'automa è così complesso che derivarne una regex è una seccatura.

Quindi, sapete già dove andiamo a parare con questa premessa, spero. Ci serve un algoritmo per minimizzare l'automa / l'espressione.

---
## Equivalenze

>[!tip] Definizione
>Una relazione riflessiva, simmetrica e transitiva, che partiziona in classi di equivalenza un insieme S sul quale è applicata, e viceversa, ogni partizione di S è associata un'equivalenza che la definisce.

Adesso, troviamo l'equivalenza adatta per semplificare un automa:

>[!warning] Relazione di Congruenza
>Date due lettere $u$ e $v\ \in \Sigma^*$:
>- Se $u,\ v$ hanno gli stessi completamenti a destra (ovvero $uabc \in L \Longleftrightarrow vabc \in L$), si dicono **congruenti a destra**.
>- Se $u,\ v$ hanno gli stessi completamenti a sinistra (ovvero $abcu \in L \Longleftrightarrow abcv \in L$), si dicono **congruenti a destra**.
>- Se $u$ e $v$ sono congruenti a destra e a sinistra, si dicono **congruenti**.

Con questa relazione, possiamo definire una **equivalenza di Nerode**:

>[!tip] Definizione
>Dato un linguaggio L sull'alfabeto $\Sigma$, l'equivalenza di Nerode associata al linguaggio L definita in $\Sigma^*$ è:
>$$u\ N_L\ v\ se\ \forall y \in \Sigma^*,\ \ uy \in L \Longleftrightarrow vy \in L.$$
>
>In altre parole, l'equivalenza di Nerode è una congruenza destra.

---

>[!example] Teorema di Myhill-Nerode
>Dato un linguaggio L sull'alfabeto $\Sigma$, le seguenti proposizioni si equivalgono:
>  (i) L è regolare
> (ii) L è unione di classi di una congruenza destra su $\Sigma^*$ di indice finito
>(iii) $N_L$ ha indice finito
>
>Sul beamer del professore il teorema è dimostrato.

Dato un linguaggio regolare L, l'automa di Nerode di L è un automa deterministico che accetta L con il minimo numero di stati possibile. Questo è dimostrabile a partire dalle dimostrazioni dei teoremi di cui sopra.

Vogliamo dunque trasformare l'automa in partenza in un automa equivalente che abbia per nodi le classi di equivalenza di Nerode, e possiamo farlo seguendo il procedimento di cui sotto.

>[!check] Minimizzazione dell'Automa
>A partire dalla mappa stati $\times$ input:
>1. Etichetto gli stati finali come "classe 1" e gli altri come "classe 0";
>2. Rimpiazzo l'output presente nella griglia con l'etichetta appena assegnata a quello stato;
>3. Compio una suddivisione aggiuntiva che raggruppa gli stati che presentano gli stessi output, questo produrrà nuove classi numerate (per convenzione riserviamo i numeri più grandi agli stati finali);
>4. Se non è cambiato nulla dall'ultima iterazione: go to 5, altrimenti, go to 2;
>5. Hai fatto! Il tuo automa minimo è pronto all'uso.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]
