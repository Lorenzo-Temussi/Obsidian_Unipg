◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]

---
# Dall'automa alla regex

Abbiamo visto un algoritmo per convertire una espressione regolare in un ASFND con $\varepsilon$-transizioni, per bilanciare dovremmo anche familiarizzare con l'algoritmo inverso, che a partire dall'automa consente di derivare una espressione regolare equivalente.

>[!tip] Premesse
>L'ASF A con cui lavoreremo sarà, per semplicità:
>- dotato di stati $q_1, q_2, ..., q_n$
>- dotato di stato iniziale $q_1$
>  
>  Inoltre definiremo gli insiemi del tipo $L_ijk$ con $0 \leq k < i, \ j \leq n$ come:
>  
>*gli insiemi che contengono le etichette dei cammini del grafo di A che iniziano in $q_i$, terminano in $q_j$, e attraversano solo gli stati di indice $\leq$k.*
>  
>  Possiamo poi immaginare, senza necessità di dimostrazione rigorosa che:
>  $$L(A)=\bigcup \limits_{q_j \in F} L_1jn. $$

Notare che la notazione che abbiamo usato ben si presta ad essere definita ricorsivamente:

$$E_{ijk} = E_{ijk-1} + (E_{ikk-1})^* (E_{kjk-1}),\ 1\leq k < i, j \leq n.$$

Gli occhi di falco avranno intuito che questa formula ci consente di determinare algoritmicamente l'intera regex associata ad un qualsiasi ASF deterministico e non.

Per comodità lavoreremo su un automa modificato per avere un solo stato finale, raggiungibile con una $\varepsilon$-transizione da tutti gli stati finali originali (ora non più finali).

Ci farà comodo imparare ad implementare questo metodo sul grafo stesso. Possiamo seguire questa procedura:

>[!example] Procedura
>1) Ogni etichetta multipla (a, b) è rimpiazzata con la rispettiva unione (a+b);
>2) preso uno stato $q_k$ non finale: $\forall$ lato del grafo che entra in $q_k\  (q_i -^{E_{ik}}\rightarrow q_k )$ e ogni lato del grafo che esce da $q_k\  (q_k -^{E_{kj}}\rightarrow q_j)$, con $i, j \neq k$:
>3) rimpiazziamo l'etichetta del lato $q_iq_j$ con $E_{ij} + E_{ik}E_{kk}^*E_{kj}$. Se il lato non esiste, la creiamo;
>4) rimuoviamo lo stato $q_k$ con tutti i lati uscenti ed entranti in esso;
>5) se ancora l'automa presenta stati non iniziale/finali, torniamo al passo 3.
>6) L'automa con due soli stati $q_i$ e $q_f$ presenta un singolo lato che ha come label la regex ricercata.
---

# La classe dei linguaggi formali è un'Algebra Booleana

Tutte i linguaggi regolari possono essere messi in relazione con le operazioni di unione, intersezione e complemento tramite espressioni regolari.

Con questo dato, posso determinare se due regex X e Y sono equivalenti verificando che:
$$(X-Y)\cup (Y-X) = \emptyset$$
e dunque, costruendo l'automa di questa regex derivata, osserverò che se le due sono in effetti equivalenti, gli stati finali saranno tutti inaccessibili.

---
◀️ _Back to:_ [[Linguaggi Formali e Compilatori]]