---
date:
autore: Lorenzo Temussi
fonte: slides e lezioni
---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---
## Linguaggi Generati

Nell'ultima lezione abbiamo definito una Grammatica a struttura di frase come una quadrupla del tipo:

> [!NOTE] Promemoria
> $V$ (Vocabolario totale);
>  $\Sigma \subseteq V$ (alfabeto dei simboli terminali);
>   $P$ (un insieme di produzioni  finite, della forma $\alpha \rightarrow \beta$ con $\alpha \in V^{*} \setminus \Sigma^{*}$ e $\beta \in V^{*}$);
>   $S \in N = V \setminus \Sigma$ (simbolo iniziale)
> 
> $G = \langle V, \Sigma, P, S \rangle$  
> Le lettere di $N$ si dicono **variabili**.

#### Conseguenze dirette

Prese $\alpha ,  \beta \in V^{*}$  :

Definiamo come **conseguenza diretta** di $\alpha$ ogni $\beta$ che verifica quanto segue:

$\alpha = \gamma_{1} \gamma \gamma_{2}$   ,   $\beta = \gamma_{1} \gamma^{'} \gamma_{2}$   ,   $\exists \ \gamma \rightarrow \gamma^{'} \in P$

>[!note] In parole povere
>Se in seguito ad una Produzione su di una parola-fattore (o sottoparola), di $\alpha$, viene prodotto $\beta$, allora $\beta$ è una **Conseguenza Diretta** di $\alpha$.

La relazione di conseguenza diretta si indica con il simbolo "implica":

   $\alpha \ \Rightarrow \ \beta$      ( $\beta$  è una **Conseguenza Diretta** di $\alpha$ )

#### Conseguenze

La relazione fra due frasi attraverso conseguenze diretta ($\alpha \Rightarrow \alpha_{1} \Rightarrow \alpha_{2} \  ... \ \Rightarrow \beta$)  si dice di conseguenza e si indica con $\alpha \ \Rightarrow ^{*}\ \beta$. La conseguenza diretta stessa può essere immaginata come una conseguenza speciale ad un passo.

Tutte le conseguenze del **simbolo iniziale** $S$ sono riunite sotto il nome di **forme sentenziali**, e il **linguaggio generato** da G altro non è che l'insieme di tutte le forme sentenziali di S **prive di variabili**.

>[!example] Esercizio Suggerito
>Trovare il linguaggio generato di G = $\langle V, \Sigma, P, S \rangle$, sapendo che:
>$V={a, b, S},$ 
>$\Sigma = {a, b},$
>$N={S},$
>$P= \{S \ \rightarrow \ ab, \ \ \  S \ \rightarrow \ aSb\}.$
>>[!check]- Soluzione
>>$S(G) = \{ a^{n}Sb^{n} | n \geq 0\} \cup \{a^{n}b^{n} | n > 0 \}$
>>
>>e L(G) è l'insieme S(G) meno tutte le forme contenenti parole non finali (variabili), ovvero:
>>
>>$L(G) = \{a^{n}b^{n} | n > 0 \}$

Se due grammatiche G generano lo stesso linguaggio L, si dicono equivalenti.

### Problemi su una grammatica

Ora che sappiamo come scrivere una grammatica e generarvi un linguaggio, possiamo utilizzarle per uno scopo nobile: risolvere problemi reali. 

Due problemi classici su una grammatica sono **Recognition** e **Parsing**:

- **Recognition** chiede: a partire da una grammatica G e una parola $w \in \Sigma^{*}$, di determinare se $w \in L(G)$.
- **Parsing** chiede: a partire da una grammatica G e una parola $w \in L(G)$, di individuare una derivazione (la serie di conseguenze dirette) che eseguite su S, portano a $w$.

>[!warning] Perdita di Generalità
>Non esiste un algoritmo capace di risolvere questi problemi per una qualunque grammatica G e lettera $w$. Siamo dunque costretti a trovare dei compromessi fra efficienza dell'algoritmo e espressività delle grammatiche su cui si può applicare.

---

## Chomsky arriva in nostro aiuto

>[!quote] Noam Chomsky, in una lettera a Jeffrey Epstein
>Per quanto riguarda il modo terribile in cui sei trattato dal pubblico e dalla stampa, il modo migliore di navigare la situazione è ignorarlo.

Noam Chomsky, nei suoi scritti, enumera i linguaggi in Tipi, di cui ciascuno è una sottoclasse di quelli di tipo inferiore. Gli algoritmi di parsing e recognition diventano più efficienti con l'aumentare del tipo.

---
# Tipo 0

>[!tip] Definizione:
>Le grammatiche di tipo 0, dette anche "a struttura di frase", generano linguaggi ricorsivamente enumerabili.

Le restrizioni sono quelle viste finora:
- Una quadrupla con un alfabeto, un insieme di simboli terminali, un singolo simbolo iniziale, un insieme di produzioni finite.

>[!example] Esempio
>Segue l'insieme P di una grammatica di tipo 0 che ai più attenti risulterà familiare, gli elementi sono ingrigliati per la vostra miglior convenienza.
>
>
| $S \rightarrow NVS$  | $A \rightarrow N$     | $N \rightarrow a$ |
| :------------------: | --------------------- | :---------------: |
| $S \rightarrow N,AF$ | $A \rightarrow N,A$   | $N \rightarrow b$ |
|                      | $,NF \rightarrow \&N$ | $N \rightarrow c$ |

Alcuni linguaggi di tipo 0 non sono riconoscibili né parsabili.

---
# Tipo 1

>[!tip] Definizione:
>Le grammatiche di tipo 1, dette anche "context sensitive", sono una sottoclasse del tipo 0, e producono linguaggi context sensitive.
>
>L'insieme P di una grammatica di tipo 1 contiene solo elementi del tipo:
>$$\alpha_{1}X\alpha_{2} \ \rightarrow \alpha_{1}\beta\alpha_{2} \ \ , \ \ con \ X\ \in \ N ,\ \ \  \alpha_{1}, \alpha_{2}, \beta \ \in \ V^{*}, \ \ \ \beta \neq \varepsilon.$$

>[!example] Esempio
>Segue l'insieme P di una grammatica di tipo 1 equivalente alla grammatica di tipo 0 di cui sopra, gli elementi sono ingrigliati per la vostra miglior convenienza.
>
| $S \rightarrow NVS$ | $VN \rightarrow ,N$  | $N \rightarrow a$ | $U \rightarrow a$ |
| :-----------------: | -------------------- | :---------------: | ----------------- |
|  $S \rightarrow U$  | $VU \rightarrow \&U$ | $N \rightarrow b$ | $U \rightarrow b$ |
|                     |                      | $N \rightarrow c$ | $U \rightarrow c$ |

La restrizione principale dei linguaggi di tipo è la non-restringibilità della stringa, che sarebbe infranta per esempio da $,NF \rightarrow \&N$ .

Ricordiamo che se due grammatiche sono equivalenti, non vuol dire che siano "dello stesso tipo", significa solo che esiste una grammatica di un altro tipo che genera lo stesso linguaggio. Per i nostri interessi l'ideale sarebbe scegliere la grammatica di tipo più alto capace di generare il linguaggio che ci serve.

>[!tip] Definizione:
>Una grammatica di dice **monotòna** se tutte le produzioni in P hanno forma:
>
>$$\alpha \rightarrow \beta \ \ \ con \ \ |\alpha | \leq |\beta |.$$

Le grammatiche monotone:
- comprendono ogni singola grammatica di tipo 1;
- NON sono tutte di tipo 1;
- sono sempre equivalenti ad una grammatica di tipo 1;

Senza fare un intero esempio, una produzione di tipo $bB \rightarrow Bb$ non infrange il principio di monotonia, ma infrange il principio del tipo 1.

Algoritmi molto costosi possono risolvere i problemi di recognition e parsing per ogni linguaggio di tipo 1.

---
# Tipo 2

>[!tip] Definizione:
>Le grammatiche di tipo 2, dette anche "context-free", sono una sottoclasse del tipo 1, e producono linguaggi context-free.
>
>L'insieme P di una grammatica di tipo 2 contiene solo elementi del tipo:
>$$X \ \rightarrow \beta \ \ , \ \ con \ X\ \in \ N ,\ \ \   \beta \ \in \ V^{*} \ \ $$

>[!example] Esempio
>Segue l'insieme P di una grammatica di tipo 2 equivalente alla grammatica di tipo 1 di cui sopra, gli elementi sono ingrigliati per la vostra miglior convenienza.
>
>
| $S \rightarrow N$ | $M \rightarrow N,M$  | $N \rightarrow a$ |
| :---------------: | -------------------- | :---------------: |
| $S \rightarrow M$ | $M \rightarrow N\&N$ | $N \rightarrow b$ |
|                   |                      | $N \rightarrow c$ |

In altre parole, ogni produzione parte sempre e solo da un singolo simbolo.

Gli algoritmi di recognition e parsing per grammatiche di tipo 2 sono effettivamente efficaci, e hanno importanti applicazioni nell'analisi sintattica.

---
# Tipo 3

>[!tip] Definizione:
>Le grammatiche di tipo 3, dette anche "regolari", sono una sottoclasse del tipo 2, e producono linguaggi regolari.
>
>L'insieme P di una grammatica di tipo 3 contiene solo elementi del tipo:
>$$X \ \rightarrow aY \ \ oppure \ \ X \ \rightarrow \ a, \ \ con \ X,\ Y\ \in \ N ,\ \ \   a \ \in \ \Sigma \ \ $$

>[!example] Esempio
>Segue l'insieme P di una grammatica di tipo 2 equivalente alla grammatica di tipo 1 di cui sopra, gli elementi sono ingrigliati per la vostra miglior convenienza.
>
>
| $S \rightarrow a$ | $S \rightarrow aR$ | $R \rightarrow \&N$ | $M \rightarrow aR$ | $N \rightarrow a$ |
| :---------------: | ------------------ | ------------------- | ------------------ | :---------------: |
| $S \rightarrow b$ | $S \rightarrow bR$ | $R \rightarrow ,M$  | $M \rightarrow bR$ | $N \rightarrow b$ |
| $S \rightarrow c$ | $S \rightarrow cR$ |                     | $M \rightarrow cR$ | $N \rightarrow c$ |

Notare che ogni produzione deve avere in output almeno un simbolo terminale, e non può restituire un'espressione con simboli non terminali alla sinistra di simboli terminali.

Gli algoritmi per recognition dei linguaggi di tipo 3 hanno importanti applicazioni nell'analisi lessicale.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]