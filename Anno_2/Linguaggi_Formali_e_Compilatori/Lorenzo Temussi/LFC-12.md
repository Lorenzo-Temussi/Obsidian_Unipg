◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

## Analisi Lessicale
---

Durante la compilazione di un file di testo contenente codice sorgente in un dato linguaggio, i processi di Analisi Lessicale (ricerca di Lessemi da rimpiazzare con Token) e Analisi Sintattica (produzione di gerarchie di Token in forma di Alberi) sono separati per aumentare efficienza, portabilità e semplicità di programmazione.

>[!example] Dizionarietto
>#### Token
>Simbolo astratto che rappresenta un'unità lessicale, può essere processato dal parser.
>#### Lessema
>Sequenza di caratteri di un codice sorgente associato ad un token, vengono riconosciuti e tokenizzati dall'analizzatore lessicale.
>#### Pattern
>Regex che descrive la forma di un lessema.
>
>Se un pattern è associato a più di un lessema, si tiene traccia delle informazioni del lessema all'interno di una Tabella dei Simboli.

## Capire i Token
---

La tabella dei simboli sarà simile a questa:

| token             | descrizione informale                 | esempi                        |
| ----------------- | ------------------------------------- | ----------------------------- |
| if                | if                                    | if                            |
| else              | else                                  | else                          |
| comparazione      | <, >, <=, >=, =\= e !=                | <, >, ...                     |
| id                | lettera iniziale, poi lettere e cifre | var, a, x0                    |
| numero            | costante numerica                     | 3.14, 0, 6.02e04              |
| stringa letterale | testo compreso fra due ".             | "Hello Wordl!", " ", "pingas" |

Tipicamente, sarà necessario implementare un token per ogni parola chiave, uno o più per gli operatori, uno per gli id, uno o più per le costanti, e uno per ogni segno di punteggiatura.

I token sono identificati da regex (pattern) e hanno un ordine di priorità.
L'analizzatore lessicale esamina il testo, identifica il prefisso più lungo del testo che sia un lessema [^1], restituisce il primo token in ordine di priorità corrispondente a quel lessema [^2], per poi ricominciare il processo.

## Capire i Pattern
---

Per meglio apprezzare il lavoro svolto dall'analizzatore lessicale immaginiamo di dover risolvere un problema in cui abbiamo:

- Una sequenza finita di regex $E_1, E_2, . . . , E_n$ , che sarebbero i pattern;
- Una parola $w$, che sarebbe il testo da analizzare;

e ci è richiesto di determinare:

- Il più lungo prefisso $u$ di $w$ che appartenga al linguaggio denotato dalla regex $F=E_1, E_2, . . . , E_n$ ;
- il più piccolo indice $j$ tale che $u$ appartenga al linguaggio denotato da $E_j$

##### Svolgimento:

1) Per ogni espressione $E_j$ costruiamo un automa a stati finiti corrispondente che accetta il linguaggio denotato da esso.
2) Facciamo finta che non abbiano stati comuni.
3) Costruiamo l'automa A che accetta il linguaggio denotato da $F=E_1, E_2, . . . , E_n$ , che abbia gli stessi stati, transizioni e stati finali di tutti gli altri automi appena costruiti e un nuovo stato iniziale $i_0$, che porta agli stati iniziali originali degli altri automi mediante $\varepsilon$-transizioni.[^3]
4) Con la costruzione dei sottoinsiemi otteniamo un automa deterministico $A_D=\langle P, \Sigma ,\delta , q_0, F^{'} \rangle$ che accetta il linguaggio denotato da $F$.

Osserviamo che gli stati di $A_D$ sono sottoinsiemi di $Q = \{i_0\} \cup \bigcup^n_{j=1}\ \ Q_j$ e che $w$ è nel linguaggio denotato da $E_j$ sse $f_j\in \hat{\delta}(q_0, u)$.

##### Soluzione:

Troviamo il più lungo prefisso $u$ di $w$ accettato da $A_D$ e il più piccolo indice $j£ tale che $f_i \in \hat{\delta}(q_0, u)$ 

Per sapere quando fermare la ricerca, basta annotare qual è l'ultima transizione da uno stato finale prima dell'arrivo in $\emptyset$ individua il più lungo prefisso di $w$ accettato da $A_D$.

## Dura Lex, sed Lex
---

Il professore introduce Lex, un generatore di analizzatori lessicali.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

[^1]: Ovvero prende la prima lettera non vuota del testo rimanente e scorre tutta la parola che la contiene, per poi dare in output la parola più lunga che a) contenga quella lettera b) sia un lessema noto.

[^2]: I token esistono in una lista ordinata, in modo che, per esempio int sia sempre riconosciuto come tipo e non come nome di variabile.

[^3]: In parole povere, agganciamo tutti gli automi in parallelo.
