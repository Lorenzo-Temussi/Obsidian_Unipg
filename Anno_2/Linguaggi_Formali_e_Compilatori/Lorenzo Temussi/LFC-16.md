◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

## Iterazione nei Linguaggi non Contestuali
---

Riportiamo alla mente il Lemma di Iterazione dei linguaggi regolari:

>[!tip] Lemma:
>Dato $L$ linguaggio regolare, $\exists$ un intero $n$ tc. per ogni parola $w\in L$ di lunghezza $|w| \geq n$ si può fattorizzare  $w=xyz$ con $y \neq \varepsilon$ e $xy^kz \in L\  \forall \ k \geq 0$.

Quello relativo ai linguaggi non contestuali è diverso, ma svolge la stessa funzione: una "prova del nove" che, se fallita, smaschera un linguaggio prima creduto non-contestuale come meramente dipendente dal contesto, o peggio ancora (sputa a terra) a struttura di frase.

>[!tip] Lemma:
>Dato $L$ linguaggio non contestuale, $\exists$ un intero $n$ tc. per ogni parola $w\in L$ di lunghezza $|w| \geq n$ si può fattorizzare  $w=xuyvz$ con $uv \neq \varepsilon$ e $xu^kyv^kz \in L\  \forall \ k \geq 0$.


## Dimostrazione
---

Tenetevi forte perché questa senza grafico è pesante:

>[!question] Dimostrazione
>1. Posto $L=L(G)$ con $G$ priva di $\varepsilon$-produzioni e produzioni unarie;
>2. Sia $n$ la massima lunghezza delle parole di $L$ che hanno un albero di derivazione di altezza $\leq \# (N)$;
>3. Sia $w\in L$, con $|w|>n$;
>4. In un cammino di lunghezza $> \# (N)$ dalla radice a una foglia nell'albero di derivazione c'è una variabile che si ripete;
>5. $S \Rightarrow^* xAz,\ \ \ A \Rightarrow^* uAv,\ \ A\Rightarrow^*y,\ \ w=xuyvz,\ \ uv \neq \varepsilon;$
>6. $S\Rightarrow^* xAz \Rightarrow^* xuAvz \Rightarrow^* xuuAvvz \Rightarrow^* .\ .\ .\ \Rightarrow^* xu^kAv^kz \Rightarrow^* xu^kyv^kz;$
>7. quindi $xu^kyv^kz \in L \ \forall k \geq 0$.


---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]