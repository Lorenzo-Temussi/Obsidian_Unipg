◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---

### Automi a Pila
---

La versione più recente e pulita degli automi a carbone. Descritti da una settupla:

$$A=\langle Q, \Sigma , \Gamma , \delta , q_0 , Z_0 , F \rangle$$
in cui:
- Q è l'insieme degli stati;
- $\Sigma$ è l'alfabeto di output;
- $\Gamma$ è l'alfabeto di pila;
- $\delta : Q \times (\Sigma \cup \{ \varepsilon \}) \times \Gamma \rightarrow ℘_F(Q \times \Gamma^*)$ è la funzione di transizione;
- $q_0 \in Q$ è lo stato iniziale;
- $Z_0 \in \Gamma$ è il simbolo iniziale della pila;
- $F \subseteq Q$ è l'insieme degli stati finali.


### Bello, come funziona?
---

Inizialmente l'automa è nello stato $q_0$ e la pila contiene $Z_0$. 

Poi avviene la magia... 

Durante ogni iterazione, in cui l'automa si trova nello stato $p$, e riceva $a$ in input e $Z$$ dall'operazione $pop$ , l'automa controlla se $\delta (p,a,Z)$ contiene una coppia $(q, \gamma)$, e se sì, spinge $\gamma$ sulla pila e si porta nello stato $q$.


### Configurazioni Interne:
---

Una configurazione interna dell'automa a pila $A$ è una coppia $(q, \gamma) \in Q \times \Gamma^*$.

Comunque, ecco, se dato un input $k$, l'automa cambia configurazione interna si scrive:

$(q_1, \gamma_1)\models^k = (q_2, \gamma_2)$

una catena di transizioni fra configurazioni con input $w=a_1a_2a_3a_4...a_n$  si può riassumere con:

$(q_1, \gamma_1)\models^w = (q_n, \gamma_n)$


### Metodi di accettazione:
---

Ricordiamoci che sta roba non la facciamo per divertimento, abbiamo un obiettivo (2 in realtà, ma uno dei due è): determinare se una parola è accettata o meno da un automa/linguaggio/grammatica.

Quindi, preso il nostro automino $A$ e la nostra parolina $w \in \Sigma^*$, questa è accettata -

- *per stato finale* se si ha:
$$(q_0, Z_0)\models^w = (f, \gamma),\ \ f \in F,\ \gamma \in \Gamma^*$$
- *per pila vuota* se si ha:
$$(q_0, Z_0)\models^w = (p, \varepsilon),\ \ p \in Q$$
- *per stato finale E pila vuota* se si ha:
$$(q_0, Z_0)\models^w = (f, \varepsilon),\ \ f \in F$$
I tre sono nomenclati rispettivamente come $L_F(A)$, $L_P(A)$, $L(A)$.


### Automi a pila deterministici
---

Data una configurazione interna e una lettera in input, un AAPD porta ad una sola configurazione interna in output.

Questo automa risolve problemi di accettazione in tempo lineare.


### Convergenza di casi
---

Un linguaggio accettato per stato finale da un Automa A è accettato per stato finale e pila vuota se aggiungo un sacco di $\varepsilon$-transizioni spilative allo stato finale.

Un linguaggio accettato per pila vuota da un Automa a è accettato per stato finale e pila vuota se rendo ogni stato finale.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]