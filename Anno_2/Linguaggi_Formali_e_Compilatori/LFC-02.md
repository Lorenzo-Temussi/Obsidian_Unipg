---
autore: Lorenzo Temussi
date: 2026-02-27
---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

## I. Introduzione ai Linguaggi Formali

Ogni descrizione di qualsiasi cosa avviene tramite la mediazione di un linguaggio, composto di parole. Descrivere un linguaggio finito è semplice, basta elencare le parole che contiene, ma un linguaggio infinito?

Il Teorema di Cantor sostiene che non esista una funzione iniettiva di $\mathcal{P}(\Sigma^{*})$ in $\Sigma^{*}$, ovvero che non sia possibile associare ad ogni linguaggio una sua descrizione univoca.

Di alcuni linguaggi infiniti è tuttavia possibile dare una descrizione finita, in particolare dato un linguaggio $\mathbf{L}$, il linguaggio $\mathbf{L}^{*}$ dato da tutte le combinazioni di parole in $\mathbf{L}$, ovvero la sua chiusura di Kleene, è sia ben definito che, tipicamente, infinito.

---

## II. Definizioni Fondamentali

- **Alfabeto:** insieme non vuoto $\Sigma$ di simboli, detti lettere.
    
- **Parola:** sequenza finita di lettere di $\Sigma$.
    
- **Insieme di tutte le parole:** denotato con $\Sigma^{*}$.
    
- **Parola vuota:** sequenza di zero lettere, denotata $\varepsilon$ o $\Lambda$.
    
- **Lunghezza di una parola $u$:** $\mathcal{l}(u)$ o $|u|$.
    
- **Concatenazione:** operazione che produce una parola composta delle lettere della prima in ordine seguite da quelle della seconda. L’operazione è binaria (totale) su $\Sigma^{*}$.
    
- **Potenza di una parola:** serie di concatenazioni della stessa parola, numero di iterazioni pari all’esponente.
    
- **Fattore di una parola $w$:** parola $v$ sse $w = x v y$ per opportune parole $x$ e $y$.
    
    - Se $x = \varepsilon$, $v$ è **prefisso** di $w$.
        
    - Se $y = \varepsilon$, $v$ è **suffisso** di $w$.
        
    - $v$ è **fattore proprio** di $w$ se $v \neq w$.
        
- **Linguaggio formale:** ogni sottoinsieme di $\Sigma^{*}$.
    

> [!NOTE] Vocabolario, Alfabeti e Produzioni  
> Se abbiamo un alfabeto finito $V$ (Vocabolario totale), $\Sigma \subseteq V$ (alfabeto dei simboli terminali), un insieme di produzioni $P$ (finite, della forma $\alpha \rightarrow \beta$ con $\alpha \in V^{*} \setminus \Sigma^{*}$ e $\beta \in V^{*}$) e simbolo iniziale $S \in N = V \setminus \Sigma$, possiamo definire una **grammatica a struttura di frase**:
> 
> $G = \langle V, \Sigma, P, S \rangle$  
> Le lettere di $N$ si dicono **variabili**.

Posti $\alpha, \beta \in V^{*}$:

- $\beta$ è detta **conseguenza diretta** di $\alpha$ ($\alpha \Rightarrow \beta$) se esistono parole $\gamma_{1}, \gamma_{2} \in V^{*}$ e una produzione $\gamma \rightarrow \gamma'$ in $P$ tali che:  
    α=γ1γγ2,β=γ1γ′γ2\alpha = \gamma_{1} \gamma \gamma_{2}, \quad \beta = \gamma_{1} \gamma' \gamma_{2}α=γ1​γγ2​,β=γ1​γ′γ2​
    
- $\beta$ è detta **conseguenza** di $\alpha$ in $G$ ($\alpha \Rightarrow^{*} \beta$) se esistono $n < 0, \alpha_{0}, \alpha_{1}, ..., \alpha_{n} \in V^{*}$ tali che:  
    α=α0⇒α1⇒⋯⇒αn=β\alpha = \alpha_{0} \Rightarrow \alpha_{1} \Rightarrow \dots \Rightarrow \alpha_{n} = \betaα=α0​⇒α1​⇒⋯⇒αn​=β
    
- Le conseguenze del simbolo iniziale $S$ si dicono **forme sentenziali**.
    
- Il **Linguaggio Generato** da $G$ è l’insieme delle forme sentenziali prive di variabili.
    

---

## III. Convenzioni

- Variabili: $A, B, C, D, ...$
    
- Simboli terminali: $a, b, c, ...$
    
- Parole sull’alfabeto $V$: $\alpha, \beta, \gamma, ...$
    
- Parole sull’alfabeto $\Sigma$: $u, v, w, ...$
    

---

## IV. Caso Studio

$G = \langle V, \Sigma, P, S \rangle$

- $N = {\langle frase \rangle, \langle listaNomi \rangle, \langle fineLista \rangle, \langle nome \rangle}$
    
- $\Sigma = {\text{'Aldo', 'Bianca', 'Carlo', 'e', ',', ' '}}$
    
- $V = N \cup \Sigma$
    
- $P = \{$
    
    - $\langle nome \rangle \rightarrow \langle Aldo \rangle$
        
    - $\langle nome \rangle \rightarrow \langle Bianca \rangle$
        
    - $\langle nome \rangle \rightarrow \langle Carlo \rangle$
        
    - $\langle frase \rangle \rightarrow \langle nome \rangle$
        
    - $\langle frase \rangle \rightarrow \langle listaNomi \rangle \langle fineLista \rangle$
        
    - $\langle listaNomi \rangle \rightarrow \langle nome \rangle$
        
    - $\langle listaNomi \rangle \rightarrow \langle nome \rangle, \langle listaNomi \rangle$
        
    - $, \langle nome \rangle \langle fineLista \rangle \rightarrow e \langle nome \rangle$  
        $\}$
        
- $S = \langle frase \rangle$
    

> [!EXAMPLE] Frase generata  
> In questo caso, questo linguaggio formale $G$ ci consente di scrivere varie frasi diverse.  
> La frase che ci interesserà di più sarà:  
> `"Aldo, Bianca e Carlo"`