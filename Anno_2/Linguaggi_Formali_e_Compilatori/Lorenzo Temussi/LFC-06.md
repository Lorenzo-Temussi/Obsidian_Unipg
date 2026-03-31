◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---
# $\varepsilon$-transizioni

Ok, se vi ricordate gli automi non deterministici del capitolo precedente, gli ANDSF possono, dati un input e uno stato, produrre più stati diversi in output, ma sono comunque vincolati ad attendere un input per produrre un output, per cui l'algoritmo di recognition richiede esattamente tanti passi quassi i simboli nella parola di input. 

Ebbene, esiste un sottoinsieme di automi per cui questo principio non vale.

>[!tip] Accessibility
>Per i gentiluomini e gentildonne che richiedono input visuale, segue un grafo.

![[Screenshot 2026-03-29 at 16-14-19 (PNG Image 800 × 600 pixels).png]]

Il grafo di cui sopra descrive il processo di recognition di un numero binario razionale, cosa significa la $\varepsilon$ in uscita da $q_0$?

>[!example] Definizione
>Un automa a stati finiti non deterministico con $\varepsilon$-transizioni è una quintupla:
>$$ A= \langle Q, \Sigma, \delta, q_0, F \rangle \ , $$
>definita in modo analogo a quella degli ASFND, eccetto per quanto riguarda $\delta$, che accetta in input anche la lettera vuota $\varepsilon$ (corrispondente ad una transizione extra, che non richiede nessun simbolo per essere eseguita).

Il grafo è esattamente uguale ad un grafo di un ASFND con $\varepsilon$ come possibile etichetta per i lati.

Segue la scrittura in tabella equivalente al grafo di cui sopra:


| $\delta$ | \|    | $\varepsilon$ | +           | -           | .           | 0              | 1              | \|    | F        |
| -------- | ----- | ------------- | ----------- | ----------- | ----------- | -------------- | -------------- | ----- | -------- |
| ---      | \|--- | ---           | ---         | ---         | ---         | ---            | ---            | \|--- | ---      |
| $q_0$    | \|    | $\{q_1\}$     | $\{q_1\}$   | $\{q_1\}$   | $\emptyset$ | $\emptyset$    | $\emptyset$    | \|    |          |
| $q_1$    | \|    | $\emptyset$   | $\emptyset$ | $\emptyset$ | $\{q_2\}$   | $\{q_1, q_3\}$ | $\{q_1, q_3\}$ | \|    |          |
| $q_2$    | \|    | $\emptyset$   | $\emptyset$ | $\emptyset$ | $\emptyset$ | $\{q_4\}$      | $\{q_4\}$      | \|    |          |
| $q_3$    | \|    | $\emptyset$   | $\emptyset$ | $\emptyset$ | $\{q_4\}$   | $\emptyset$    | $\emptyset$    | \|    |          |
| $q_4$    | \|    | $\emptyset$   | $\emptyset$ | $\emptyset$ | $\emptyset$ | $\{q_4\}$      | $\{q_4\}$      | \|    | $\times$ |

Un modo ancora più comodo di scrivere un automa a parte da una grammatica. Certo che questi lati $\varepsilon$ sono un po' una seccatura per i nostri algoritmi, chissà se esiste un modo per sbarazzarsene...

No, non dirmi che...

## Esatto, determinizziamo pure questi automi

>[!tip] Teorema
>Dato un qualsiasi $A$, automa a stati finiti non deterministico con $\varepsilon$-transizioni, esiste effettivamente un automa a stati finiti deterministico $A^\prime$ tale che:
>$$L(A) = L(A^\prime).$$

L'utilità di questo processo è tale che quando esci di casa dovresti stare attento che la porta sia chiusa così non posso entrarti in casa e determinizzare tua nonna.

>[!info] Definizione
>Preso un automa a stati finiti non deterministico con $\varepsilon$-transizioni, la **$\varepsilon$-chiusura** di un suo stato q è l'insieme di tutti gli stati raggiungibili attraverso un cammino di soli $\varepsilon$-transizioni partendo da q, e include q.
>
>L'insieme delle $\varepsilon$-chiusure di un insieme di stati $q_0,q_1, ..., q_n$ è l'unione degli insiemi $\varepsilon$-chiusura di ogni stato preso singolarmente.

Il processo di determinizzazione è poi analogo a quello già visto, eccetto che i nuovi stati dell'automa deterministico sono basati sull'unione delle $\varepsilon$-chiusure degli stati di arrivo di una transizione, e non sull'unione degli stati stessi.

C'è un bell'esempio sul beamer del professore, guardatelo, io non intendo copiarlo a mano con tanto di tabella (no offesa).

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]