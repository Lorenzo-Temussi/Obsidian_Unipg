---
date: 2026-02-16
tags:
  - Diritto
type: lezione
---
# AI Act, Diritto d'Autore e Gestione del Rischio

📝 Contenuto della Lezione

## Opacità dell'AI e Ruolo dei Dati
Una delle caratteristiche fondamentali dei sistemi di Intelligenza Artificiale attuali è l'opacità, spesso definita come **"Blackbox"**. Nemmeno gli sviluppatori sono in grado di spiegare il *perché* di un determinato output, ma possono solo illustrare il "percorso" logico compiuto. Sostanzialmente, si tratta di una lettura statistica basata sui dati di addestramento.

I dati sono cruciali durante il training e influenzano direttamente l'output. Un sistema addestrato su dati "vecchi" o contenenti pregiudizi (*bias*) produrrà risultati alterati. Esistono dati "vecchi" che sono caduti nel pubblico dominio.

> [!INFO] Liber Liber e Pubblico Dominio
> Progetti come **Liber Liber** raccolgono e rendono disponibili libri e opere ormai in pubblico dominio, ovvero libere da diritti patrimoniali e accessibili a tutti.

## Diritto d'Autore: Fondamenti e Durata
Il pubblico dominio subentra quando il diritto d'autore decade. Il diritto d'autore è fondamentale e nasce nel momento in cui un autore crea un'opera creativa. Nel 1983 ci furono aggiornamenti normativi per includere fotografia e cinematografia, superando i dubbi iniziali sul fatto che fosse la macchina, e non l'artista, a produrre l'opera.

La discriminante è la **creatività**: una mostra o un'immagine sono protette se esprimono una visione creativa. Quando manca la creatività, come nel caso di alcune banche dati, subentra una protezione diversa (diritto *sui generis*) di durata limitata (15 anni), che tutela l'investimento piuttosto che l'originalità. Negli anni, anche il software è stato incluso tra le opere protette.

Il diritto d'autore si divide in:
1.  **Diritto Morale:** Il diritto inalienabile di essere riconosciuti come autori dell'opera (espressione della personalità dell'autore).
2.  **Diritto Patrimoniale:** Il diritto di sfruttare economicamente l'opera (es. farsi pagare per l'utilizzo).

Il diritto patrimoniale è disponibile e rinunciabile. Questo è alla base del software **Open Source** (codice aperto, modificabile, sviluppo comunitario) e delle licenze **Creative Commons**.

> [!INFO] Plagio
> Il plagio è la violazione del diritto d'autore tramite l'appropriazione, totale o parziale, di un'opera altrui spacciandola per propria. È punito penalmente. In ambito accademico (tesi), spesso si utilizzano soglie di tolleranza (es. 25%), e i controlli odierni includono anche il testo generato da IA.

### Durata e Differenze Internazionali
* **Italia/Europa:** Il pubblico dominio si ottiene **70 anni dopo la morte dell'autore**. Cessa il diritto patrimoniale (non si può più guadagnare dall'esclusiva), ma permane il diritto morale.
* **USA:** Vige il **Copyright** (diritto di copia), focalizzato più sull'aspetto economico che morale. La durata è diversa: 75 anni, estesi a 95 anni con il *Mickey Mouse Act* (opere dal 1922 al 1978).

> [!INFO] SIAE e Licenze
> In Italia, l'originalità si può depositare alla SIAE. La SIAE controlla l'utilizzo delle licenze e riscuote i diritti per conto degli autori. Tecnologie come la Blockchain possono oggi essere usate per provare l'originalità e la data certa di un contenuto.

Il marchio (es. logo Disney) è diverso dal diritto d'autore: è un titolo di proprietà industriale che copre un simbolo/prodotto nel mercato contro i falsi e, se rinnovato (pagato), non scade mai.

> [!INFO] Marchio vs Diritto d'Autore
> Il marchio tutela i segni distintivi di un'impresa (brand, logo) per evitare confusione nel consumatore e contraffazione. A differenza del diritto d'autore che ha una scadenza naturale, il marchio può essere rinnovato all'infinito.

## Bias nei Dati e Applicazioni Mediche
Tornando all'AI, l'uso di dati di addestramento pubblici o storici può introdurre pregiudizi (es. bias razziali). Anche in medicina, algoritmi addestrati su vecchi casi (es. medicina nucleare) possono identificare nuove patologie permettendo diagnosi anticipate. Tuttavia, l'AI soffre del problema dei falsi positivi/negativi, specialmente su patologie rare.

L'AI può suggerire *come* è arrivata a un risultato, ma non può spiegarne il *perché* profondo. Il verdetto finale spetta sempre all'utilizzatore umano (es. il radiologo).

> [!INFO] Bias nei dati di addestramento
> I bias sono distorsioni sistematiche nei dati usati per il training (es. sovrarappresentazione di una etnia o genere). Se i dati in ingresso sono viziati, l'algoritmo replicherà e amplificherà tali pregiudizi nelle sue decisioni (fenomeno *Garbage In, Garbage Out*).

## AI Act: Approccio basato sul Rischio
L'AI Act adotta un approccio basato sulla sicurezza del prodotto (scelta di campo: il prodotto deve essere plasmato per evitare usi nocivi). Non vieta l'AI in sé, ma classifica i sistemi in base al rischio per i diritti fondamentali.

> [!INFO] Riferimento ai Trattati UE
> La classificazione dei rischi si fonda sui valori sanciti dalla Carta dei diritti fondamentali dell'Unione europea (CARTA DI NIZZA) e dai trattati istitutivi (TUE, TFUE), discussi nella lezione precedente.

### Definizione e Formula del Rischio
L'Art. 3 num. 2 definisce il rischio come la combinazione della probabilità del verificarsi di un danno e la gravità del danno stesso.

$$R = P \times D$$

Dove $R$ è il Rischio, $P$ è la Probabilità e $D$ è il Danno.

### La Piramide del Rischio
L'AI Act struttura i sistemi in una piramide.

#### 1. Pratiche Vietate (Rischio Inaccettabile)
Sono pratiche bandite dal mercato UE (ma permesse per scopi di ricerca pura). Includono sistemi che manipolano il comportamento o sfruttano vulnerabilità (Art. 5).
Esempio: **Social Credit Score**. A differenza del *Credit Score* bancario, il Social Scoring (nato in Cina) valuta la persona nella sua interezza (comportamenti, caratteristiche fisiche), mettendo a rischio diritti e libertà.

> [!INFO] Contesto Social Scoring (Cina)
> In Cina, il sistema di credito sociale è legato a meccanismi di controllo statale pervasivi, facilitati anche da problematiche storiche di registrazione all'anagrafe e controllo demografico.

> [!INFO] Dettaglio Articolo 5 (Pratiche Vietate)
> L'Articolo 5 elenca tassativamente le pratiche proibite perché contrarie ai valori dell'Unione, come la manipolazione subliminale, lo sfruttamento di gruppi vulnerabili (bambini, disabili) e la valutazione sociale da parte delle autorità pubbliche. Queste pratiche sono vietate dal 2025.

#### 2. Sistemi ad Alto Rischio
Sono sistemi che possono avere un impatto negativo sulla sicurezza o sui diritti fondamentali (Art. 6). Sono considerati tali se integrati in prodotti di sicurezza o usati in settori sensibili (biometria, polizia, istruzione, lavoro).

Esempio: Algoritmo spagnolo (VioGén) per la violenza di genere, che suggeriva ai poliziotti il fattore di rischio di recidiva.
Esempio: Identificazione biometrica remota "live" in spazi pubblici. Oggetto di forte dibattito tra Garante Privacy EU ed Europol. È tendenzialmente vietata salvo eccezioni gravissime (terrorismo, ricerca dispersi), poiché configura una sorveglianza di massa.

> [!INFO] Pacchetto Omnibus e Tempistiche
> Esistono pressioni (es. USA) che influenzano l'entrata in vigore di alcune norme. Il riferimento al "Pacchetto Omnibus" suggerisce slittamenti o modifiche nelle date di applicazione per specifici obblighi (es. Art 6 par 2 potrebbe slittare al 2027/2028).

> [!INFO] Allegato 1
> L'Allegato 1 dell'AI Act contiene l'elenco delle normative di armonizzazione dell'UE. Se un sistema AI è un componente di sicurezza di un prodotto coperto da queste norme (es. giocattoli, ascensori, auto), è automaticamente ad alto rischio.

> [!INFO] Sorveglianza Umana (Human in the loop)
> Per i sistemi ad alto rischio è obbligatoria la sorveglianza umana. L'uomo deve poter intervenire, interpretare l'output e, se necessario, ignorare o spegnere il sistema (come nel caso dell'algoritmo di polizia).

> [!INFO] Articolo 3, comma b
> Riferimento alle definizioni aggiornate dei fornitori e dei deployer (utilizzatori) dei sistemi di IA, essenziali per stabilire le responsabilità nella catena del valore.

#### 3. AI per Finalità Generali (GPAI)
L'AI Act è stato aggiornato per includere i modelli "General Purpose" (Art. 3, def. 63). Questi modelli, addestrati su grandi quantità di dati (autosupervisione), possono svolgere un'ampia gamma di compiti e integrarsi in sistemi a valle.

Se possiedono capacità di impatto elevato, presentano un **Rischio Sistemico** (def. 65): possono causare incidenti su larga scala, influenzare la salute pubblica o propagare effetti negativi lungo la catena del valore.

> [!INFO] Soglia dei FLOPs
> Per determinare se un modello GPAI ha un "rischio sistemico", la Commissione usa criteri tecnici come la potenza di calcolo utilizzata per l'addestramento, misurata in FLOPs (Floating Point Operations). Superata una certa soglia, il rischio è presunto.

## AI e Diritto d'Autore in Italia (L.633/1941)
La normativa italiana specifica che il diritto d'autore è riservato agli esseri umani. Le opere create con l'ausilio di strumenti AI possono essere protette solo se si dimostra un apporto creativo umano significativo (il lavoro intellettuale deve essere documentato).

### Text and Data Mining (Art. 70-ter)
L'articolo recepisce la direttiva sul diritto d'autore nel mercato unico digitale. È consentita l'estrazione di testo e dati da opere legittimamente accessibili per l'addestramento dell'AI.
* **Opt-out:** I titolari dei diritti possono riservare l'uso delle loro opere (es. tramite file `robots.txt` nei siti web, come fatto dal *Corriere della Sera*).
* **Consenso:** Se non è specificato il divieto ("non espressamente riservato"), l'estrazione è consentita.

Vi sono dibattiti tecnici sulla natura dell'output: alcuni sostengono che i sistemi vettoriali frammentino i dati a tal punto da non violare il diritto d'autore nell'output; altri sostengono che se il risultato non è frutto dell'intelletto umano, non è proteggibile.

> [!INFO] Reato di Deepfake
> Il "Deepfake" non è solo una tecnologia ma può configurare reati specifici (es. sostituzione di persona, diffamazione, pornografia non consensuale). La normativa sta evolvendo per punire l'uso malevolo di manipolazioni audio/video realistiche.

---
## ⏭️ Navigazione Lezioni

- **Index Corso Diritto:** [[Diritto Privato dell'Informatica]]