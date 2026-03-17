---
autore: Lorenzo Temussi
fonte: Appunti a lezione
date: 2026-03-16
---
Da [[Diritto Privato dell'Informatica]], in data 16/03/2026.

## Atto in Giudizio

>[!Info] Codice Civile Libro 6 Art 2697 
>Chi agisce in giudizio deve provare i fatti che costituiscono il fondamento del diritto che vuole vedere riconosciuto.
>

Il giudice può pronunciarsi esclusivamente sulla materia dell'atto.

>[!done] Vocabolario
>**Attore:** la parte che cita in giudizio l'altra.
>**Convenuto:** la parte citata in giudizio.
>**Petitum:** la pretesa che l'attore vuole vedere riconosciuta.
>**Causa Petendi:** le ragioni di diritto che dovrebbero provare la ragione dell'attore.
>**Atto di citazione:** atto con cui l'attore cita in giudizio il convenuto.
>**Imputato:** persona fisica che subisce un danno.
>**Danno emergente:** perdita patrimoniale.
>**Mancato Lucro:** danno patrimoniale causato in seguito ad un evento di qualche tipo. L'esempio più comune potrebbe essere un idraulico che guadagna intorno ad una certa cifra ogni mese che viene investito da una macchina e non può lavorare per un periodo di tempo, durante il quale era possibile aspettarsi che avrebbe lavorato e guadagnato allo stesso ritmo di prima.

L'attore deve provare anche il nesso di consequenzialità del caso, ovvero la logica secondo la quale le azioni compiute o mancate del convenuto, opposte alla legge, hanno cagionato il danno. 
Solitamente questo nesso deve provare una consequenzialità immediata e diretta.

---

>[!info] GDPR Art. 82
>In caso di danni cagionati dal trattamento illecito dei dati personali, l'imputato ha diritto ad un risarcimento dal titolare e/o dal responsabile del trattamento. Questi sono esonerati se possono provare che l'evento dannoso non è ad essi imputabile.
>

Il titolare del trattamento è tipicamente il proprietario del servizio che raccoglie i dati degli utenti, il responsabile è tipicamente una figura di tecnico informatico (ehi guarda sono io), che implementa le misure reali con cui vengono poi trattati i dati.

Il titolare del trattamento è il responsabile unico, a patto che il responsabile del trattamento possa dimostrare di aver seguito le indicazione del suddetto esattamente come le ha ricevute.

>[!tip] Caso Ipotetico
>L'Università commissiona un video ad una azienda, specificando quali dati sono trattabili e in quale misura (es: uno studente chiede di non figurare in video). In questo caso, l'Università è il titolare del trattamento dei dati, e l'azienda è il responsabile, nel contesto di questa commissione.



>[!warning] Caso Reale 
>Un utente PosteItaliane riceve un'e-mail di phishing composta con la cura di una miniatura certosina, clicca il link, segue le istruzioni, e un malintenzionato dirige a sé stesso un versamento da 150.000 € dal CC dell'imputato.
>
>Furioso, il correntista cita in giudizio PosteItaliane accusando di aver subito un danno emergente per colpa loro.
>
>Il caso sembra aperto e chiuso, PosteItaliane non ha nemmeno trattato i dati dell'imputato, in apparenza, ma, questi impugna le insoddisfacenti misure di protezione dei dati personali messe a disposizione da PosteItaliane (autenticazione ad 1 fattore).
>
>In risposta la Corte di Cassazione riconosce a PosteItaliane una colpa di omissione per non aver aggiornato le misure di sicurezza ad Autenticazione a due Fattori (che ai tempi era già lo standard per la protezione dei dati).

Al giorno d'oggi anche l'autenticazione a due fattori presenta delle criticità, in quanto è possibile ricevere i messaggi dovuti ad altri facendo dei magheggi con la SIM che non ho capito. 

>[!error] Non hai capito perché avevi la testa fra le nuvole

In un altro caso, una truffa era avvenuta sfruttando questa peculiarità, ma l'imputato ha perso la causa perché ha citato in giudizio la compagnia di telecomunicazioni, che non aveva la colpa in questo caso, essendo in riga con i protocolli di sicurezza, e non la banca, che aveva atteso troppo per aggiornare le proprie misure di sicurezza.

>[!info] GDPR Art. 24
>Il comportamento contrario ai codici di condotta del settore fonda responsabilità civile e diritto al risarcimento del danno.

Questo include anche i casi di omissione di aggiornamento dei sistemi di sicurezza di cui sopra.

>[!info] Sentenza della Cassazione 21.6.2018 16133
>Si riconosce un illecito nella incontinente divulgazione di contenuti di una cartella sanitaria.

Nell'ambito del trattamento dei dati personali è possibile incorrere in un illecito anche in casi:
- di mancata adozione di metodi di cifratura e controlli, in caso di accesso abusivo di terzi
- di finalità d'uso non precedentemente dichiarate
- di trattamento successivo alla revoca del consenso
- di comunicazione non autorizzata degli stessi

>[!info] GDPR Considerando 74
>Spetta al titolare dei dati personali dimostrare di aver messo in atto misure adeguate ed efficaci a proteggere i dati dell'imputato.

Nel caso in cui i dati personali a disposizione del titolare non consentano la distinzione fra due utenti, può essere scusato uno scambio di persona, MA questi dovrà giustificare la ragione per cui i profili degli utenti non avessero assegnato un identificatore univoco, tipicamente un codice-pseudonimo.

>[!info] Sentenza della Cassazione 10638/2016
>La banca può essere esonerata in casi di trascuratezza, errore o frode del correntista, o in casi di forza maggiore, ma l'onere della prova ricade su di essa.

I casi di forza maggiore sopra menzionati sono un riferimento ad attacchi imprevisti e particolarmente Day 0 Exploits, ovvero espedienti per aggirare falle informatiche scoperte molto di recente in un sistema. Il termine suggerisce che potrebbero essere state scovate il giorno stesso, e dunque è impossibile aspettarsi che il titolare del trattamento dei dati possa implementare una contromisura in tempo.

---
◀️ *Back to [[Diritto Privato dell'Informatica]].*

