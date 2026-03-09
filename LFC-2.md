Lezione di [[Linguaggi Formali e Compilatori]] del 

Ogni descrizione di qualsiasi cosa avviene tramite la mediazione di un linguaggio, composto di parole. Descrivere un linguaggio finito è semplice, basta elencare le parole che contiene, ma un linguaggio infinito?

Il Teorema di Cantor sostiene che non esista una funzione iniettiva di $\mathcal{P}$($\Sigma^{*}$) in $\Sigma^{*}$, ovvero che non sia possibile associare ad ogni linguaggio una sua descrizione univoca.

Di alcuni linguaggi infiniti è tuttavia possibile dare una descrizione finita, in particolare dato un linguaggio $\mathbf{L}$, il linguaggio $\mathbf{L}^{*}$ dato da tutte le combinazioni di parole in $\mathbf{L}$, ovvero la sua chiusura di Kleene, è sia ben definito che, tipicamente, infinito. 

##### Definizioni

Un alfabeto è un insieme non vuoto $\Sigma$ di simboli, detti lettere.

Una sequenza finita di lettere di $\Sigma$ si dice parola sull'alfabeto $\Sigma$. 

L'insieme di tutte le parole sull'alfabeto $\Sigma$ si denoterà con $\Sigma^{*}$.

La sequenza di zero lettere, che si denota con $\varepsilon$ o con $\Lambda$, si dice parola vuota.

La lunghezza di una parola u si indica con $\mathcal{l}$(u), o con $|u|$.

L'operazione di concatenazione di due parole produce una parola composta delle lettere della prima in ordine seguite da quelle della seconda parola. L'operazione è binaria (totale) su $\Sigma^{*}$.

L'operazione di potenza è una serie di concatenazioni della stessa parola con numero di iterazioni pari all'esponente.

Una parola v è fattore di una parola w sse risulta che w=xvy per opportune parole x e y. Se x=$\varepsilon$ v si dice prefisso di w, se y=$\varepsilon$ v si dice suffisso di w. Si dice che v è fattore proprio di w se v$\neq$w.

Ogni sottoinsieme di $\Sigma^{*}$ si dice linguaggio formale (o solo linguaggio) sull'alfabeto $\Sigma$.

Se abbiamo un alfabeto finito V (detto Vocabolario totale), $\Sigma\subseteq V$ (detto alfabeto dei Simboli terminali), un insieme delle produzioni  P (insieme finito di espressioni della forma $\alpha\rightarrow\beta$ con $\alpha\in V^{*}\setminus\Sigma^{*}$ e $\beta\in V^{*}$) e  simbolo iniziale $S\in N=V\setminus\Sigma$ , possiamo definire una grammatica a struttura di frase:

G = $\langle V, \Sigma , P, S\rangle$ 

Le lettere di N si dicono variabili.

Posti $\alpha ,\beta  \in V^{*}$ :
- $\beta$ è detta una conseguenza diretta di $\alpha$ ($\alpha \Rightarrow \beta$) se esistono parole $\gamma_{1}, \gamma_{2} \in V^{*}$ e una produzione $\gamma \rightarrow \gamma'$ in P tali che:
	$\alpha = \gamma_{1}\gamma\gamma_{2},    \beta = \gamma_{1}\gamma'\gamma_{2}$
- $\beta$ è detta una conseguenza di $\alpha$ in G ($\alpha \Rightarrow^{*} \beta$) se esistono $n<0,  \alpha_{0},  \alpha_{1}, ..., \alpha_{n} \in V^{*}$   tali che $\alpha = \alpha_{0} \Rightarrow \alpha_{1} \Rightarrow ... \Rightarrow \alpha_{n} = \beta$
- Le conseguenze del simbolo iniziale S si dicono forme sentenziali
- Il Linguaggio Generato da G è l'insieme delle forme sentenziali prive di variabili.
##### Convenzioni
Le variabili si indicano con A, B, C, D ...
I simboli terminali con $a, b, c, \dots$
Le parole sull'alfabeto V con $\alpha , \beta , \gamma , ...$
Le parole sull'alfabeto $\Sigma$ dei terminali con $u, v, w, \dots$


##### Caso Studio

G = $\langle V, \Sigma , P, S\rangle$ 

N= {$\langle frase \rangle$, $\langle listaNomi\rangle$, $\langle fineLista\rangle$, $\langle nome\rangle$}
$\Sigma$={'Aldo', 'Bianca', 'Carlo', 'e', ',', ' '}
V=N $\cup$ $\Sigma$ 
P= {
	$\langle nome\rangle \rightarrow \langle Aldo \rangle$ 
	$\langle nome\rangle \rightarrow \langle Bianca\rangle$
	$\langle nome\rangle \rightarrow \langle Carlo\rangle$
	$\langle frase\rangle \rightarrow \langle nome\rangle$
	$\langle frase\rangle \rightarrow \langle listaNomi \rangle \langle fineLista \rangle$
	$\langle listaNomi \rangle \rightarrow \langle nome \rangle$
	$\langle listaNomi \rangle \rightarrow \langle nome \rangle, \langle listaNomi\rangle$
	$, \langle nome\rangle \langle fineLista\rangle \rightarrow e \langle nome \rangle$ }

S=$\langle frase\rangle$

In questo caso, questo linguaggio formale G ci consente di scrivere varie frasi diverse, fra cui, quella che ci interesserà di più sarà:

"Aldo, Bianca e Carlo"