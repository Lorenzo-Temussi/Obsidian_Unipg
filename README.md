# 🏛️ Appunti Informatica UNIPG

> *"Trova in pochi clic tutte le informazioni che ti servono per preparare il tuo esame e accrescere la tua conoscenza dell'informatica.*
> *Costruiamo insieme questa cattedrale al genio umano."*

---

## Come entrare nella Cattedrale (Istruzioni per l'uso)

Questa repository è strutturata per essere usata e visualizzata direttamente dentro **[Obsidian](https://obsidian.md/)**. 

Non è solo testo: accetta file `.md` (Markdown per Obsidian), `.pdf` (slide, documenti e dispense) e sorgenti `LaTeX` per le formule matematiche più pesanti. Tutto è unificato in un solo grande albero.

Per avere tutto pronto sul tuo PC in 4 semplici passi:

1. **Clona il progetto** sul tuo computer (apri il terminale nella cartella in cui vuoi salvare gli appunti):
   ```bash
   git clone [https://github.com/Lorenzo-Temussi/Obsidian_Unipg.git](https://github.com/Lorenzo-Temussi/Obsidian_Unipg)
   ```
2. **Scarica e apri [Obsidian](https://obsidian.md/)**.
3. Nella schermata iniziale di Obsidian, clicca su **"Apri cartella come vault"** (*Open folder as vault*) e seleziona la cartella che hai appena clonato.
4. **Inizia l'esplorazione!** Una volta aperto il vault, clicca sul file dell'Indice Generale [[UNIPG]] per avere la mappa completa e navigare facilmente tra i vari anni e semestri.

---

## Aggiungere i tuoi Appunti (Regole per contribuire)

Vuoi aggiungere i tuoi appunti, delle slide utili o sistemare la formattazione di una pagina? Per mantenere la cattedrale in ordine ed evitare fastidiosi conflitti su Git, usiamo un metodo semplicissimo basato su **sottocartelle personali**.

1. **Sincronizzati e crea un branch:**
   ```bash
   git pull origin main
   git checkout -b aggiunta-appunti-davide
   ```
2. **Crea la tua cartella:** Vai nella cartella del corso (`Anno_X/Corso_Sigma/`) e crea una sottocartella tutta tua, ad esempio `appunti_tuo-nome` (o `appunti_n`).
3. **Metti lì i tuoi file:** Salva tutti i tuoi file `.md`, i tuoi PDF e le tue immagini dentro la tua cartella `appunti_tuo-nome`. In questo modo sei libero di organizzarli come preferisci senza fare confusione con i file degli altri.
4. **Aggiorna l'Indice del corso:** Apri il file indice principale del corso in quesitone e aggiungi i link ai tuoi file usando la sintassi di Obsidian `[[Nome del tuo file]]`, scrivendo chiaramente che sono i tuoi appunti.
5. **Manda tutto online!** Fai commit, pusha il tuo branch e apri una Pull Request verso il `main`:
   ```bash
   git add .
   git commit -m "Aggiunti appunti di Tuo-Nome per Sistemi Operativi"
   git push origin aggiunta-appunti-Tuo-nome
   ```

*(P.S. Cerca di dare nomi chiari ai file. Ricorda di ignorare la tua cartella `.obsidian` personale e di non pushare i file spazzatura)*