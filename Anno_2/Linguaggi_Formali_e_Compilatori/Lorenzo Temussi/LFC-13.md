◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

## Linguaggi non contestuali
---

Anziché da un concetto partiamo da un esempio:

Sia P il linguaggio delle palindrome sull'alfabeto $\Sigma = \{a,\ b\}$:

Ogni palindroma si ottiene partendo da $\varepsilon, a$ o $b$, e aggiungendo una $a$ o $b$ all'inizio e alla fine della parola.

$$P=\varepsilon + a +b +aPa + bPb$$
Qui sopra abbiamo ora l'algoritmo ricorsivo per verificare se una parola è palindroma, e (qui sotto) la grammatica delle palindrome.

$$S\rightarrow\varepsilon,\ \ \ S\rightarrow a,\ \ \ S\rightarrow b,\ \ \ S\rightarrow aSa,\ \ \ S\rightarrow bSb.$$

### Grammatiche Non-Contestuali
---

Abbiamo già esaminato le Grammatiche Non-Contestuali nella [[LFC-03]], per sicurezza ricordiamo che hanno forma:

$$X\rightarrow \alpha,\ \ \ ,\ con\ X \in N,\ \ \alpha \in V^*$$
Se ci fermiamo un minuto a ragionare, vedremo che le grammatiche lineari destre sono un sottoinsieme stretto delle grammatiche non-contestuali.

## Linguaggio di Dick
---

Che nome fortunato, e anche serio. 

Dati:
- $\Sigma_n = \{a_1, a_2,\ .\ .\ .\ , a_n, b_1, b_2,\ .\ .\ .\ ,b_n\}$ ;
- $P= \{ S\rightarrow a_iSb_i,\ \ \ i=1,2,\ .\ .\ .\ n,$
  $S\rightarrow SS,$
  $S\rightarrow\varepsilon.\}$
- $G_n=\langle V, \Sigma_n, P, S \rangle$ con unica variabile $S$.

Il Linguaggio $D_n$ generato da $G_n$ è detto il Linguaggio di Dick. Un esempio di linguaggio di Dick è la grammatica delle parentesi.

Segue un esempio lunghissimo di cui non ho per forza capito lo scopo, in cui scriviamo una grammatica che produce tutte le regex di un alfabeto.

## Alberi di Derivazione
---

Sono alberi con:
- Radice;
- Figli Ordinati per ogni nodo;
- Etichette sui nodi;
  
  E dunque foglie totalmente ordinate.

>[!tip] Nota
>Per la gente nata stamani alle 10 di mattina:
>Un albero è un grafo orientato con un nodo d'origine (radice), nodi collegati ad un "genitore" (l'unico nodo da cui si può raggiungere questo in un passo solo) e a zero o più "figli" (nodi raggiungibili da questo in un solo passo).
>
>"Etichettati" significa che ad ogni nodo è assegnato "qualcosa", tipicamente un numero, nel nostro caso una espressione.

#### Per creare un albero T di derivazione dalla grammatica G:

1. L'etichetta della radice deve essere S;
2. Le etichette dei nodi interni sono elementi di N;
3. Le etichette delle foglie sono elementi $\beta \in \Sigma \cup \{\varepsilon\}$;
4. Le foglie con etichetta $\varepsilon$ sono le uniche figlie dei loro genitori;
5. Se un nodo con etichetta $X$ ha figli etichettati, nell'ordine, $\alpha_1, \alpha_2, \ .\ .\ ., \alpha_k,$ allora $X\rightarrow \alpha_1 \cdot \cdot \cdot \alpha_k$ è una produzione di $G$.

Questo albero ha una parola associata riconosciuta nella grammatica G, che si ottiene leggendo le etichette delle foglie in ordine.

**Tutte e sole** le parole in G hanno un albero di derivazione associato.

Se in una grammatica $G_{NA}$ ad ogni parola corrisponde solamente un albero di derivazione (il caso generale ne prevede un numero a piacere), si dice una **Grammatica Non Ambigua**.

Ultimo sforzo, ricorderete certamente come ogni linguaggio possa essere generato da più di una grammatica? Ebbene, se nessuna delle grammatiche che generano un linguaggio non-contestuale è non-ambigua, il linguaggio si dice **Inerentemente Ambiguo**.


---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]