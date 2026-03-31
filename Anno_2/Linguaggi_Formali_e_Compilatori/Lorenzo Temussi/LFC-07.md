◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---
# Espressioni Regolari

A questo punto, siamo familiari con le operazioni sui linguaggi, le ripassiamo per sicurezza.

>[!warning] Promemoria
>1. $L_1 \cup L_2$: Linguaggio che include tutte le parole incluse da $L_1$ o $L_2$;
>2. $L_1 \cap L_2$: Linguaggio che include solo le parole incluse sia da $L_1$ che da $L_2$;
>3. $\urcorner L_1$: Linguaggio che include tutte e sole le parole con lo stesso alfabeto di $L_1$, che non sono già incluse in $L_1$;
>4. $L_1 L_2$: Linguaggio che include tutte le parole composte concatenando una parola in $L_1$ e una in $L_2$;
>5. $L^n$: Concatenazione speciale di un linguaggio con sé stesso n volte di fila;
>6. $L^*$: Chiusura di Kleene, unione di tutte le potenze di $L^n \ \forall n > 0$;

>[!check] Operazioni Regolari
>**Unione**, **concatenazione** (e **potenza** obv), e **chiusura di Kleene** sono dette operazioni regolari.

---
Il processo per produrre espressioni regolari a partire da un alfabeto è un po' macchinoso, ma apre la strada all'uso di algoritmi con performance eccellenti:

>[!tip] Processo
>1. Preso un alfabeto $\Sigma$, definiamo come $\hat{\Sigma}$ l'alfabeto creato aggiungendo ad esso le lettere $\emptyset$, +, \*, (, )
>2. Definiamo come espressione regolare sull'alfabeto $\Sigma$ ogni parola sull'alfabeto $\hat{\Sigma}$ composta di un solo simbolo su $\Sigma$, e $\emptyset$.
>3. Inoltre, è un'espressione regolare anche ogni parola creata a partire da espressioni regolari E e F eseguendo le operazioni $(E+F)$, $(EF)$ e $E^*$, (le espressioni regolari di cui sopra).
>   
>   E voilà, adesso possiamo produrre espressioni regolari a piacere dato un alfabeto di partenza.

Per ogni espressione regolare esiste un linguaggio denotato da essa. Per le espressioni mono-simbolo, il linguaggio include solo il simbolo stesso, negli altri casi segue la logica:

>[!example] Linguaggi regolari
>1. $(E+F) \rightarrow L_E \cup L_F$;
>2. $(EF) \rightarrow L_E L_F$;
>3. $E^* \rightarrow L_E^*$

Ricordiamo che la classe dei linguaggi regolari è la più piccola famiglia di linguaggi che contiene i linguaggi finiti ed è chiusa per le operazioni regolari.

>[!tip] Convenzione
>Per risparmiare parentesi adesso che c'è stato l'aumento delle accise, rispettiamo la priorità delle operazioni:
>1. Chiusura di Kleene;
>2. Concatenazione;
>3. Somma;

---
>[!quote] Teorema di Kleene
> Un linguaggio è regolare sse è riconosciuto da un automa a stati finiti. In aggiunta:
> - Esiste un processo detto *sintesi*, che può produrre un automa a stati finiti data un'espressione regolare.
> - Esiste un processo detto *analisi*, che può produrre un'espressione regolare dato un automa a stati finiti.

---

>[!bug] Seguono formule con un sacco di simboli.
>Non le trascrivo, ma sono solo tre algoritmi incredibilmente intuitivi, guardateveli nella molto accessibile fonte originale.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]