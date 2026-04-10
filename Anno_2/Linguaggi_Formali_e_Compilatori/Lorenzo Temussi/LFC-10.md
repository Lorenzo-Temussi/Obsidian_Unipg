◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---
# Lemmi di Iterazione dei Linguaggi Regolari

>[!info] Lemma
>Per ogni dato L linguaggio regolare, esiste un intero $n$ tale che ogni parola $w \in L$ con lunghezza $\geq n$ può essere fattorizzata come $w=xyz$ con $y\neq \varepsilon$ e
>$$xy^mz \in L \ \ \forall \ m\geq 0$$
>

Ovvero: se il linguaggio è regolare, esiste una lunghezza massima che una parola può avere senza avere cicli di caratteri infinitamente iterabili al suo interno. Intuitiva se pensiamo all'automa a stati finiti: certamente nessuna parola può raggiungere una lunghezza infinita senza passare nuovamente per uno degli stati (finiti) in cui è già passata.

La naturale conseguenza è che ogni linguaggio privo di questa proprietà non è regolare, ma sembra solo (per quanto taluni linguaggi hanno questa proprietà senza essere regolari).

>[!example] Esempio
>Certamente il linguaggio $L={a^mb^m|m\geq0}$ è regolare... giusto?
>In realtà no: pensiamo alla formula $xy^mz$, in questo linguaggio y può essere solamente:
>- Una serie di $a$ (che spariglierebbe il numero delle a rispetto alle b);
>- Una parola di forma $a^nb^m$ (che porterebbe ad avere delle a a destra della b più a sinistra);
>- Una serie di $b$ (che spariglierebbe il numero delle b rispetto alle a);
>  
>  E abbiamo dimostrato la non-regolarità senza dover costruire un'aberrazione gigante di grafo. Useremo il tempo risparmiato per grindare gli LP su Guilty Gear: STRIVE.

Sì ok i casi 1 e 3 sono solo casi speciali del caso 2 ma non ci chiamiamo tutti Jimmy Neutron quindi li elenco tutti e tre.

Fine.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]