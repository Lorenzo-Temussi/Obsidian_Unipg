---
autore: Lorenzo Temussi
date:
fonte: slides e lezioni
---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---
# Automi a Stati Finiti

Gli **automi a stati finiti** (che da adesso in avanti saranno abbreviati in ASF per brevità) sono degli adorabili costrutti informatici che funzionano più o meno come macchine di Turing a memoria finita e sono rappresentate con dei **grafi orientati**.

Sono dotati di un numero finito di configurazioni interne (stati), un nastro di input diviso in celle, e un cursore che scorre una cella ad ogni suddivisione di tempo, e può passare da uno stato all'altro a seconda del contenuto della cella e dello stato precedente. 

Un automa del genere può facilmente essere utilizzato per risolvere problemi di recognition a patto che:
- Gli stati siano organizzati in modo tale da imitare la grammatica di un linguaggio;
- I simboli della parola siano scritti in ordine ciascuno in una cella di memoria contigua;
- Alcuni stati siano contrassegnati come "finali" (ovvero, convalidanti della parola).

---

## L'automa a stati finiti deterministico

Un ASF deterministico (ovvero uno a cui ogni coppia stato-simbolo corrisponda un solo stato in output) può essere scritto come quintupla $A$:

$$A = \langle Q, \Sigma, \delta, q_{0}, F \rangle,$$
ove

- $Q$ è un ==insieme finito di stati==;
- $\Sigma$ è un ==alfabeto di input==;
- $\delta \ : \ Q \times \Sigma \rightarrow Q$ è la ==funzione di transizione==;
- $q_{0} \in Q$ è lo ==stato iniziale==;
- $F \subseteq Q$ è l'==insieme degli stati finali==.

>[!example] Esempio
>
| $Q=\{q_{0}, q_{1}, q_{2}\}$ |     | $\delta$    | ==$\alpha$== | ==$\beta$== |
| --------------------------- | --- | ----------- | ------------ | ----------- |
| $\Sigma = \{a, b\}$         |     | ==$q_{0}$== | $q_{0}$      | $q_{1}$     |
| $F=\{q_{0}, q_{1}\}$        |     | ==$q_{1}$== | $q_{2}$      | $q_{1}$     |
|                             |     | ==$q_{2}$== | $q_{2}$      | $q_{2}$     |

Una funzione $\delta$ può essere estesa a $\hat{\delta}$ (la prima è applicata su un alfabeto, la seconda sulla chiusura di Kleene dell'alfabeto stesso) ponendo:

- $\hat{\delta}(q, \varepsilon) = q\  ,\ \ \ \ per\ ogni\ q\ \in Q\ ,$
- $\hat{\delta}(q, va) = \delta(\hat{\delta}(q, v), a)\  ,\ \ \ \ per\ ogni\ q\ \in Q\ ,$

La funzione $\hat{\delta}$ si comporta dunque come un cursore, e "scorre" tutte le lettere dalla prima all'ultima (all'ultima lettera si applica la prima proprietà), e lo stato ottenuto da una valutazione viene usato come stato-argomento della valutazione successiva.

>[!example] Esempio
>Calcoliamo $\hat{\delta}(q_{0}, aabb)$ per l'automa precedente:
>
>$$\hat{\delta}(q_{0}, \varepsilon) = q_{0},$$
>$$\hat{\delta}(q_{0}, a) = \delta(\hat{\delta}(q_{0}, \varepsilon), a) = \delta(q_{0}, a) = q_{0}, $$
>$$\hat{\delta}(q_{0}, aa) = \delta(\hat{\delta}(q_{0}, a), a) = \delta(q_{0}, a) = q_{0}, $$
>$$\hat{\delta}(q_{0}, aab) = \delta(\hat{\delta}(q_{0}, aa), b) = \delta(q_{0}, b) = q_{1}, $$
>$$\hat{\delta}(q_{0}, aabb) = \delta(\hat{\delta}(q_{0}, aab), b) = \delta(q_{1}, b) = q_{1}. $$

Ora che abbiamo compreso il funzionamento della funzione, possiamo offrire una definizione di Linguaggio accettato da un automa:

>[!tip] Definizione
>L'insieme delle parole accettate da $A$ si dice linguaggio riconosciuto(o accettato) da $A$ e si denota $L(A)$.
>
>$$L(A) = \{w \in \Sigma^{*} | \hat{\delta}(q_{0}, w) \in F\}$$

Questo calcolo ha complessità lineare, in quanto richiede tanti passaggi quanti sono i simboli in input.

>[!warning] Janky Graphics
>A ogni automa $A = \langle Q, \Sigma, \delta, q_{0}, F \rangle,$ associamo un grafo orientato etichettato disegnato tremendo con mermaid. Segue il grafo dell'Automa descritto precedentemente negli esempi.
>- I vertici saranno gli stati;
>- Le frecce sono triple $(q, a, \delta (q, a))$;
>- Segnaliamo stato iniziale (freccia entrante) e stati finali (bordo doppio);

>[!bug] Non ci sono riuscito
>Mermaid è un macello, eccovi però un ASF disegnato con un tool online che ho trovato. Chi ride perde i privilegi di pull request.

![[ASF1.png]]

Seguono una serie di altri esempi educativi che potete guardare direttamente dalle slide scusate ma sta cosa è pessima e basta.

---

◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]