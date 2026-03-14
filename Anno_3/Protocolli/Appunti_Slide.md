# Teoria Protocolli

---

## Indice Generale

### **Primo Modulo**

- [Comunicazione Dati](#comunicazione-dati)
- [Informazione e Misura](#informazione-e-misura)
- [Flussi Trasmissivi](#flussi-trasmissivi)
- [DTE, DCE, CPE](#dte-dce-cpe)
- [Le Reti ed il Loro Mondo](#le-reti-ed-il-loro-mondo)
- [Valutazione della Rete](#valutazione-della-rete)
- [Tipo di Trasmissione](#tipo-di-trasmissione)
- [Classificazione delle Reti](#classificazione-delle-reti)
- [Reti Wireless](#reti-wireless)
- [Struttura delle Reti](#struttura-delle-reti)
- [Reti Mesh](#reti-mesh)
- [Wi-Fi vs Mesh](#wi-fi-vs-mesh)
- [I Protocolli secondo ISO-OSI](#i-protocolli-secondo-iso-osi)
- [La Trasmissione Dati](#la-trasmissione-dati)
- [Segnali Sinusoidali](#segnali-sinusoidali)
- [Sviluppo in Serie di Fourier](#sviluppo-in-serie-di-fourier)
- [Filtri](#filtri)
- [Modulazione di un Segnale](#modulazione-di-un-segnale)
- [Modulazione ad Onda Continua](#modulazione-ad-onda-continua)
- [Modulazione Impulsiva](#modulazione-impulsiva)
- [PDF_6: PCM](#pdf_6-pcm)
- [PDF_7: EVM](#pdf_7-evm)
  - [Codifica Differenziale DPSK](#codifica-differenziale-dpsk)
  - [Modulazione QAM](#modulazione-qam)
  - [Codifica Trellis](#codifica-trellis)
  - [Alterazione del Segnale](#alterazione-del-segnale)
- [Limiti della Velocità nel Trasferimento](#limiti-della-velocità-nel-trasferimento)
- [PDF_8: Altri Limiti della Velocità](#pdf_8-altri-limiti-della-velocità)
  - [Schemi di Controllo](#schemi-di-controllo)
  - [Codifica di Canale (Encoding)](#codifica-di-canale-encoding)
  - [Controllo degli Errori](#controllo-degli-errori)
- [PDF_9](#pdf_9)
  - [Multiplazione](#multiplazione)
  - [Modem](#modem)
  - [ADSL](#adsl)
  - [Interfacce](#interfacce)
- [PDF_10](#pdf_10)
  - [Interfaccia RS422](#interfaccia-rs422)
  - [Tecnologie in Fibra Ottica](#tecnologie-in-fibra-ottica)
  - [Tecnologie in Banda Larga](#tecnologie-banda-larga)
  - [PDH](#pdh-plesiochronous-digital-hierarchy)
  - [SDH](#sdh-synchronous-digital-hierarchy)
- [PDF_11](#pdf_11)
  - [SONET](#sonet-synchronous-optical-network)
  - [ISO/OSI Livello 2](#protocolli-di-livello-2-iso-osi-data-link)
    - [Protocolli Asincroni](#protocolli-asincroni-startstop)
    - [Protocolli Sincroni](#protocolli-sincroni)
    - [BSC](#bsc-binary-synchronous-communications)
    - [HDLC](#hdlc-high-level-data-link-control)

### **Secondo Modulo**

- [PDF_1](#secondo-modulo---pdf_1)
  - [IP](#indirizzamento-ip)
  - [CLASSI](#classi-di-indirizzi-ip)
  - [Indirizzi Riservati](#indirizzi-ip-riservati)
  - [Subnetting](#subnetting)
  - [Routing](#routing-e-tabella-di-routing)
- [PDF_2](#secondo-modulo---pdf_2)
  - [ARP](#arp-address-resolution-protocol)
  - [RARP](#rarp-reverse-arp)
  - [Numeri di protocollo](#numeri-di-protocollo)
  - [Numeri di porta](#numeri-di-porta)
  - [Frame di rete](#struttura-frame-di-rete)
- [PDF_3](#secondo-modulo---pdf_3)
  - [Name Service](#name-service-servizi-di-risoluzione-nomi)
  - [DNS](#dns-domain-name-system)
  - [Configurazione TCP/IP](#configurazione-tcpip)
  - [Configurazione Routing](#configurazione-del-routing)
  - [Definizione Sottoreti](#definizione-delle-sottoreti)
- [PDF_4](#secondo-modulo---pdf_4)
  - [Internet Daemon](#internet-daemon-inetd)
  - [TCP/IP](#architettura-di-rete-tcpip)
  - [Dispositivi OSI](#dispositivi-di-rete-e-livelli-osi)
  - [Protocolli](#protocolli-di-supporto)
  - [Autonomous System](#autonomous-system-as)
  - [Configurazione Delle Interfacce di rete](#configurazione-delle-interfacce-di-rete)
- [PDF_5](#secondo-modulo---pdf_5)
  - [Comandi Avanzati ifconfig](#comandi-avanzati-di-ifconfig)
  - [Configurazione avanzata del Routing](#configurazione-avanzata-del-routing)
  - [Protocolli di Routing](#protocolli-di-routing)
- [PDF_6](#secondo-modulo---pdf_6)
   - [Gateway Routing Daemon](#gateway-routing-daemon-gated---approfondimento)
   - [Gated Configurazione](#configurazione-di-gated)
- [PDF_PARTE_FINALE](#secondo-modulo---pdf_parte_finale)
   - [DNS: BIND](#dns-bind-berkeley-internet-name-domain)
   - [Configurazione di BIND](#configurazione-di-bind)
   - [Configurazione del Resolver](#configurazione-del-resolver-1)
   - [Configurazione di Named](#configurazione-del-server-named)
   - [Configurazione Name Sarver Caching-Only](#configurazione-name-server-caching-only)
   - [Standard Resource Records](#standard-resource-records-rr)
   - [Record Start of Authority (SOA)](#record-start-of-authority-soa)
   - [Configurazione Authoritative Name Server](#configurazione-authoritative-name-server)
   - [Map Files (Zone Files)](#map-files-zone-files)
   - [File di Reverse Domain (Reverse DNS)](#file-di-reverse-domain-reverse-dns)
   - [Servizi di rete UNIX](#servizi-di-rete-unix)
   - [Riepilogo dei File di Configurazione](#riepilogo-dei-file-di-configurazione)

---

## Primo Modulo

### Comunicazione Dati

Per parlare di processo comunicativo, si parla di:

- **Sorgente di informazione**
- **Cammino fisico**
- **Destinatario**

L'**informazione** è l'insieme di dati correlati tra loro. Un esempio è la piramide DIKW.

Il **protocollo** è l'insieme di regole che consentono la comunicazione e definisce **COSA** e **COME**.

Questi protocolli sono definiti da standard stabiliti da organizzazioni come **ISO**, **IEEE**, **ICANN**, **W3C** e senza questi definiti due dispositivi non possono comunicare.

Il **modello TCP/IP ISO** ha 4 layer:

- Network Access
- Internet
- Transport
- Application

---

### Informazione e Misura

L'informazione ha come misura il **bit** e vale:

**Q = log₂M**

dove M è il numero di stati possibili di un sistema e Q i bit necessari per distinguerli.

Un sistema elaborativo deve avere dei **codici** per associare le sequenze di bit ad un carattere come **BCS**, **AIKEN**, **ASCII**, **UNICODE**, ecc.

I più usati sono l'**ASCII** a 7/8 bit, l'**EBCDIC** a 8 bit, l'**UNICODE**.

---

### Flussi Trasmissivi

- **Simplex** → unidirezionale
- **Half duplex** → bidirezionale a turni
- **Full duplex** → bidirezionale diretto

---

### DTE, DCE, CPE

L'applicazione utente risiede nel **Data Terminal Equipment (DTE)** come ad esempio un PC.

Il **Data Circuit Terminating Equipment (DCE)** converte i segnali nella forma migliore per l'invio sul canale.

Il **CPE (Customer Premises Equipment)** si usa in caso sia richiesto un dispositivo di pertinenza dell'utente.

---

### Le Reti ed il Loro Mondo

La **rete** è un insieme di dispositivi connessi. Vi sono uno o più nodi capaci di inviare o ricevere dati.

**Reti ad elaborazione:**

- **Concentrata** → un DTE potente viene messo a disposizione di altri DTE che ne sfruttano la capacità di calcolo
- **Distribuita** → DTE diviso in più punti

Per entrambi i modelli vi sono 3 procedure di colloquio:

- **Inquiry** → forma di interrogazione messa a disposizione da servizi del PC
- **Conversational** → stabilisce delle regole e formati, bloccando quelli diversi
- **Interattivo** → risponde ad applicazioni sensibili. Invia tutte le applicazioni che consentono pieno sfruttamento delle risorse elaborative

---

### Valutazione della Rete

- **Affidabilità** → priva di errori, rimedia ai guasti, gestisce bene le situazioni critiche
- **Sicurezza** → protezione dei dati da accesso, perdite e modifiche indesiderate
- **Prestazioni** →

  - **Ritardo** → misurazione tempo di transito dei dati
  - **Tempo risposta** → tempo tra richiesta e risposta
  - **Throughput** → quantità di dati spediti in unità di tempo

  Queste dipendono da numero di DTE, tipologia dei mezzi e dal software.

  - **Banda** → banda passante di frequenze che può essere usata per la trasmissione dei dati. Massima velocità alla quale è possibile trasmettere informazioni. Per valutare la velocità di banda si usano strumenti come **ping**, **traceroute**, **speedtest**, **pingtest** e **netindex**

---

### Tipo di Trasmissione

- **Point-to-Point** → tra due DTE diretti mediante linea telefonica o dedicata
- **Multi-point** → collegamento condiviso tra più DTE. La condivisione avviene in maniera temporale o condivisione dello spazio del canale

---

### Classificazione delle Reti

- **WAN** → grandi senza limitazione, DTE distanti, arriva fino a Tbits. Sono distribuite, quindi anche se un nodo cade, il routing instrada verso un'altra path.
- **LAN** → 1 o 2 km, uso privato, arriva fino a migliaia Gbits. Possono esserci alcuni DTE che fungono da server.
- **WLAN** → reti locali LAN ma senza fili. Usa lo spettro radio. La velocità dipende dallo standard usato:
  - WiFi 5 (802.11ac) → 3.5 Gbps
  - WiFi 6 (802.11ax) → 9.6 Gbps
  - 2.4 GHz → offre una copertura ampia ma poco potente
  - 5 GHz → copertura meno ampia ma più potente
- **MAN** → livello cittadino, fibra ottica ad alta velocità

> **Docker:** Per sicurezza tutti i software in genere girano come demoni separati all'interno dei software server

---

### Reti Wireless

Usate principalmente per la comunicazione mobile. Abbiamo:

- **WLAN** (802.11)
- **WiMax** (IEEE 802.16x)
- **IEEE 802.20**
- **CDPD** (Cellular Digital Packet Data)

---

### Struttura delle Reti

La **topologia** di una rete è la configurazione geometrica dei collegamenti fra i vari componenti. Sono volte a creare stabilità, a migliorare il rendimento e a diminuire i costi.

- **Rete ad albero** → stazioni a livelli, con un livello centrale. Semplice ma vulnerabile
- **Rete a dorsale** → collegamento multi punto via Ethernet. Questa crea una specie di spina dorsale lungo tutta la rete. Questa rete richiedeva anche una speciale terminazione montata a fine del cavo.
- **Rete a stella** → ogni nodo è connesso ad un dispositivo centrale. È più economica rispetto ad una struttura a maglia completa. Ad esempio un Ethernet con topologia a stella aveva un doppino UTP non schermato, quindi in plastica.
- **Rete ad anello** → molto usata in passato. Ogni nodo ha un punto-a-punto con solo 2 nodi. Ha una trasmissione unidirezionale, ogni nodo rigenera il segnale. Non supporta errori
- **Rete a maglia (MESH)** → tutti i nodi sono collegati tra loro. Il costo totale del percorso è **N(N-1)/2**. Ogni apparato ha un collegamento Duplex.

---

### Reti Mesh

Combinazione di nodi fissi e mobili interconnessi tra loro con link wireless per avere una rete auto-configurante multi-hop.

Offre una grande affidabilità, ha una gestione dinamica dei malfunzionamenti, sia per quanto riguarda il collegamento radio che per quanto riguarda la componente hardware della rete.

Vengono monitorati in tempo reale i percorsi disponibili e selezionati quelli migliori.

Sono soggette ad un alto tasso di errore visto l'utilizzo di onde radio, dunque serve sviluppare protocolli ottimizzati per il wireless.

La maglia usata tra gli access point forma il **wireless backhaul multi-hop**, un sistema di comunicazione che fornisce ad ogni utente servizi a basso costo multi-hop a banda larga.

- **Backhaul network** = rete comprendente nodi intermedi tra dorsale e nodi periferici

La rete Mesh risolve le seguenti esigenze:

- Trasmissione in movimento e simmetrica (uplink-downlink)
- Limiti di banda delle strutture ad albero
- Reti ad-hoc senza infrastruttura
- Configurazione automatica
- Radiolocalizzazione senza GPS
- Resistenza alle interferenze
- 100% degli IP utilizzabili
- Più sicurezza

---

### Wi-Fi vs Mesh

Nelle reti WiFi un guasto blocca tutta la rete mentre nelle reti Mesh si ha maggiore tolleranza ai guasti e flessibilità nella pianificazione.

---

### I Protocolli secondo ISO-OSI

Il compito dei protocolli, ovvero chi gestisce il colloquio tra due DTE o DCE è:

- Gestire il flusso dei dati e gli scambi
- Controllo degli errori
- Sincronizzazione
- Strutturare i dati trasmessi

I protocolli per le relazioni tra due DTE si possono dividere in:

#### **Ambito Primario/Secondario:**

- **Polling/Selecting**
- **BSC**
- **HDLC**
- **SNRM**
- **RTS/CTS** → si basa su interfaccia seriale RS-232. Una stazione che vuole trasmettere manda un segnale alla stazione master attivando il segnale Request To Send. Se il master può ricevere risponde con un segnale Clear To Send. Questa procedura si basa sull'handshake.
- **XON/XOFF** → usato per terminali vicini tra loro. La stazione primaria invia dati, vengono memorizzati e utilizzati. Quando la memoria si riempie viene mandato un carattere XOFF che impedisce l'invio di nuovi blocchi. Appena il DTE si libera manda un messaggio XON
- **Stop and Wait**
- **ARQ** → Automatic Repeat Request o Query. Protocollo Full Duplex che usa il concetto di finestra mobile per essere più efficiente.

#### **Ambito relazioni ibride:**

- **HDLC**
- **PPP**
- **MPLS**

#### **Ambito peer to peer:**

- **TDM**
- **FDM**
- **SDH**

---

### La Trasmissione Dati

Lo strato fisico deve trasportare dati. Questi sono:

- **Digitali** → rappresentazione discreta
- **Analogici** → segnale intenso, continuo

Nei DTE si usa una rappresentazione digitale trascrivendo ogni dato in sequenze di 0 o 1.

I dati vengono sottoposti a:

- Conversione in un differente tipo di segnale digitale, con livello 0 o 1
- Conversione in analogico (modulazione), quindi un segnale con diversi livelli di intensità

---

### Segnali Sinusoidali

È un segnale che varia nel tempo secondo la legge:

**U = U sin(ωt + Φ)**

dove:

- **t** è il tempo trascorso
- **ω** velocità angolare
- **Φ** lo sfasamento di fase

La curva descritta prende il nome di **sinusoide**.

![Segnali Sinusoidali](images/segnali_sinusoidali.png)

Questa curva rappresenta il valore del seno dell'angolo istante per istante che ruota in senso antiorario con velocità **ω**. Quindi **Φ** rappresenta l'angolo che viene formato con l'asse x all'istante 0.

Ruotando tornerà alla posizione di partenza e si ripeterà. Il numero di volte al secondo che il segnale torna allo stato di partenza si chiama **FREQUENZA** e viene calcolata in **Hertz = 1/t**.

Un segnale che ha una frequenza di **1 KHz** vuol dire che percorrerà la circonferenza 1000 volte al secondo. La velocità è data dunque da **2πf**. Il periodo che sta nel mezzo della ripetizione del segnale si chiama periodo.

**ω = 2πf**

Dunque un'onda portante sinusoidale ha forma del tipo:

**s(t) = A cos(2πft + Φ) = A sin(ωt + Φ + π/2)**

con:

- **A** ampiezza della portante
- **f** frequenza
- **Φ** fase

Un **periodo** è dato dall'unità di tempo diviso la frequenza → **T = 1/f**.

Dunque un segnale con **1 KHz** di frequenza ha periodo di **1/1000 = 1 millisecondo**.

La **lunghezza d'onda λ** mette in relazione frequenza e velocità di trasmissione:

**λ = C/f** dove **C = 300.000 km/sec**

Lo **spettro** è l'insieme di frequenze che il segnale contiene.

La **larghezza di banda** è l'intervallo delle frequenze contenute in un segnale composto. Se un segnale ad esempio trasmette da 300 Hz a 3400 Hz la sua larghezza sarà 3100 Hz.

---

### Sviluppo in Serie di Fourier

Il teorema di Fourier ci dice che un segnale periodico può essere considerato come la somma di infinite sinusoidi diverse.

Matematicamente:

**S(t) = A₀ + A₁ sin(ωt + φ₁) + A₂ sin(2ωt + φ₂) + A₃ sin(3ωt + φ₃) + ...**

![Fourier Terza Armonica](images/fourier_terza.png)

![Fourier Nona Armonica](images/fourier_nona.png)

Utilizzando sempre più segnali sinusoidali diversi e opportuni, il segnale ricostruito in giallo è sempre più tendente ad una forma quadrata. Questo si ha passando da un'analisi dalla 3ª alla 9ª armonica. Il numero di armoniche usate per la ricostruzione di un segnale varia in base alla potenza del segnale da rappresentare. In genere si considera l'armonica sino a che la sua ampiezza non sia **1/10** della grandezza originale.

L'analisi di Fourier ci ricorda che un segnale digitale è un segnale analogico composto da banda teoricamente infinita. Nasce il problema di come trasmettere il segnale analogico come digitale tra 2 punti.

---

### Filtri

Sistema che tratta in modo specifico le componenti di un segnale a frequenze diverse. Aiuta a separare le informazioni o eliminare il disturbo.

I **filtri attivi** usano amplificatori operazionali o transistori, quelli **passivi** usano componenti come resistori o condensatori.

#### **Filtro Passa Basso**

Permette il passaggio di frequenze sotto una certa soglia, chiamata frequenza di taglio. In questa sussiste la relazione:

**Vout / Vin = 1/√2**

dove **Vout** è il segnale in uscita e **Vin** quello in entrata. Così è attenuato circa di un 30%.

#### **Filtro Passa Alto**

Permette il passaggio di frequenze al di sopra della frequenza di taglio.

#### **Filtro Passa Banda**

Permette il passaggio di frequenze all'interno di un certo range detto _banda passante_ e attenua quelle fuori da questo range.

#### **Filtro Elimina Banda o Filtro Notch**

Blocca un certo intervallo di frequenze **ωL - ωH**.

---

### Modulazione di un Segnale

Il DTE sorgente immette nel canale un segnale digitale con distribuzione di energia troppo ampia per poter stare dentro un canale telefonico, deve quindi essere convertita.

La **modulazione** è un'operazione secondo la quale un segnale **portante** viene modificato in un parametro essenziale in accordo al segnale informativo d'ingresso, **modulante**.

---

### Modulazione ad Onda Continua

Ha 3 tipi di modulazione analogica:

#### **AM (Amplitude) - Modulazione di Ampiezza**

Sistema per il quale si modula l'ampiezza del segnale che si deve trasmettere **portante** in maniera proporzionale al segnale che si intende trasmettere, **modulante**.

Così il segnale modulato ha la stessa frequenza del segnale portante.

In digitale lo 0 è bassa potenza e l'1 alta potenza.

Trasmettendo un segnale modulante del tipo **vm(t) = vm cos(ωmt + Φ)** ponendo **Φ = 0**.

Sia la portante **vp(t) = vp cos(ωpt)** con frequenza maggiore, il segnale modulato in ampiezza diventa:

**v(t) = [Vp + KaVm cos(ωmt)] cos(ωpt)**

![Modulazioni](images/modulazioni.png)

#### **FM (Frequency) - Modulazione di Frequenza**

Nella AM il rumore che cade nella banda del segnale si somma, degradando così il contenuto informativo. Nella modulazione di frequenza l'ampiezza resta standard, ma cambia la frequenza del segnale. Più l'onda modulante aumenta più l'onda si infittisce. Ha un'efficienza maggiore e risente meno dei disturbi, ma è più complessa da costruire.

La pulsazione della portante varia di frequenza, proporzionalmente al valore della modulante, lasciando l'ampiezza **Vp** inalterata.

**vm(t) = VM sin ωmt**

**vp(t) = Vp sin(ωpt + mf sin ωmt)**

con **mf = (Kf VM)/ωm = (Kf VM)/2πfm = Δf/fm**

#### **PM (Phase) - Modulazione di Fase**

Simile alla modulazione di frequenza, ma la frequenza del segnale portante è più stabile. Viene spesso usato per amplificare il segnale di sistemi di frequenza.

Si fa variare la fase della portante in modo direttamente proporzionale all'ampiezza modulante.

**VPM(t) = VP cos(ωPt + Kp Vm sin ωmt)**

---

### Tabella Riassuntiva AM-FM-PM

| Caratteristica          | AM              | FM        | PM                                |
| ----------------------- | --------------- | --------- | --------------------------------- |
| Parametro modificato    | Ampiezza        | Frequenza | Fase                              |
| Robustezza al rumore    | Bassa           | Alta      | Alta                              |
| Complessità             | Bassa           | Alta      | Alta                              |
| Impiego tipico          | Radio analogica | Radio FM  | Comunicazioni digitali (PSK, QAM) |
| Ampiezza della portante | Variabile       | Costante  | Costante                          |

---

### Modulazione Impulsiva

È un tipo di modulazione dove l'informazione è codificata in una serie di impulsi.

#### **PAM (Pulse Amplitude Modulation)**

Il segnale analogico varia l'ampiezza del treno di impulsi che costituisce la portante.

![PAM](images/pam.png)

#### **PWM (Pulse Width Modulation)**

L'informazione è codificata sotto forma di durata temporale degli impulsi di un segnale. Il modulante varia la larghezza degli impulsi.

![PWM](images/pwm.png)

#### **PPM (Pulse Position Modulation)**

Le ampiezze degli impulsi sono identiche, ma la loro posizione viene modificata in base al segnale della modulante. Più il segnale è positivo più viene ritardata la posizione degli impulsi rispetto a quella di riposo e viceversa.

![PPM](images/ppm.png)

#### **PCM (Pulse Code Modulation)**

Si applica a canali telefonici e permette di fare passare su un solo cavo coassiale fino a 30 telefonate.

---

## PDF_6: PCM

### PCM (Pulse Code Modulation)

Per la sua realizzazione si effettuano 3 operazioni a partire dal microfono di ingresso:

#### **Campionamento**

**Teorema di Shannon:** un segnale a banda limitata compreso tra due frequenze **f₁** e **f₂** | **f₂ > f₁** può essere rappresentato mediante una successione di campioni prelevati con frequenza pari a **2f₂**.

Si assume come frequenza di campionamento il valore **fc = 8 KHz** superiore di **1,2 KHz** al valore minimo di **2f₂ = 6,8 KHz**.

Il periodo sarà dunque **T = 1/fc = 1/8000 = 125 μsec**

Si definisce **frequenza di Nyquist** la minima frequenza necessaria per campionare senza perdere informazione. La minima frequenza è pari al doppio della banda.

Il segnale viene quindi prima campionato poi sostituito dalla frequenza PAM.

#### **Quantizzazione**

Il dato per essere trasmesso deve assumere solo determinati valori discreti e finiti.

Si definisce prima un massimo e un minimo e si divide l'intervallo creato.

Nella **quantizzazione uniforme** ogni sotto-intervallo è uguale ad ogni altro sotto-intervallo.

Dato **n** il numero di bit usati:

- Il numero di livelli sarà **M = 2ⁿ**
- L'ampiezza **q = Vpp/M**
- La varianza **q²/12**

Essendo la quantizzazione irreversibile, occorre tener conto dell'**errore di quantizzazione**, nato dal fatto che il segnale vocale può avere infiniti valori mentre la sua discretizzazione no.

È provato che usando **256 livelli** l'orecchio umano non percepisce differenza.

#### **Codifica**

L'ampiezza degli impulsi viene trasformata in bit.

Ad esempio se l'ampiezza iniziale del primo impulso è di 5V, sarà rappresentata dalla sequenza binaria **101**.

**Esempio:** vengono spediti 96 impulsi. Il n.0, n.32 e n.64 saranno da vedersi consequenziali come il 5, 37, 69. Di questi 32 impulsi il n.0 serve per dettare il sincronismo, il 16 per il controllo della bontà di trasmissione.

In totale di 30 canali vocali, 2 sono di servizio.

Vengono trasmessi 32 canali con 8000 campioni al secondo. Ogni canale contiene 8 bit, quindi al secondo vengono trasmessi:

**Vbit = 32 × 8000 × 8 = 2048 Mbit/s**

Si possono raggruppare più canali.

---

### Modulazioni Digitali

Tecniche che modulano segnali digitali, ossia 0 e 1 o -1 e +1.

#### **Modulazione per Modem di Banda Base**

Per il collegamento tra 2 DTE si parla di codifica volta ad eliminare segnali di bassa frequenza e segnali in componente continua.

Il digitale rimane lo stesso, ma vengono fatte delle modifiche alla portante rispetto al modulante.

#### **ASK (Amplitude Shift Keying)**

La modulazione a spostamento d'ampiezza trasmette i bit modificando l'ampiezza della portante.

**s(t) = { A cos(2πft) se bit=1, 0 se bit=0 }**

Semplice ma sensibile al rumore.

#### **FSK (Frequency Shift Keying)**

Modulazione per spostamento di frequenza. I bit vengono trasmessi variando la frequenza della portante mantenendo ampiezza e fase costanti.

Più robusta di ASK ma richiede banda maggiore.

#### **PSK (Phase Shift Keying)**

Si trasmettono i bit modificando la fase portante, mantenendo ampiezza e frequenza costanti. Molto robusta ma può causare discontinuità.

#### **BPSK (BiPolar Phase Shift Keying)**

La portante mantiene valori costanti per ampiezza e frequenza, ma per garantire massima protezione da rumore, vengono usati due valori opposti di fase in base al valore del bit: **0°** e **180°** per rispettivamente bit 1 e bit 0.

Quindi, l'onda "invertirà" il segnale quando vi sarà un valore 0, mentre per valore 1 rimane uguale.

#### **4-PSK**

Modulazione digitale a 4 fasi. I bit vengono riuniti in coppie usate per modulare in fase la portante sinusoidale (dibit).

![4-PSK](images/4psk.png)

I due bit generano due flussi separati meno veloci di quello originale.

Le due portanti hanno stessa frequenza, ma le loro fasi differiscono di 90°.

La fase del segnale in uscita dal primo modulatore può assumere valori **0°** e **180°**, il secondo **90°** e **270°**.

Infine vengono sommate generando un segnale che può assumere 4 fasi diverse: **45°, 135°, 225°, 315°**.

Il circuito sfasatore sfasa il segnale portante di 90°.

Al blocco di separazione è applicato in ingresso il segnale modulante **Vi** che viene separato in bit pari (P) portati al moltiplicatore 1 e dispari (D) portati al moltiplicatore 2.

Inoltre il separatore associa allo stato logico basso +1, mentre a quello alto -1, così da avere un segnale in fase (livello basso) o sfasato di 180° (livello alto) all'uscita del moltiplicatore.

![Schema 4-PSK](images/4psk_schema.png)

---

### Diagrammi a Costellazione

Rappresentazione teorica del segnale, usata per la comprensione del suo stato.

Il segnale trasmesso in digitale è diviso in 2 segnali modulati in quadratura che non interferiscono denominati **I** e **Q** (In-fase e Quadratura).

Si crea un diagramma su piano con I e Q come assi e in base allo schema di modulazione i punti nel diagramma saranno più o meno fitti.

Il problema è che a causa di interferenze, il vettore del segnale modulato non si trova in uno dei punti previsti, ma leggermente più o meno spostato a seconda dei disturbi.

---

### Vettore Errore

Differenza tra il punto teorico e il punto reale.

Può essere descritto caratterizzato dal suo modulo e dalla sua fase.

![Vettore Errore](images/vettore_errore.png)

I vettori errore descrivono quanto "balla" il segnale ricevuto nei dintorni del punto teorico.

Misurandone tanti e tenendo in considerazione il valore quadratico medio del modulo, si ricava un parametro che descrive la qualità intrinseca della modulazione.

---

## PDF_7: EVM

### EVM (Error Vector Magnitude)

Questo parametro esprime il valore % dell'errore rispetto al segnale.

Può essere calcolato anche come rapporto espresso in dB tra valore quadratico medio della potenza del vettore e il valore quadratico medio della potenza del segnale ideale di riferimento.

**Più grande EVM peggiore la qualità.**

Essendo valori piccoli il rapporto espresso in dB assume valori estremamente piccoli. Tanto più negativi quanto migliore il segnale.

1. [Decibel e EVM](#decibel-e-evm)
2. [Modulazioni Digitali](#modulazioni-digitali)
   - [Codifica Differenziale DPSK](#codifica-differenziale-dpsk)
   - [Modulazione QAM](#modulazione-qam)
   - [Codifica Trellis](#codifica-trellis)
3. [Alterazioni del Segnale](#alterazioni-del-segnale)
4. [Limiti della Velocità](#limiti-della-velocità)
5. [Codifica di Canale](#codifica-di-canale)
6. [Controllo degli Errori](#controllo-degli-errori)
7. [Multiplazione](#multiplazione)
8. [Modem](#modem)
9. [Interfacce](#interfacce)

## Decibel e EVM

### Definizione di Bel e Decibel

Il **Bel** è definito come logaritmo del rapporto tra una grandezza X e il suo valore di riferimento X₀.

**1 Decibel** = 1/10 di Bel

Formula generale: **dBₓ = 10 log(X/X₀)**

**Scala logaritmica:**

- x = 0 ⇒ logaritmo = -∞
- x = 1 ⇒ logaritmo = 0
- x = valore della base ⇒ logaritmo = 1

⚠️ **Importante:** Valori sempre più negativi di EVM indicano prestazioni migliori.

### Misurazione dell'EVM

**Strumenti utilizzati:**

- Analizzatore di segnali
- Analizzatore di modulazione
- Analizzatore vettoriale
- Versione software (su analizzatori di spettro, digitalizzatori, oscilloscopi)

**Processo di misurazione:**

1. Il segnale viene demodulato
2. Dai dati demodulati si ricostruisce il segnale ideale
3. Per differenza si ottiene il segnale errore
4. L'elaborazione del segnale errore porta all'EVM

**Formati di output:**

- Forma sintetica tabellare
- Percentuale
- dB
- Grafico dell'evoluzione nel dominio del tempo
- Analisi della fase del vettore o solo del modulo

---

## Modulazioni Digitali

### Codifica Differenziale DPSK

Per evitare complicazioni si usa una **modulazione differenziale (DPSK)**.

**Caratteristiche:**

- Ai due livelli binari corrisponde:
  - Nessuna variazione, oppure
  - Variazione di 180°
- La prima cifra si individua inviando una sequenza prestabilita a inizio comunicazione
- Ha lo stesso andamento di un PSK (stesse caratteristiche spettrali)

**Codifica avanzata:**

```
01 = 90°
10 = 180°
11 = -90° (o 270°)
```

### Modulazione QAM

**QAM (Quadrature Amplitude Modulation)** = Combinazione di ASK e PSK

Chiamata anche **modulazione di ampiezza in quadratura**.

Si ottiene modulando in ampiezza due portanti della stessa frequenza sommate in quadratura (sfasate di 90°).

✓ **Utile per trasmissioni veloci**

#### Modulazione 16-QAM

**Funzionamento:**

- Dati divisi in gruppi da 4 bit (quadribit)
- La fase della portante varia secondo la regola 8-DPSK in base agli ultimi 3 bit
- Il primo bit opera una modulazione di ampiezza sul segnale già modulato in fase
- Risultato: 2³ = 8 salti di fase, ciascuno con un'ampiezza corrispondente al primo bit (0 o 1)

#### Modulazione 64-QAM

Modulazione **bidimensionale** ottenuta dalla combinazione di due PAM modulate con portanti seno e coseno.

### Codifica Trellis

**Codifica "con memoria"**

Rappresentata da una macchina con due stati associati a:

- **S0** → valore -A
- **S1** → valore +A

(supponendo un segnale PAM dove i simboli sono rappresentati da livelli di ampiezza)

**Regole:**

- Bit **0**: non fa cambiare stato
- Bit **1**: cambia lo stato

---

## Alterazioni del Segnale

Tutti i processi di modifica che differenziano il segnale da quello originale.

### 1. Attenuazione

**Definizione:** Perdita di energia del segnale.

**Soluzione:** Uso di amplificatori.

**Misura in decibel:**

Con **P₁ = potenza di output** e **P₂ = potenza di input**:

```
dB = 10 log₂(P₂/P₁)
```

Con **V₁ = tensione iniziale** e **V₂ = tensione finale**:

```
dB = 20 log₁₀(V₂/V₁)
```

**Valori di riferimento:**

- Fino a 20 dB: ✓ Perfetto
- Da 60 dB in su: ✗ Critico

### 2. Distorsione

**Definizione:** Cambiamento della forma del segnale, tipicamente in un segnale costituito da varie frequenze.

**Causa:** Possibili ritardi tra i vari segnali che creano differenze tra forma del segnale inviato e quello ricevuto.

### 3. Rumore

**Definizione:** Insieme di segnali indesiderati che si sovrappongono a quello utile.

**Causa principale:** Rumore termico causato dai componenti del sistema.

**SNR (Signal-to-Noise Ratio):**

```
SNR = P_segnale / P_rumore
```

**Valori di riferimento:**

- 28 dB: ✓ Ottimo
- 7-10 dB: ✗ Critico

### 4. Interferenza

**Definizione:** Sovrapposizione di informazioni non desiderate. Contaminazione da parte di segnali esterni.

### 5. Interferenza Intersimbolica

**Causa:** Limitazioni della banda che provocano un arrotondamento dei segnali emessi da un DTE.

---

## Limiti della Velocità

Velocità calcolata in **bit/sec** su canali telefonici:

**Tipi di canali:**

- **Canali perfetti:** senza distorsioni o ritardi
- **Canali ideali:** solo ritardo costante
- **Canali reali:** attenuazioni e ritardi in funzione della frequenza

### Teorema di Nyquist

**Formula (canale senza rumore):**

```
MaxDataRate = 2B × log₂(V)
```

- **B** = larghezza di banda
- **V** = numero di livelli di tensione differenti nel segnale

### Teorema di Shannon

**Formula (tenendo conto del rumore):**

```
MaxDataRate = C = B × log₂(1 + S/N)
```

- **B** = larghezza di banda
- **S** = potenza del segnale
- **N** = potenza del rumore

**Utilizzo:**

1. Con la prima formula si ricava il numero opportuno di livelli V
2. Con la seconda si ottiene il Max Data Rate reale

---

## Altri Limiti della Velocità

### Throughput

Quanto velocemente si possono spedire dati attraverso una rete **reale** (la velocità trasmissiva considera quella teorica).

### Latenza

Tempo necessario ad un messaggio per arrivare a destinazione.

**Componenti:**

- Tempo di propagazione
- Tempo di trasmissione
- Tempo di inoltro
- Tempo di attesa

### Jitter

Esprime la **variabilità del ritardo** con cui i pacchetti vengono consegnati.

### Velocità di Modulazione e Trasmissione

**Velocità di modulazione:** numero di simboli trasmessi al secondo, espressa in **baud** (simboli/sec).

⚠️ **Nota:** Un simbolo può rappresentare più bit.

**Relazione:**

```
Velocità_modulazione = Velocità_trasmissione / log₂(n)
```

---

## Codifica di Canale (Encoding)

Tecniche di codifica usate per la sincronizzazione.

### NRZ (Not Return to Zero)

**Caratteristiche:**

- Stato digitale **1** → segnale alto
- Stato digitale **0** → segnale basso
- ✓ Facile, non richiede circuiti complicati
- Dati passati direttamente in uscita
- ✗ Lunghe stringhe potrebbero causare perdita di sincronismo

### RZ (Return to Zero)

**Caratteristiche:**

- Stessa rappresentazione degli stati digitali
- A metà dell'impulso torna sempre a 0
- Clock a frequenza doppia (riduce al 50% la durata dell'impulso)
- Il ricevitore distingue tra 3 livelli
- ✓ Lunghe stringhe non causano perdita di sincronismo
- ✗ Maggior rischio di errore

### Manchester

**Caratteristiche:**

- Divide in 2 parti uguali il periodo di cifratura
- **0 logico** → transizione dal basso verso l'alto a metà bit
- **1 logico** → transizione dall'alto verso il basso a metà bit
- ✗ Raddoppia la banda necessaria
- ✓ Usata nelle LAN
- Richiede circuito complicato

### AMI (Alternate Mark Inversion)

**Caratteristiche:**

- Codice a tre livelli: **+V, 0, -V**
- Ottenuto dal codice RZ lasciando inalterato lo zero
- Stato logico **1** alternato tra +V e -V
- ✓ Usato in PCM

### Scrambling

**Scopo:** Superare i problemi di trasmissione su lunga distanza.

**Funzionamento:**

- Cambiano le regole di codifica per mescolare i bit
- Uso di registro a ciclo
- Usato nella codifica **2B1Q** (2 Binary 1 Quaternary)
- Flusso di bit organizzato in gruppi di 2 bit
- Ogni gruppo codificato in uno di 4 possibili livelli
- ✓ Mantiene costante il segnale

---

## Trasmissione dei Dati

### Trasmissione Orientata al Carattere

**Utilizzo:** Principalmente per contenuti testuali

**Caratteristiche:**

- In assenza di start e stop bit: sequenza di caratteri **SYN** per avviare il sincronismo
- **DLE (Data Link Escape):** carattere di controllo per byte stuffing
- **Byte stuffing:** aggiunta di uno 0 ogni cinque 1 consecutivi

### Trasmissione Orientata al Bit

**Caratteristiche:**

- Dati non organizzati in caratteri
- ✓ Riduce l'inefficienza legata ai caratteri di controllo
- ✓ Evita dipendenza dai caratteri
- Usa **idle bytes** o **flag bytes** per indicare inizio/fine trama (non SYN o STX)

---

## Controllo degli Errori

### Tipi di Errore

1. **Errori single bit:** invertono un solo bit (comune)
2. **Errori multiple bit:** invertono più bit non consecutivi
3. **Error burst:** invertono due o più bit consecutivi (molto raro)

### Rilevamento degli Errori

**Tecnica:** Ridondanza

I bit supplementari aggiunti sono **bit ridondanti**, eliminati quando il ricevitore conferma la trasmissione corretta.

#### 1. VRC (Controllo Ridondanza Verticale)

**Funzionamento:**

- Aggiunta di un singolo bit all'unità
- Numero di bit = 1 diventa pari o dispari
- **Parity check:** numero pari
- **Disparity check:** numero dispari

**Limiti:**

- ✓ Facile da implementare
- ✗ Non rileva inversione di bit pari

#### 2. LRC (Controllo Ridondanza Longitudinale)

**Funzionamento:**

- Come VRC: bit di parità per ogni unità
- Aggiunge unità supplementare con bit di parità per sequenze corrispondenti
- ✓ Maggiore affidabilità del VRC
- ✗ Può essere ingannato da trasposizioni di byte

#### 3. CRC (Controllo di Ridondanza Ciclica)

**Funzionamento:**

- Orientato ai bit
- Associa ogni sequenza di k bit ai coefficienti di un polinomio di grado k-1
- Usa un **checksum** per rendere il polinomio divisibile per G(x)
- G(x) è conosciuto a priori da ricevitore e mittente

**Calcolo del checksum:**

1. Aggiungere r bit 0 al segmento → sequenza m+r bit corrispondente a x^r × M(x)

   - r = gradi di G(x)
   - M(x) = polinomio della sequenza iniziale

2. Dividere x^r × M(x) per G(x) con divisione mod 2

   - R(x) = polinomio corrispondente al checksum

3. Sommare R(x) a x^r × M(x) → segmento da trasmettere con checksum

**Suggerimenti per G(x):**

- Con polinomi aventi **x⁰ = 1**: errori di un bit sempre rilevati
- Con **x+1** come fattore: rilevazione errori di numero dispari
- **r** deve essere il più grande possibile

**Classi di errori burst (L = lunghezza errore):**

- **L ≤ r:** tutti gli errori rilevati
- **L ≥ (r+1):** errore non rilevato con probabilità (1/2)^r
- **L = (r+1):** errore non rilevato con probabilità (1/2)^(r-1)

---

## Multiplazione

**Definizione:** Utilizzo dello stesso canale per più comunicazioni separate.

### FDM (Frequency Division Multiplexing)

**Funzionamento:**

- Le comunicazioni vengono shiftate a frequenza superiore con un certo gap
- Ancora ampiamente usata nella rete telefonica

**Caratteristiche:**

- Banda fonica: **B = 4 kHz**
- Ogni canale multiplato occupa 4 kHz
- Numero di canali: **N = BT / 4 kHz**
- Traslazione realizzata mediante modulazione di ampiezza di N portanti (**frequenze vertici**)
- In ricezione: filtraggio delle bande e demodulazione per estrarre segnale in banda base
- Da 12 a 10.800 canali multiplabili
- ✗ Sensibile al rumore (segnale analogico)

**Esempio:**

- 12 canali multiplati traslati con portanti distanti 4 kHz (64-68-...-108 kHz)
- Banda totale: **BT = 12 × 4 kHz = 48 kHz**

### WDM (Wavelength Division Multiplexing)

**Utilizzo:** Segnali ottici

**Caratteristiche:**

- Ottimizza l'utilizzo della fibra ottica
- Modula la lunghezza d'onda del raggio luminoso
- ✓ Invio di diversi raggi in contemporanea

### D-WDM (Dense Wavelength Division Multiplexing)

**Caratteristiche:**

- Modula fino a **16 lunghezze d'onda** alla distanza di 0.08 nm
- Lunghezze d'onda modulate con flussi TDM
- Velocità: fino a **1 Tb/s**

#### EDFA (Amplificatori in fibra ottica drogata)

Usano un tratto di fibra drogata di lunghezza L come mezzo per l'amplificazione del segnale ottico. Il segnale ottico e uno di pompa vengono multiplati in una fibra drogata e il segnale risulta amplificato per effetto dell'emissione di fotoni grazie all'interazione del segnale ottico di pompa con gli ioni del drogante.

### C-WDM (Coarse Wavelength Division Multiplexing)

**Utilizzo:** Reti metropolitane a basso costo

**Caratteristiche:**

- Maggiori spaziature tra i canali
- ✓ Risparmio economico
- Spaziatura: circa **20 nm**
- Frequenze: da 1310 nm a 1610 nm

### TDM (Time Division Multiplexing)

**Funzionamento:** Usa la temporizzazione per i differenti segnali

**Tipi:**

1. **TDM Sincrono:**

   - Intervalli scelti indipendentemente dalla presenza di dati
   - Corrispondenza tra dato e canale

2. **TDM Statistico:**
   - Intervalli allocati solo quando ci sono dati da spedire
   - Nessuna corrispondenza fissa tra dato e canale

Un segmento di dati è diviso in base al numero di canali logici disponibili.

---

## Modem

**Modem** = Contrazione di **Modulatore/Demodulatore**

### Funzioni Principali

- Converte segnali dal DTE in segnali adatti per la trasmissione (tipicamente linea telefonica)
- Trasforma segnale numerico dal DTE in segnale analogico e viceversa
- Gestisce circuiti di comando e controlla l'interfaccia
- Corregge errori e analizza i dati ricevuti

### Modem Fonici

**Range di frequenze:** 300-3400 Hz

### Altri Tipi di Modem

- **Modem ISDN:** 128 kbps
- **Modem xDSL:** da 640 kbps a 100 Mbps
- **Modem PLC** (Power Line Communications): su linea elettrica (640 kbps – 200 Mbps)
- **Modem GPRS/UMTS/HSDPA/LTE:** integrati in cellulari o PC card (56 kbps – 7.2 Mbps - 100 Mbps)
- **Modem in banda base:** collega direttamente due utenti su doppino telefonico

### Configurazioni

**Modem esterni:**

- Seriali (cavo COM1/2)
- Paralleli (cavo LPT1/2)
- USB

**Modem interni:**

- PCI (lavorano sul BUS PCI)
- PCMCIA o PC card (solo PC portatili)

### Modulazione per Velocità

- **Bassa velocità** (fino a 1200 bit/s): modulazione **FSK**
- **Velocità media** (fino a 4800 bit/s): modulazione **PSK** o **DPSK**
- **Alta velocità** (oltre 9600 bit/s): modulazione **QAM**

### Standard ITU

Lo standard delle tecniche di interfacciamento è deciso dall'**ITU**.

#### V.21 - FSK

#### V.29 - QAM

- Codifica multilivello su 4 bit
- Spettro: circa 2400 Hz
- Portante: 1700 (±1) Hz

#### V.32 - QAM

- Modalità sincrona point-to-point
- Modulazione QAM
- 2400 baud, quadribit su 16 livelli
- Velocità: 9600 bit/s
- **Codifica Trellis:** maggiore immunità al rumore
  - Aumenta la ridondanza (ogni 4 bit, uno ridondante)
  - Costellazione di 32 livelli
- **Soppressione dell'eco:** invio full-duplex del segnale e sua replica invertita

#### V.34

- Collegamenti con due terminazioni analogiche
- Velocità: 28.880 bit/s
- Codifica non lineare, multidimensionale
- Sfrutta tutta la banda disponibile

#### V.90

- Migliora le prestazioni del V.34
- Flusso verso la rete minore
- Segnale verso l'utente tipo dati

#### V.92

- Upstream: 48 kbps
- **Quick connect**
- Mantiene connessioni attive fino a 16 minuti
- Codifica adattiva

---

## ADSL

(Asymmetrical Digital Subscriber Line)
Il doppino telefonico possiede una discreta banda, limitata però a soli 4 kHz.

### Tecniche di Modulazione

1. **CAP (Carrierless Amplitude Phase)**

   - Versione sofisticata di QAM

2. **DMT (Discrete Multi-Tone)**
   - Modula un insieme di **256 sottoportanti** distanti 4.3125 kHz
   - Banda totale: 26 kHz - 1.1 MHz

### Suddivisione della Banda

1. **Banda bassa:** fino a 4 kHz
2. **Banda media:** per upstream
3. **Banda alta:** per downstream

### Velocità Teoriche

- **Downstream:** 8 Mbit/s
- **Upstream:** 800 kbit/s

### Standard ANSI T1.423

- Non ancora completamente standardizzato
- Ogni costruttore ha varianti proprie
- Linee guida dallo standard ANSI T1.423
- Ammette solo modulazione DMT
- Adattamento di rateo
- Connessione a livello di internetworking con reti ATM

---

## Interfacce

### Interfaccia Centronics Parallela

**Caratteristiche:**

- Interfaccia parallela a 8 bit asincrona
- Uso tipico: collegamento PC-stampante
- Originariamente monodirezionale
- Ora supporta anche dispositivi input
- Connettore tipo D a 25 poli Femmina
- Fino a 3 interfacce LPT parallele
- Ogni interfaccia con 3 indirizzi contigui

**Registri:**

- Primo registro: contiene i dati
- Secondo registro: stato della stampante

### Interfaccia RS232

**Connettori:**

- **DTE:** spina
- **DCE:** presa
- Connettore standard: 25 poli
- Altre applicazioni: connettore a 9 poli

**Linee (Circuiti) dell'interfaccia V.24:**

| Codice | Nome                               | Direzione | Funzione                                      |
| ------ | ---------------------------------- | --------- | --------------------------------------------- |
| C101   | Massa di protezione                | -         | Collegata alla massa dei segnali C102         |
| C102   | Massa di segnali                   | -         | Riferimento comune per tutti i circuiti       |
| C103   | Dati in trasmissione               | DTE → DCE | Dati binari seriali dal DTE al DCE            |
| C104   | Dati in ricezione                  | DCE → DTE | Dati binari seriali dal DCE al DTE            |
| C105   | Richiesta di trasmissione          | DTE → DCE | Trasmette la portante in linea                |
| C106   | Pronto a trasmettere               | DCE → DTE | DCE pronto a trasmettere (risposta a C105)    |
| C107   | Modem pronto                       | DCE → DTE | Modem collegato                               |
| C108   | DTE pronto                         | DTE → DCE | DTE pronto                                    |
| C109   | Portante in ricezione              | DCE → DTE | Portante sopra soglia di ricezione            |
| C110   | Rilevatore qualità segnale         | DCE → DTE | Tutti i dati sono corretti                    |
| C111   | Selezione di velocità              | DTE → DCE | Obbliga il modem a scegliere velocità elevata |
| C112   | Selezione di velocità              | DCE → DTE | Modem seleziona velocità usata                |
| C113   | Clock trasmissione da DTE          | DTE → DCE | Clock del DTE                                 |
| C114   | Clock trasmissione da DCE          | DCE → DTE | Clock del DCE                                 |
| C115   | Clock in ricezione                 | DCE → DTE | Clock per dati ricevuti su C104               |
| C118   | Trasmissione supervisore           | DTE → DCE | Come C103 per canale supervisore              |
| C119   | Ricezione supervisore              | DCE → DTE | Come C104 per canale supervisore              |
| C120   | Richiesta trasmissione supervisore | DTE → DCE | Per canale supervisore                        |
| C121   | Pronto trasmissione supervisore    | DCE → DTE | Per canale supervisore                        |
| C122   | Rilevatore segnale supervisore     | DCE → DTE | Uguale a C109                                 |
| C123   | Rilevatore qualità supervisore     | DCE → DTE | Come C110                                     |
| C125   | Chiamata in arrivo                 | DCE → DTE | Indica ricezione chiamata (risposta su C108)  |
| C125   | Scelta frequenza trasmissione      | -         | -                                             |

### Interfaccia USB

**Storia:** Inventata nel 1995 per sostituire le porte seriali e parallele.

**Versioni:**

- **USB 1.0:** 12 Mbps
- **USB 2.0:** 480 Mbps
- **USB 3.0:** 5 Gbps

**Connettore:** 4 poli disposti verticalmente

- GND
- DATI +
- DATI -
- +5V

### Interfaccia IEEE 1394 (FireWire)

**Caratteristiche:**

- Seriale e bidirezionale
- Concepita per alte velocità
- Standard evoluto: collegamenti fino a 100 m
- Per PC: schede su bus PCI
- Connettori: 4 pin o 6 pin

# PDF_10

### Interfaccia RS422

Standard nato per la trasmissione di segnali digitali fino a 10 Mbits/s su distanze fino a 1200m.

**Caratteristiche principali:**

- Ogni linea differenziale è pilotata da un driver dedicato
- Utilizzo comune per connessioni punto a punto
- Supporto fino a 10 ricevitori per linea

**Stati logici:**

- **Stato logico 1 (idle)**: terminale A negativo rispetto a B (A < B)
- **Stato logico 0**: terminale A positivo rispetto a B (A > B)
- La differenza di potenziale tra A e B deve essere almeno 4V
- I terminali A e B hanno sempre valori opposti tra loro

### Reti per la Trasmissione Dati

**Tipologie principali:**

- **PSTN** (Public Switching Telephone Network)
- **ISDN** (Integrated Service Digital Network)
- **CATV** (Community Antenna Television)
- **LAN** (Local Area Network)
- **VPN** (Virtual Private Network)
- **Wireless Network**

Queste rappresentano connessioni fisiche a reti di ISP (Internet Service Provider) che forniscono accesso a Internet.

### Strutture di Rete in Italia

**Doppino telefonico (Twisted Pair):**

La rete italiana si basa prevalentemente su doppini telefonici organizzati in tre livelli:

1. **Rete di accesso primaria**: tra centrale e armadio stradale

   - Composta da cavi con centinaia di coppie

2. **Rete secondaria**: tra armadio e distributore

   - Composta da cavi con decine di coppie

3. **Raccordo cliente (cablaggio verticale)**: tra distributore e borchia di accesso
   - Ultimo miglio verso l'utente finale

### Tecnologie in Fibra Ottica

**FTTH (Fiber To The Home):**

- **OLT** (Optical Line Termination): terminazione in centrale
- **ONU** (Optical Network Unit): interfaccia con il terminale utente
- **ONT** (Optical Network Termination): terminazione ottica presso l'utente

**FTTC (Fiber To The Cabinet):**

- Fibra fino all'armadio stradale
- Ultimo tratto in rame fino all'abitazione

**FTTB (Fiber To The Building):**

- Fibra fino alla centralina condominiale
- Collegamento finale in rame

**Architetture di rete in fibra:**

- **AON** (Active Optical Network): detta anche P2P (Point-to-Point)
  - Presenza di apparati attivi lungo il percorso
- **PON** (Passive Optical Network):
  - Assenza di apparati attivi tra OLT e ONT/ONU
  - Utilizza topologia ad albero
  - Maggiore efficienza energetica

### Tecnologie Banda Larga

#### xDSL

**Caratteristiche:**

- Sfrutta cavi a coppie recenti e circuiti utente brevi
- In Italia circa 1/3 della popolazione non ha accesso a centrali DSLAM nel proprio comune

**DSLAM** (Digital Subscriber Line Access Multiplexer):

- Multiplexa migliaia di accessi DSL
- Fornisce un'unica interfaccia ad alta densità verso la rete di trasporto
- Opera come switch di rete a livello 2 OSI

#### Televisione Digitale Terrestre Interattiva (DVB-H)

**Standard europeo DVB-H:**

- Permette ricezione su dispositivi portatili
- Combina standard video digitale con protocollo IP
- Suddivide contenuti in pacchetti dati trasferibili su rete cellulare

#### Comunicazioni Mobili 3G e 4G

**Evoluzione delle tecnologie:**

1. **GSM** (Global System for Mobile Communications)
2. **GPRS** (General Packet Radio Service)
3. **UMTS** (Universal Mobile Telecommunications System)
4. **HSPA** (High Speed Packet Access) - tecnologia 3G avanzata

### PDH (Plesiochronous Digital Hierarchy)

**Caratteristiche:**

- Tecnologia per multiplexing e demultiplexing di canali aggregati
- Le unità sono sincronizzate ma non perfettamente
- Per estrarre un singolo canale è necessario estrarre un elemento della gerarchia per volta

**Funzionamento:**

- Codifica PCM genera flussi da 64 kbit/s
- Trame ripetute ogni 125 μs
- Primo metodo di multiplazione con 32 canali (30 dati + 2 controllo)
- Utilizza multiplexer TDM (Time Division Multiplexing)
- Il multiplexer inserisce slot aggiuntivi per compensare differenze di bitrate
- **Limitazione**: non controlla le prestazioni della rete

### SDH (Synchronous Digital Hierarchy)

**Vantaggi rispetto a PDH:**

- Risolve i problemi di temporizzazione di PDH
- Protocollo a livello fisico per trasmissione su fibra e rete elettrica
- Tutti gli elementi di rete sincronizzati sullo stesso clock
- Aggrega flussi con bitrate diversi

**Caratteristiche tecniche:**

- Permette elevati livelli di qualità tramite informazioni di servizio
- Utilizzata per anelli ottici di accesso (topologia a rete o P2P)
- Nessun limite di distanza
- Velocità fino a 140 Gbit/s
- **Limitazione**: utilizza TDM

**Evoluzione:**

- Per reti con maggior numero di accessi si preferisce Gigabit Ethernet
- SDH evolve in OTN (Optical Transport Network)

# PDF_11

### SONET (Synchronous Optical Network)

**Architettura a livelli:**

1. **Path Layer** (Livello 3 OSI):

   - Responsabile della comunicazione end-to-end
   - Controlla e gestisce lo stato delle connessioni

2. **Line Layer** (Livello 2 OSI):

   - Multiplexing di diversi path tra due nodi
   - Protezione ai guasti

3. **Section Layer** (Livello 2 OSI):

   - Definisce funzioni dei rigeneratori lungo il canale

4. **Photonic Layer** (Livello 1 OSI):
   - Definisce formato di trasmissione su fibra

### Rete CDN (Circuit Data Network)

**Caratteristiche:**

- Rete digitale parallela alla PSTN
- Rete centrale con multiplazione verso gli utenti
- Collegamenti numerici punto-punto o punto-multipunto
- Mette a disposizione un flusso dati della banda desiderata tra due località qualunque del territorio nazionale
- Tecnica di multiplazione trasparente all'utente

### Rete ISDN (Integrated Services Digital Network)

**Obiettivi:**

- Evoluzione della rete telefonica tradizionale
- Collegamento digitale end-to-end senza modem
- Richiede apparati specifici presso centrale e utente

**Struttura canali:**

- **2 canali B**: per fonia/dati (64 kbit/s ciascuno)
- **1 canale D**: di controllo e segnalazione (16 kbit/s)
- Possibilità di raggruppare i due canali B per ottenere 128 kbit/s

**Soluzioni di accesso:**

1. **BRI** (Basic Rate Interface):

   - Per utenti residenziali e piccole aziende
   - 2B+D (144 kbit/s totali)

2. **PRI** (Primary Rate Interface):
   - Per grandi aziende
   - Supporta fino a 30 linee multiplexate
   - Accesso a 2 Mbit/s
   - 30B+D

**Componenti hardware:**

- **NT1** (Network Termination 1):

  - Termina la linea ISDN
  - Converte il doppino in bus S (8 fili, connettori RJ45)
  - Bus S compatibile con LAN Ethernet 10/100baseT

- **TA** (Terminal Adapter):

  - Interfaccia dispositivi non nativamente compatibili con bus S
  - Conversione per apparecchi analogici

- **ISPBX**: centralino telefonico per ISDN

**Protocolli:**

- **LAPD** (Link Access Protocol channel D): protocollo di livello 2
- Modalità **ABM** (Asynchronous Balanced Mode)
- Segnale in linea digitale **2B1Q** (no conversione A/D necessaria)

### Standard di Videocomunicazione

#### H.320

- Trasmissione audio/video su linee digitali ISDN
- Trasmissione digitale indipendente dalla velocità ISDN

#### H.323

- Standard per sessioni audio, video e dati su reti packet-switched
- Non garantisce QoS (Quality of Service)
- Interoperabilità tra applicazioni di produttori diversi

#### H.324

- Comunicazione multimediale su linee a basso bitrate
- Per reti PLMN (Public Land Mobile Network) e 3G

#### T.120

- Standard per conferenze dati
- Comunicazione real-time tra più partecipanti
- Funzioni aggiuntive:
  - Lavagna elettronica condivisa
  - Chat testuale
  - Scambio file
  - Condivisione applicazioni

---

## Protocolli di Livello 2 ISO-OSI (Data Link)

Il livello Data Link gestisce il trasferimento corretto dei dati sulla linea trasmissiva, strutturando i dati in frame e implementando controllo di flusso ed errori.

I protocolli di trasmissione definiscono le regole che DTE, DCE e CPE devono seguire per garantire la corretta ricezione dei dati.

### Protocolli Asincroni (Start/Stop)

**Caratteristiche:**

- Prima forma di protocollo per trasmissione dati
- Trasmissione di caratteri singoli
- Intervallo variabile tra caratteri successivi
- Bit time di durata definita

**Struttura frame:**

- 1 bit di start
- n bit di dati (tipicamente 7-8)
- 1 bit di parità (opzionale)
- 1-2 bit di stop

**Gestione errori:**

- Errore di framing se il bit di stop non corrisponde
- Protocollo XMODEM tipico esempio

**Protocollo XMODEM:**

1. Ricevente invia **NAK** ogni 10 secondi per segnalare disponibilità
2. Trasmettitore invia pacchetto dati
3. Ricevente risponde:
   - **ACK** (ASCII 06H): ricezione corretta
   - **NAK**: ricezione errata, ritrasmissione
4. A termine il mittente invia **EOT** (ASCII 04H)
5. Ricevitore conferma EOT con ACK finale

### Protocolli Sincroni

**Differenze rispetto agli asincroni:**

- Assenza di bit di start/stop
- Sincronizzazione tramite:
  - Caratteri SYN (protocolli orientati al carattere)
  - Sequenze di bit flag (protocolli orientati al bit)
- Trama con numero di bit definito dal protocollo

#### BSC (Binary Synchronous Communications)

**Tre modalità operative:**

1. Rete dedicata punto-punto
2. Rete commutata punto-punto
3. Rete multipunto

**Codifiche supportate:**

- ASCII
- EBCDIC
- SBT (Six-Bit Transcode)

**Tipi di trame:**

- Trame di controllo
- Trame informative

**Funzionamento punto-punto:**

- Trasmettitore invia caratteri di sincronismo (SYN)
- Entrambi i DTE possono essere trasmettitori o ricevitori
- In caso di contesa:
  - Un DTE diventa stazione primaria (ripete invio)
  - L'altro diventa stazione secondaria
- Risposta con ACK (successo) o NAK (errore)
- Terminazione con EOT

**Funzionamento multipunto (BSC3):**

- Interrogazione ciclica (polling) per individuare terminale destinatario
- Stazione primaria gestisce le comunicazioni

#### HDLC (High-Level Data Link Control)

**Caratteristiche generali:**

- Protocollo orientato ai bit
- Standard ISO per trasmissioni sincrone full-duplex
- Formati fissi definiti in frame/trame
- Utilizzato per grandi reti

**Tipi di connessione:**

1. **Bilanciata**: tra due stazioni paritarie
2. **Sbilanciata**: una primaria, più secondarie (half-duplex)

**Modalità operative:**

1. **NRM** (Normal Response Mode):

   - Sbilanciata, half-duplex
   - Stazione secondaria trasmette solo su permesso

2. **ABM** (Asynchronous Balanced Mode):

   - Unica modalità LAPB (canale B)
   - Bilanciata, full-duplex
   - Entrambe le stazioni possono iniziare trasmissione

3. **ARM** (Asynchronous Response Mode):
   - Simile a NRM ma limitata a due stazioni
   - Stazione secondaria può iniziare trasmissione

**Struttura frame HDLC:**

```
+------+----------+----------+---------------+------+
| Flag | Indirizzo| Controllo| Informazione | FCS  | Flag |
| 8bit |  8bit+   |  8bit+   |   variabile  | 16bit+ | 8bit |
+------+----------+----------+---------------+------+
```

**Campi del frame:**

1. **Flag** (01111110):

   - Delimitatore di inizio/fine frame
   - Trasmesso continuamente in linea idle
   - Utilizza bit stuffing per trasparenza

2. **Indirizzo** (8 bit, estendibile):

   - Non indica protocollo di livello rete
   - Contiene altre informazioni di controllo

3. **Controllo** (8 bit, estendibile):

   - Identifica tipo di trama

4. **Campo informativo**:

   - Contiene pacchetto dati da livello OSI 3
   - Nessun limite teorico di ampiezza

5. **FCS** (Frame Check Sequence):
   - Campo di ridondanza ciclica
   - Minimo 16 bit (tipicamente CRC-16 o CRC-32)

**Tipi di frame:**

1. **I-frame** (Information):

   - Trasporto dati utente
   - Contiene numeri di sequenza per controllo flusso

2. **S-frame** (Supervisory):

   - Controllo flusso
   - ACK e richieste di ritrasmissione
   - Non contiene campo informativo

3. **U-frame** (Unnumbered):
   - Setup e gestione del link
   - Comandi speciali di controllo
   - Modalità operative

---

# MODULO 2 - TCP/IP

# PDF_1

### Indirizzamento IP

**Struttura IP address:**

- 32 bit (IPv4)
- Identifica univocamente un host in rete
- Suddiviso in due parti:
  - **Network ID**: identifica la rete
  - **Host ID**: identifica l'host nella rete

> **Importante**: Gli indirizzi vengono assegnati alle interfacce, non agli host!

### Classi di Indirizzi IP

**Classe A:**

- Primo bit: 0
- Range: 1.0.0.0 - 126.255.255.255
- Subnet mask: 255.0.0.0 (/8)
- Reti: 126
- Host per rete: 16.777.214

**Classe B:**

- Primi due bit: 10
- Range: 128.0.0.0 - 191.255.255.255
- Subnet mask: 255.255.0.0 (/16)
- Reti: 16.384
- Host per rete: 65.534

**Classe C:**

- Primi tre bit: 110
- Range: 192.0.0.0 - 223.255.255.255
- Subnet mask: 255.255.255.0 (/24)
- Reti: 2.097.152
- Host per rete: 254

**Classe D:**

- Primi quattro bit: 1110
- Range: 224.0.0.0 - 239.255.255.255
- Utilizzo: multicast

**Classe E:**

- Primi quattro bit: 1111
- Range: 240.0.0.0 - 255.255.255.255
- Riservata per uso sperimentale

### Indirizzi IP Riservati

**Indirizzi privati (RFC 1918):**

- Classe A: 10.0.0.0/8
- Classe B: 172.16.0.0/12 (172.16.0.0 - 172.31.255.255)
- Classe C: 192.168.0.0/16

**Altri indirizzi speciali:**

- **127.0.0.0/8**: loopback (127.0.0.1)
- **0.0.0.0**: indirizzo non specificato
- **255.255.255.255**: broadcast limitato
- **Network address**: tutti bit host a 0
- **Broadcast address**: tutti bit host a 1

### Subnetting

**Subnet Mask:**

- Permette di suddividere una rete in sottoreti
- Utilizza parte dei bit host come bit di rete

**Regole:**

- Bit a **1**: parte dell'indirizzo di rete
- Bit a **0**: parte dell'indirizzo host

**Esempio pratico:**

```
IP: 192.168.1.130
Subnet mask: 255.255.255.192 (/26)

Network: 192.168.1.128
Primo host: 192.168.1.129
Ultimo host: 192.168.1.190
Broadcast: 192.168.1.191
Host disponibili: 62
```

### Routing e Tabella di Routing

**Routing:**
I gateway instradano dati tra reti diverse.

**Decisioni di instradamento dell'host:**

1. Se destinazione è sulla rete locale → invio diretto
2. Se destinazione è remota → invio a gateway locale

**Processo di analisi indirizzo IP:**

1. Determina classe dell'indirizzo
2. Estrae network ID di destinazione
3. Cerca rete nella routing table
4. Instrada pacchetti secondo la tabella

**Visualizzare routing table:**

```bash
netstat -nr
```

**Struttura routing table:**

- **Destination**: rete di destinazione
- **Gateway**: gateway da utilizzare
- **Genmask**: subnet mask
- **Flags**: stato della route (U=Up, G=Gateway, H=Host)
- **Iface**: interfaccia di uscita

**Route flags comuni:**

- **U**: route attiva (Up)
- **G**: route utilizza gateway
- **H**: route verso host specifico
- **D**: route creata dinamicamente
- **M**: route modificata dinamicamente

# PDF_2

### ARP (Address Resolution Protocol)

**Funzione:**
Risoluzione dinamica indirizzi IP in indirizzi fisici (MAC address)

**Funzionamento:**

1. Host A necessita MAC address di Host B
2. Host A invia richiesta ARP in broadcast sulla LAN
3. Host B risponde con il proprio MAC address
4. Host A memorizza associazione in cache ARP

**Cache ARP:**

- Ogni macchina mantiene una cache ARP
- Memorizza associazioni IP-MAC temporanee
- Riduce traffico di rete

**Visualizzare cache ARP:**

```bash
arp -a
```

### RARP (Reverse ARP)

**Utilizzo:**

- Per workstation diskless
- Per dispositivi senza storage locale

**Funzionamento:**

1. Workstation conosce solo il proprio MAC address
2. Invia richiesta RARP broadcast
3. Server RARP risponde con IP address assegnato
4. Workstation può caricare SO e configurazione

### Numeri di Protocollo

**Definizione:**

- Byte nel datagram header IP
- Identifica protocollo del livello superiore

**File di configurazione:**

```bash
cat /etc/protocols
```

**Protocolli comuni:**

- **1**: ICMP
- **6**: TCP
- **17**: UDP
- **89**: OSPF

### Numeri di Porta

**Caratteristiche:**

- 16 bit (0-65535)
- Identificano processi/servizi su un host

**Tipi di porte:**

1. **Well-known ports** (0-1023):

   - Servizi standard
   - Richiedono privilegi root

2. **Registered ports** (1024-49151):

   - Servizi registrati IANA

3. **Dynamic/Private ports** (49152-65535):
   - Assegnazione dinamica

**Porte nel TCP segment:**

- **Source port**: porta sorgente
- **Destination port**: porta destinazione

**Visualizzare porte:**

```bash
cat /etc/services
```

**Porte comuni:**

- **20/21**: FTP (dati/controllo)
- **22**: SSH
- **23**: Telnet
- **25**: SMTP
- **53**: DNS
- **80**: HTTP
- **110**: POP3
- **143**: IMAP
- **443**: HTTPS

### Struttura Frame di Rete

**Incapsulamento:**

```
[Frame Ethernet]
  [Datagram IP]
    [Segmento TCP/UDP]
      [Dati Applicazione]
```

**Frame Ethernet:**

- Preamble (7 byte)
- SFD (1 byte)
- MAC destinazione (6 byte)
- MAC sorgente (6 byte)
- Type/Length (2 byte)
- Dati (46-1500 byte)
- FCS (4 byte)

---

# PDF_3

## Name Service (Servizi di Risoluzione Nomi)

### Funzione

Associa nomi simbolici (hostname) agli indirizzi IP delle interfacce di rete.

**Caratteristiche:**

- Nomi e IP sono generalmente intercambiabili
- Il sistema converte automaticamente hostname → IP
- Necessaria traduzione nota a tutti gli host della rete

### Host Table

**File di configurazione:**

```bash
/etc/hosts
```

**Caratteristiche:**

- Tabella statica locale
- Formato: `IP_address hostname [alias...]`
- Utilizzata come fallback se DNS non disponibile
- Utile per host critici locali

**Esempio:**

```
127.0.0.1       localhost
192.168.1.1     router gateway
192.168.1.10    server1 srv1
```

**NIC Host Table:**

- Registro centralizzato degli host registrati
- Scaricabile via FTP da NIC
- Ormai obsoleta per reti grandi

### DNS (Domain Name System)

**Caratteristiche:**

- Sistema di database distribuiti
- Architettura gerarchica
- Aggiornamento automatico della rete
- Scalabile per reti di qualsiasi dimensione

**Funzionamento:**

1. Client invia query DNS al server locale
2. Se il server non ha l'informazione:
   - Inoltra query al server autoritativo
   - Server autoritativo risponde
3. Server locale memorizza risposta in cache
4. Risposta inviata al client

**Componenti DNS (BIND - Berkeley Internet Name Domain):**

1. **Resolver**:

   - Gestisce le query DNS
   - Componente client
   - Libreria utilizzata dalle applicazioni

2. **Name Server**:
   - Gestisce le risposte
   - Componente server
   - Mantiene database DNS

**Tipi di Name Server:**

1. **Primary Server (Master)**:

   - Fonte autoritativa per un dominio
   - Carica dati da file di zona locali
   - Autorità primaria per il dominio

2. **Secondary Server (Slave)**:

   - Backup del primary server
   - Trasferisce intero database dal primary (zone transfer)
   - Fornisce ridondanza e load balancing

3. **Caching-only Server**:
   - Non autoritativo per alcun dominio
   - Memorizza risposte da altri server
   - Riduce carico di rete e tempo di risposta

**Gerarchia DNS:**

```
.                    (root)
├── com
│   └── example.com
├── org
├── net
└── it
    └── dominio.it
```

---

## Configurazione TCP/IP

### Parametri Essenziali

Per configurare correttamente un host TCP/IP sono necessari:

1. **IP Address**: indirizzo univoco dell'interfaccia
2. **Hostname**: nome simbolico dell'host
3. **Default Gateway Address**: router di default
4. **Subnet Mask**: maschera di sottorete
5. **Domain Name**: dominio DNS di appartenenza
6. **Name Server Address**: indirizzi server DNS
7. **Broadcast Address**: indirizzo di broadcast
8. **Routing Protocol**: protocollo di routing (se necessario)

### Assegnazione Indirizzi IP

**Autorità di assegnazione:**

- **NIC** (Network Information Center) - storicamente
- **RIPE** (Réseaux IP Européens) - per Europa
- **IANA/ICANN** - coordinamento globale

**Strategie di assegnazione:**

1. **Sequenziale**: indirizzi consecutivi agli host
2. **A blocchi**: blocchi di indirizzi per sottoreti
   - Delega gestione a amministratori di sottorete
   - Maggiore flessibilità organizzativa

### Configurazione del Routing

**Tre approcci principali:**

#### 1. Routing Minimale

- Nessuna configurazione di routing necessaria
- Host connesso a una sola rete
- Nessun gateway configurato
- Comunicazione solo sulla rete locale

**Caso d'uso:**

- Workstation in rete isolata
- Dispositivi IoT su VLAN dedicata

#### 2. Routing Statico

- Tabelle di routing configurate manualmente
- Costruite dall'amministratore di rete
- Route non cambiano automaticamente

**Vantaggi:**

- Controllo totale sul percorso dati
- Predicibilità del traffico
- Minimo overhead

**Svantaggi:**

- Manutenzione manuale richiesta
- Non si adatta a cambiamenti di topologia
- Scalabilità limitata

**Caso d'uso:**

- Reti piccole e stabili
- Connessioni punto-punto critiche

#### 3. Routing Dinamico

- Tabelle di routing costruite automaticamente
- Utilizzo di protocolli di routing
- Adattamento automatico a cambiamenti di rete

**Protocolli comuni:**

- **RIP** (Routing Information Protocol)
- **OSPF** (Open Shortest Path First)
- **BGP** (Border Gateway Protocol)

**Vantaggi:**

- Adattamento automatico a guasti
- Scalabilità eccellente
- Bilanciamento del carico

**Svantaggi:**

- Overhead di protocollo
- Complessità configurazione iniziale
- Convergenza può richiedere tempo

### Scelta del Tipo di Routing

**Fattori da considerare:**

1. **Rete senza gateway**:

   - Routing minimale
   - Tutti gli host sulla stessa rete

2. **Rete con un solo gateway**:

   - Routing statico con default gateway
   - Configurazione semplice

3. **Rete con più gateway interni e uno esterno**:

   - Routing statico per sottoreti
   - Default gateway per traffico esterno

4. **Rete con molti gateway esterni**:
   - Routing dinamico necessario
   - Protocolli come OSPF o BGP

### Definizione delle Sottoreti

#### Motivazioni Topologiche

**1. Superamento limiti di distanza:**

- Componenti hardware hanno limiti fisici
- Router IP estendono la portata della rete
- Rigenerazione del segnale

**Esempio:**

- Ethernet 10Base2: max 185m per segmento
- Router permettono connessione tra edifici

**2. Connessione reti fisiche diverse:**

- Router IP collegano tecnologie diverse
- Ethernet ↔ Wi-Fi
- LAN ↔ WAN

**3. Filtro del traffico:**

- Traffico locale rimane nella sottorete locale
- Riduzione congestione rete
- Miglioramento prestazioni complessive

**Vantaggi:**

- Broadcast confinati alla sottorete
- Minor collisioni (in reti shared medium)
- Banda disponibile maggiore per host

#### Motivazioni Organizzative

**1. Struttura organizzativa:**

- Sottoreti per dipartimenti/settori
- Esempio: sottorete per IT, una per vendite, una per produzione

**2. Delegazione amministrativa:**

- Amministratori locali per ogni sottorete
- Responsabilità distribuite
- Gestione decentralizzata

**3. Isolamento del traffico (sicurezza):**

- Separazione rete produzione da rete ospiti
- VLAN per dati sensibili
- Controllo accessi tra sottoreti

**Implementazione:**

- Firewall tra sottoreti
- ACL (Access Control List) sui router
- Segmentazione fisica o logica (VLAN)

**4. Isolamento problemi potenziali:**

- Rete di test separata
- Ambiente di sviluppo isolato
- Sperimentazioni senza impatto su produzione

**Vantaggi:**

- Guasti confinati a una sottorete
- Test senza rischi per produzione
- Facilità di troubleshooting

### Best Practices Configurazione

**Documentazione:**

- Piano di indirizzamento IP completo
- Diagramma topologia di rete
- Tabelle di assegnazione subnet

**Sicurezza:**

- Utilizzo indirizzi privati (RFC 1918)
- NAT per accesso Internet
- Firewall ai confini di rete

**Ridondanza:**

- Server DNS multipli
- Gateway ridondanti (VRRP/HSRP)
- Link backup per connettività critica

**Monitoraggio:**

- SNMP per dispositivi di rete
- Logging centralizzato
- Alerting automatico per problemi


# PDF_4

## Internet Daemon (inetd)

Alcuni daemon di protocolli come `routed` e `named` (per Routing Information Protocol e DNS) vengono avviati automaticamente al boot del sistema. Altri servizi vengono gestiti da un **super daemon** chiamato **Internet Daemon (inetd)**.

### Funzionamento di inetd

inetd analizza le richieste in arrivo e avvia i daemon appropriati per ciascun servizio. Il suo processo di avvio prevede:

1. Parte tramite uno script come `/etc/rc`
2. Legge il file di configurazione `/etc/inetd.conf` che contiene l'elenco dei daemon da avviare

### Struttura del file inetd.conf

Ogni definizione nel file di configurazione contiene i seguenti campi:

- **name** → Nome del servizio
- **type** → Tipo di socket utilizzato:
  - `stream` → TCP byte stream
  - `dgram` → Servizio UDP
  - `raw` → Servizio datagram IP
- **protocol** → Nome del protocollo (es. TCP o UDP)
- **wait-status** → Comportamento del socket:
  - `wait` → Deve aspettare che il server rilasci il socket
  - `nowait` → Può iniziare una nuova connessione su quel socket
- **uid** → Nome dell'utenza sotto cui gira il server
- **server** → Pathname del programma server che inetd deve avviare
- **arguments** → Lista di argomenti da passare al programma server invocato

---

## Architettura di rete TCP/IP

![alt text](images/tcpiparch.png)

### Livelli inferiori all'IP

TCP/IP non specifica i livelli 1 e 2 del modello OSI, ma utilizza quelli conformi agli standard esistenti. Su reti locali, ad esempio, opera su Ethernet/IEEE 802.3.

---

## Dispositivi di rete e livelli OSI

![alt text](images/dispositiviosi.png)

### Repeater (Livello 1)

Opera a **livello fisico** (livello 1 OSI). Ripete semplicemente il segnale che riceve senza alcuna elaborazione. Viene utilizzato quando vi sono limitazioni fisiche alla lunghezza della LAN, per estendere la portata del segnale.

### Bridge (Livello 2)

Dispositivo che opera a **livello data link** (livello 2 OSI).

**Funzionalità principali:**
- Crea una LAN estesa collegando due o più LAN
- Ritrasmette selettivamente i pacchetti alle LAN a cui è connesso
- Ha prestazioni elevate e, operando a livello 2, non si occupa dei protocolli di livello superiore

**Tipologie di bridge:**
- **Transparent Bridge** → Collega 2 LAN Ethernet o IEEE 802.3
- **Source Routing Bridge** → Collega 2 LAN Token Ring
- **Translation Bridge** → Collega 2 LAN di tipo diverso

**Operazioni principali:**
1. **Filtering** → Analizza le trame identificando la workstation di destinazione
2. **Forwarding** → Inoltra le trame indirizzate alla destinazione corretta

### Learning Bridge

Grazie all'indirizzo MAC presente su ogni adattatore di rete, i learning bridge "imparano" automaticamente la posizione delle varie stazioni nella rete.

**Limitazioni dei bridge:**
- Falliscono quando esistono percorsi multipli per collegare 2 LAN (creano loop)
- I percorsi multipli sono però necessari per aumentare l'affidabilità e la ridondanza della connessione

### Router (Livello 3)

Opera a **livello rete** (livello 3 OSI). Instrada i pacchetti tra le varie reti e supporta percorsi multipli.

**Caratteristiche:**
- Collaborano tra loro per trovare i percorsi migliori
- Il funzionamento dipende dal protocollo di routing utilizzato
- Più intelligenti dei bridge, ma con maggiore overhead

![alt text](images/routerebridge.png)

### Brouter

Dispositivo ibrido che si comporta come:
- **Router** per certi protocolli
- **Bridge** per altri protocolli

### Router vs Gateway (Terminologia)

**Importante:** Nel mondo TCP/IP esiste confusione terminologica:
- I **router IP** vengono spesso chiamati erroneamente "gateway"
- I veri **gateway** nel modello OSI non hanno un corrispettivo diretto in TCP/IP
- I router IP effettuano l'instradamento basandosi sulle tabelle di routing

### Gateway (nel senso proprio)

Dispositivo utilizzato per connettere reti con **architetture completamente diverse**. Converte i protocolli di un'architettura in quelli di un'altra, operando potenzialmente a tutti i livelli OSI.

---

## Protocolli di supporto

### ICMP (Internet Control Message Protocol)

Progettato per riportare anomalie nel routing dei pacchetti IP e per verificare lo stato della rete.

**Principali codici ICMP:**
- **0** → Echo Reply
- **3** → Destination Unreachable
- **4** → Source Quench
- **5** → Redirect
- **8** → Echo Request
- **11** → Time Exceeded
- **12** → Parameter Problem
- **13** → Timestamp Request
- **14** → Timestamp Reply
- **15** → Information Request
- **16** → Information Reply
- **17** → Address Mask Request
- **18** → Address Mask Reply

**Note importanti:**
- Il messaggio **Redirect** indica al mittente di utilizzare una route migliore
- I messaggi di **Address Mask** sono stati introdotti per permettere a un'interfaccia di scoprire automaticamente la netmask utilizzata dalla rete

### ARP e RARP

Protocolli utilizzati per scoprire automaticamente le corrispondenze tra:
- Indirizzi di **livello 3** (IP)
- Indirizzi di **livello 2** (MAC address)

**ARP (Address Resolution Protocol):**
- Utilizzato per inviare messaggi sulla stessa rete conoscendo solo l'indirizzo IP
- Permette di scoprire il MAC address corrispondente a un IP

**RARP (Reverse ARP):**
- Utilizzato dalle postazioni diskless per scoprire il proprio indirizzo IP durante il bootstrap
- Opera al contrario dell'ARP: da MAC address a IP address

**Limitazione:** Operano solo su reti locali (non attraversano i router).

---

## Autonomous System (AS)

Il routing TCP/IP è organizzato gerarchicamente su più livelli:

1. **Primo livello** → Routing locale all'interno della stessa rete
2. **Secondo livello** → Routing tra sottoreti diverse, gestito dagli IP router
3. **Terzo livello** → Raggruppa tutte le reti in **Autonomous System (AS)**, insiemi di reti controllate da un'unica autorità amministrativa

### Caratteristiche degli AS

- Identificati da un **numero intero univoco** a livello globale
- Assegnato da un'autorità centrale
- Permettono una gestione gerarchica del routing Internet

### Tipologie di router

**Interior Router:**
- Instradano pacchetti all'interno dello stesso AS
- Utilizzano **Interior Gateway Protocol (IGP)**

**Exterior Router:**
- Instradano pacchetti anche verso AS esterni
- Utilizzano **Exterior Gateway Protocol (EGP)**

---

## Configurazione delle interfacce di rete

### Comando ifconfig

Imposta o controlla i valori delle interfacce di rete, identificando IP, netmask e broadcast address.

**Sintassi:**
```bash
ifconfig interface address netmask mask broadcast address
```

**Esempio pratico:**
```bash
ifconfig le0 128.66.12.2 netmask 255.255.255.0 broadcast 128.66.12.255
```

**Parametri:**
- **interface** → Nome dell'interfaccia da configurare (es. `le0`, `eth0`)
- **address** → Indirizzo IP assegnato all'interfaccia (formato decimale puntato o hostname)
  - Se si usa un hostname, deve essere presente in `/etc/hosts` per la risoluzione locale
- **netmask mask** → Subnet mask per l'interfaccia
  - Da impostare solo se si divide la rete in sottoreti
  - Tutti i sistemi della stessa rete devono avere la stessa subnet mask
- **broadcast address** → Indirizzo di broadcast per la rete
  - Generalmente è l'indirizzo della rete con tutti i bit dell'host impostati a 1

---

### Comando netstat

Visualizza lo stato delle interfacce di rete e delle connessioni.

**Sintassi per visualizzare le interfacce:**
```bash
netstat -ain
```

**Opzioni:**
- **-i** → Mostra le interfacce configurate
- **-a** → Considera tutte le interfacce
- **-n** → Output in forma numerica (senza risoluzione DNS)

![alt text](images/netstat.png)
![alt text](images/netsat2.png)

---

# PDF_5

## Comandi avanzati di ifconfig

### Impostare il Broadcast Address

```bash
ifconfig le0 128.66.12.2 netmask 255.255.255.0 broadcast 128.66.12.255
```

Questo comando:
- Definisce la rete locale come `128.66.12.0`
- Imposta il broadcast a `128.66.12.255`
- **Nota:** L'indirizzo `128.66.255.255` viene interpretato come host 255 della sottorete 255 della rete 128.66.0.0, NON come indirizzo di broadcast

### Assegnare un indirizzo a un'interfaccia

```bash
ifconfig le0 128.66.12.2
```

### Posizionamento dei comandi ifconfig

I comandi ifconfig vengono eseguiti automaticamente in fase di boot:

- **Unix BSD** → Script `/etc/rc.boot` o `/etc/rc.local`
- **Unix System V** → Script `/etc/tcp` o `/etc/init.d/tcp`

### Abilitare/Disabilitare interfacce (up/down)

```bash
ifconfig le0 down           # Disabilita l'interfaccia
ifconfig le0 129.66.1.2 up  # Riabilita l'interfaccia con nuovo IP
```

### Opzioni ARP e Trailer (solo Ethernet)

Queste opzioni si usano solo per interfacce di tipo Ethernet.

**Trailer:**
- Abilita o disabilita la modalità **trailer encapsulation** dei pacchetti IP
- Permette di ridurre le copie memory-to-memory richieste dal sistema ricevente
- Poco utilizzata nelle reti moderne

**ARP:**
- Abilita o disabilita la mappatura automatica degli indirizzi IP con gli indirizzi fisici Ethernet
- Normalmente lasciata abilitata

### Opzione metric

Si utilizza solo in sistemi Unix che usano **RIP (Routing Information Protocol)**.

RIP distribuisce automaticamente informazioni di routing agli altri host e costruisce dinamicamente le tabelle di routing. Le scelte di instradamento vengono prese in base al **costo di routing (metric)**.

**Impostare il metric di un'interfaccia:**
```bash
ifconfig le0 26.104.0.19 metric 3
```

**Quando usarlo:**
- Si utilizza preferibilmente quando esiste un'altra route alternativa e si vuole favorire una come primaria
- Valori di metric più bassi indicano route preferibili

---

## Configurazione avanzata del Routing

### Tipologie di routing

1. **Routing minimale** → Rete isolata da tutte le altre reti TCP/IP
2. **Routing statico** → Per reti con numero limitato di gateway. Tabella costruita manualmente
3. **Routing dinamico** → Cambia automaticamente in base alle condizioni della rete. I router si scambiano informazioni e aggiustano le tabelle dinamicamente

---

### Routing Statico

**Visualizzare la tabella di routing:**
```bash
netstat -rn
```

![alt text](images/tabella_routing_minima.png)

**Interpretazione:**
- **Prima riga** → Route di loopback verso localhost (127.0.0.1)
- **Seconda riga** → Route verso la rete locale 128.66.12.0 sull'interfaccia le0

**Limitazioni di questa tabella minima:**
- Permette la comunicazione solo con host della rete locale
- Non consente l'accesso a reti esterne

### Comando route

Aggiunge o rimuove voci nella tabella di routing.

**Sintassi:**
```bash
route add <destinazione> <gateway> <metric>
```

**Esempio:**
```bash
# route add 26.0.0.0 128.66.12.1 1
add net 26.0.0.0 gateway almond
```

**Parametri:**
- **Primo argomento** → `add` o `delete`
- **Secondo argomento** → Indirizzo di destinazione (rete o host)
- **Terzo argomento** → Gateway (indirizzo di un gateway su una rete connessa direttamente)
- **Quarto argomento** → Routing metric:
  - `0` → Route locale
  - `>0` → Route esterna

![alt text](images/static_tabel_example.png)

### Aggiungere la Default Route

```bash
# route -n add default 128.66.12.1
add net default: gateway 128.66.12.1
```

![alt text](images/tabella_aggionrata_statica.png)

**Vantaggi:**
- Permette la comunicazione con qualsiasi host esterno
- Funziona sia per Internet che per sottoreti locali (es. 128.66.1.3)

**Ottimizzazione:**
Per evitare ripetuti messaggi ICMP Redirect, è consigliabile specificare esplicitamente le route per ogni sottorete usando il comando `route`.

**Persistenza:**
I dati della tabella di routing vengono persi ad ogni reboot. Per renderli persistenti, inserire i comandi `route` nello script `/etc/rc.local`.

---

## Protocolli di Routing

I router si dividono in due categorie principali:

- **IGP (Interior Gateway Protocol)** → Instradano pacchetti internamente allo stesso AS
- **EGP (Exterior Gateway Protocol)** → Scambiano messaggi anche tra AS diversi

![alt text](images/routing_protocols.png)

---

### RIP (Routing Information Protocol)

Protocollo di routing dinamico che utilizza il daemon `routed`.

**Avvio del daemon:**
```bash
# routed
```

**Opzione `-q` (quiet mode):**
```bash
# routed -q
```
- Utilizzata quando il computer **non è un gateway**
- Previene l'invio di informazioni di routing ad altri sistemi
- Il sistema riceve solo le route consigliate da altri sistemi

**Caratteristiche:**
- Protocollo distance-vector
- Usa il numero di hop come metrica
- Limite massimo di 15 hop
- Convergenza lenta

---

### OSPF (Open Shortest Path First)

Sviluppato nel 1988 dall'IETF, è diventato standard nel 1990 per il routing all'interno di un AS.

**Vantaggi principali:**
- **Aperto** → Standard pubblico, non proprietario
- **Supporta subnet variabili** → Classless routing (VLSM)
- **Routing dinamico** → Si adatta rapidamente ai cambiamenti di topologia
- **Routing basato sul tipo di servizio** → QoS
- **Bilanciamento del carico** → Equal-cost multipath
- **Supporta sistemi gerarchici** → Organizzazione in aree

**Caratteristiche tecniche:**
- Protocollo link-state
- Convergenza rapida
- Minore overhead di banda rispetto a RIP
- Più complesso da configurare

---

### EGP (Exterior Gateway Protocol)

Protocollo per lo scambio di informazioni di routing **tra** Autonomous System diversi.

**Messaggi principali:**
- **HELLO** e **I-HEARD-YOU** → Stabiliscono e mantengono connessioni tra router EGP

**Implementazioni:**
1. **EGP User Process (egpup)** → Processo separato
2. **Gateway Routing Daemon (gated)** → Integrato nel daemon gated (**sempre preferibile**)

### Configurazione EGP (egpup)

Quando egpup viene avviato, legge un file di inizializzazione/configurazione con i seguenti parametri:

- **autonomoussystem asn** → Numero dell'Autonomous System
- **egpneighbour neighbour** → Hostname o IP del vicino EGP
- **egpmaxacquire number** → Numero massimo di vicini
- **net destination gateway address metric number** → Installa una route statica
- **egpnetsreachable net1...** → Definisce le reti da annunciare come raggiungibili ai propri vicini
- **defaultgateway address** → Installa una default route attiva

---

### BGP (Border Gateway Protocol)

Protocollo moderno utilizzato per la comunicazione tra Autonomous System.

**Caratteristiche:**
- Basato su algoritmo **path-vector** (evoluzione del distance-vector)
- Si occupa del transito di dati di terze parti attraverso una rete
- Supporta routing basato su policy

**Classificazione delle reti:**
- **Reti stub** → Unica connessione al grafo BGP (reti "foglia")
- **Reti multiconnesse** → Connessioni multiple ma **non** usate per traffico in transito
- **Reti di transito** → Spesso usate per trasportare traffico di terze parti (tipicamente reti backbone)

**Versioni:**
- BGP-4 è la versione attuale e supporta CIDR (Classless Inter-Domain Routing)

---

### Gateway Routing Daemon (gated)

**gated** è un pacchetto software unificato che combina:
- RIP
- Hello
- EGP
- BGP

**Vantaggi:**
- Compatibilità con le implementazioni standard di ciascun protocollo
- Configurazione centralizzata in un unico file
- Selezione intelligente delle route migliori

**Funzionamento:**
1. Elabora le informazioni ricevute dai vari protocolli di routing
2. Seleziona la route migliore in base alle policy configurate
3. Le route apprese tramite protocolli Interior vengono annunciate con protocolli Exterior

**Tabelle di metriche:**
- **Routing metric table** → Usata quando gated comunica route ad altri router
- **Preference table** → Usata quando gated riceve consigli da altri router per decidere quali preferire

---

# PDF_6

## Gateway Routing Daemon (gated) - Approfondimento

### Logica di funzionamento

gated gestisce in modo intelligente le informazioni provenienti da diversi protocolli di routing:

1. **Elaborazione** → Processa le informazioni ricevute dai vari protocolli
2. **Selezione** → Sceglie la route migliore utilizzando le tabelle di metrica e preferenza
3. **Annuncio** → Le route apprese tramite protocolli Interior (IGP) vengono redistribuite tramite protocolli Exterior (EGP)

### Tabelle di decisione

**Routing Metric Table:**
- Utilizzata quando gated **comunica** una route ad altri router
- Ogni protocollo ha valori di metrica specifici

**Preference Table:**
- Utilizzata quando gated **riceve** consigli da altri router
- Determina quale protocollo è più affidabile/preferibile
- Valori più bassi indicano maggiore preferenza

---

## Configurazione di gated

La sintassi del file di configurazione di gated (`/etc/gated.conf`) è simile al linguaggio C.

### Struttura del file di configurazione

Il file si divide in **6 sezioni** principali:

1. **Comandi di definizione** → Definiscono variabili e costanti
2. **Comandi di protocollo** → Configurano i protocolli di routing (RIP, OSPF, BGP, ecc.)
3. **Comandi statici** → Definiscono route statiche
4. **Comandi di controllo** → Gestiscono import/export di route e policy di routing
5. **Comandi di direttive** → Opzioni generali di comportamento
6. **Comandi di trace** → Configurano il logging e il debugging

**Sintassi:**
- Simile al C: istruzioni terminate con `;`
- Commenti supportati: `#`, `//`, `/* */`
- Struttura a blocchi con parentesi graffe `{}`

---

# PDF_PARTE_FINALE

## DNS: BIND (Berkeley Internet Name Domain)

BIND è un sistema software client/server per la risoluzione dei nomi di dominio.

### Componenti di BIND

**Resolver (Client):**
- Parte client di BIND
- Gestisce le query per le informazioni sui domain name
- Invia le richieste al server DNS

**named (Server):**
- Demone server di BIND
- Risponde alle query DNS
- Mantiene i database delle zone

---

## Configurazione di BIND

### Configurazione del Resolver

Il resolver è implementato come **libreria di sistema**. Alcuni sistemi possono utilizzare solo il resolver senza eseguire un name server locale.

#### Resolver-Only System

Sistemi che non eseguono il server DNS locale (configurazione inusuale a causa delle limitazioni tecniche).

**Configurazione:** File `/etc/resolv.conf`

#### Tipi di Name Server

**Caching-Only Server:**
- Delega le query ad altri server
- Mantiene una cache locale dei risultati (lookup recenti)
- Riduce il traffico di rete e migliora le prestazioni

**Authoritative Name Server:**
- Contengono informazioni complete su una o più zone
- Forniscono fault tolerance
- Possono essere di tre tipi:
  - **Primary Master** → Server principale con database master della zona
  - **Slave Servers** → Server secondari che sincronizzano i dati dal master
  - **Stealth Server** → Server autoritativi non elencati nei record NS della zona

---

## Configurazione del Resolver

### Due modalità di configurazione

#### 1. Configurazione di default

- Utilizza `localhost` come name server predefinito
- Il domain name viene ricavato dalla stringa restituita dal comando `hostname`, rimuovendo la parte prima del primo punto

**Verifica hostname:**
```bash
hostname
```

#### 2. Configurazione personalizzata (consigliata)

Creazione del file `/etc/resolv.conf` con configurazione personalizzata.

**Vantaggi:**
- Possibilità di definire server DNS di backup
- Maggiore controllo sulla risoluzione dei nomi
- Failover automatico in caso di problemi con il server primario

### Comandi principali in resolv.conf

**nameserver address:**
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
- Identifica tramite IP il server DNS da contattare
- I server vengono contattati nell'ordine specificato
- Si possono specificare fino a 3 nameserver

**domain name:**
```
domain example.com
```
- Definisce il nome del dominio di default
- Utilizzato per completare hostname non completi (FQDN)

**Esempio completo:**
```
domain azienda.local
nameserver 192.168.1.1
nameserver 8.8.8.8
```

---

## Configurazione del Server named

### File named.conf

`/etc/named.conf` è l'**unico file di configurazione** del demone named.

**Contenuto:**
- Impostazioni globali del server
- Indicazioni sulle varie zone del dominio servito
- Riferimenti ai Zone Files

**Zone Files:**
- Contengono informazioni per la risoluzione dei domini della rispettiva zona
- Creati dall'amministratore
- Permettono di mantenere una struttura gerarchica organizzata per zone

---

### Sintassi del file named.conf

La sintassi è simile al linguaggio C:

- Istruzioni terminate con `;`
- Commenti con `#`, `//` o `/* */`
- Struttura a blocchi con `{}`

### Direttive principali

**acl (Access Control List):**
```
acl acl-name {
    address_match_list;
};
```
- Definisce liste di controllo accesso
- Utile per limitare query e trasferimenti di zona

**include:**
```
include "/etc/named/zones.conf";
```
- Include il contenuto di un file esterno nel punto specificato
- Utile per organizzare configurazioni complesse

**options:**
```
options {
    directory "/var/named";
    forwarders { 8.8.8.8; };
};
```
- Definisce impostazioni globali del server
- Directory di lavoro, forwarders, cache, ecc.

**zone:**
```
zone "example.com" {
    type master;
    file "example.com.zone";
};
```
- Opzioni per le zone servite
- Indica i file di database per la risoluzione
- Specifica il tipo di zona (master, slave, hint)

---

## Configurazione Name Server Caching-Only

Un server caching-only è la configurazione più semplice:
- Non ha autorità su alcuna zona
- Inoltra tutte le query ad altri server DNS
- Mantiene una cache locale dei risultati

**Vantaggi:**
- Riduce il traffico di rete verso server esterni
- Migliora i tempi di risposta per query ripetute
- Facile da configurare e mantenere

**Esempio di configurazione:** [Riferimento righe 14-17 del documento originale]

---

## Standard Resource Records (RR)

Formato standard per le informazioni dei domini nei database DNS.

### Tipi di Resource Record

| Tipo | Nome completo | Descrizione |
|------|---------------|-------------|
| **SOA** | Start of Authority | Inizio di una zona e parametri che la governano |
| **NS** | Name Server | Nome del server DNS autoritativo per il dominio |
| **A** | Address | Converte hostname in indirizzo IPv4 |
| **AAAA** | IPv6 Address | Converte hostname in indirizzo IPv6 |
| **PTR** | Pointer | Converte indirizzo IP in hostname (reverse DNS) |
| **MX** | Mail Exchange | Specifica dove indirizzare la posta per un dominio |
| **CNAME** | Canonical Name | Alias per un hostname |
| **HINFO** | Host Info | Hardware e sistema operativo di un host |
| **WKS** | Well Known Service | Annunci di servizi di rete disponibili |

---

### Struttura generale dei Resource Record

```
[name] [ttl] IN type data
```

**Campi:**
- **name** → Dominio a cui si riferisce il record (può essere omesso per usare il precedente)
- **ttl** → Time To Live (secondi di validità della cache)
- **IN** → Identifica il record come Internet DNS Resource Record
- **type** → Tipo di record (vedi tabella sopra)
- **data** → Dati specifici in base al tipo di record

**Esempio:**
```
www     3600    IN  A       192.168.1.10
mail    3600    IN  A       192.168.1.20
@       3600    IN  MX  10  mail.example.com.
```

---

## Record Start of Authority (SOA)

Il record SOA definisce i parametri fondamentali di una zona DNS.

### Sintassi

```
[zone] [ttl] IN SOA origin contact (
    serial      ; Numero di versione del zone file
    refresh     ; Tempo di attesa del server secondario prima del refresh
    retry       ; Tempo di attesa prima di riprovare dopo un refresh fallito
    expire      ; Tempo dopo il quale i dati non sono più validi
    minimum     ; TTL di default per i record nella zona
)
```

**Parametri:**
- **zone** → Nome del dominio dichiarato (spesso `@` per riferirsi al dominio corrente)
- **origin** → Hostname del server DNS primario
- **contact** → Indirizzo email del responsabile del dominio (il `@` è sostituito con `.`)
- **serial** → Numero di versione del file (formato comune: YYYYMMDDNN)
- **refresh** → Intervallo (in secondi) dopo il quale i server slave controllano aggiornamenti
- **retry** → Intervallo (in secondi) di riprova in caso di fallimento del refresh
- **expire** → Tempo (in secondi) dopo il quale i dati devono essere considerati obsoleti
- **minimum** → TTL predefinito per tutti i record della zona

**Esempio pratico:**
```
@   IN  SOA ns1.example.com. admin.example.com. (
            2024120901  ; Serial (YYYYMMDDNN)
            3600        ; Refresh (1 ora)
            1800        ; Retry (30 minuti)
            604800      ; Expire (1 settimana)
            86400       ; Minimum TTL (1 giorno)
        )
```

---

## Configurazione Authoritative Name Server

Un server DNS autoritativo contiene i dati master per una o più zone.

**Configurazione base:** [Riferimento righe 27-29 del documento originale]

**Componenti necessari:**
1. File `named.conf` con definizione delle zone
2. Zone file per ciascuna zona autoritativa
3. File di reverse mapping (per conversione IP → hostname)

---

## Map Files (Zone Files)

I map files contengono i record DNS per una specifica zona.

**Contenuto tipico:**
- Record SOA
- Record NS (name server)
- Record A (indirizzi host)
- Record MX (mail exchanger)
- Record CNAME (alias)
- Altri record specifici

**Esempio:** [Riferimento righe 30-32 del documento originale]

---

## File di Reverse Domain (Reverse DNS)

I file di reverse domain permettono la conversione inversa: da indirizzo IP a hostname.

### Struttura

Ha una struttura analoga al file `named.local`, entrambi convertono indirizzi IP in hostname usando **record PTR**.

### Dominio in-addr.arpa

**Struttura analoga a `named.local`**, converte IP in hostname.

**Esempio `192.168.1.rev`:**
```
$TTL 86400
@   IN  SOA ns1.example.com. admin.example.com. (
            2024121001 3600 900 604800 86400 )
    IN  NS  ns1.example.com.

10  IN  PTR ns1.example.com.
11  IN  PTR ns2.example.com.
20  IN  PTR mail.example.com.
30  IN  PTR www.example.com.
```

**Nota:** Gli indirizzi sono scritti al contrario:
- Host `192.168.1.15` diventa `15.1.168.192.in-addr.arpa`

### Comando `nslookup`

**Uso base:**
```bash
nslookup hostname              # Query semplice
nslookup hostname dns-server   # Query a server specifico
```

**Modalità interattiva:**
```bash
nslookup
> server 8.8.8.8               # Imposta server
> set type=MX                  # Tipo di record
> example.com                  # Esegui query
> set domain=example.com       # Dominio di default
> ls example.com               # Elenca zona (se permesso)
> view filename                # Visualizza file
> exit
```

**Tipi di query:**
```bash
set type=A        # Address record (default)
set type=NS       # Name server
set type=MX       # Mail exchange
set type=CNAME    # Canonical name
set type=SOA      # Start of authority
set type=ANY      # Tutti i record
```

---

## Servizi di Rete Unix

### Servizi senza configurazione

Alcuni servizi funzionano immediatamente:
- **telnet:** Login remoto
- **ftp:** Trasferimento file

### Comandi "r" (Remote Commands)

**Suite di comandi:**
- `rlogin`: Remote login
- `rcp`: Remote copy (copia file)
- `rsh`: Remote shell (esecuzione comandi)

**Caratteristica principale:** Possono operare **senza richiesta password** se configurati correttamente.

#### Disabilitare i comandi r

**Metodo 1 - Commentare in `/etc/inetd.conf`:**
```bash
#login  stream  tcp  nowait  root  /usr/sbin/in.rlogind  in.rlogind
#shell  stream  tcp  nowait  root  /usr/sbin/in.rshd     in.rshd
```

**Metodo 2 - Richiedere sempre password:**
Cancellare il file `/etc/hosts.equiv`

### Concetti di Trusted Host e User

**Terminologia:**
- **Trusted Host:** Host considerati sicuri
- **Trusted User:** Utenti che possono accedere senza password
- **Equivalent Host:** Sinonimo di trusted host

**File di configurazione:**
1. `/etc/hosts.equiv`: Sistema globale
2. `~/.rhosts`: Per singolo utente

#### File `/etc/hosts.equiv`

**Sintassi:**
```
[+|-][hostname] [username]
```

**Esempi:**
```bash
server1.example.com           # Tutti gli utenti di server1 sono trusted
server2.example.com bob       # Solo bob di server2 è trusted
+ alice                       # alice da qualsiasi host è trusted
-badhost.example.com          # badhost sempre richiede password
+                             # PERICOLOSO: tutti gli host trusted
```

**Simboli:**
- `+` da solo = qualsiasi host (sconsigliato per sicurezza)
- `-` = forza richiesta password
- Specificare username = solo quell'utente è trusted

#### File `~/.rhosts`

**Sintassi:**
```
hostname username
```

**Esempio:**
```bash
server1.example.com alice
workstation.local bob
```

**Significato:**
- L'utente locale può essere accessibile da `alice@server1.example.com` e `bob@workstation.local` senza password
- Permette accesso anche quando `/etc/hosts.equiv` non esiste

### Accesso di root

**Regole speciali per root:**

| Utente | Controlla `/etc/hosts.equiv` | Controlla `~/.rhosts` |
|--------|------------------------------|----------------------|
| Normale | ✓ Sì | ✓ Sì |
| root | ✗ No | ✓ Sì (solo `/.rhosts`) |

**Sicurezza:** Root viene controllato solo tramite `/.rhosts` per maggiore sicurezza, ignorando `/etc/hosts.equiv`.

---

## Riepilogo dei File di Configurazione

| File | Scopo |
|------|-------|
| `/etc/inetd.conf` | Configurazione super daemon |
| `/etc/hosts` | Risoluzione statica hostname |
| `/etc/resolv.conf` | Configurazione DNS resolver |
| `/etc/named.conf` | Configurazione server DNS |
| `/etc/rc.local` | Script avvio sistema (BSD) |
| `/etc/init.d/tcp` | Script avvio rete (System V) |
| `/etc/hosts.equiv` | Trusted host globali |
| `~/.rhosts` | Trusted host per utente |

---

## Best Practices

### Sicurezza
1. **Non usare `+` in `hosts.equiv`** (apre a tutti gli host)
2. **Limitare permessi `.rhosts`:** `chmod 600 ~/.rhosts`
3. **Evitare comandi r se possibile:** Preferire SSH
4. **Usare firewall** per limitare accesso ai servizi

### DNS
1. **Incrementare serial** ad ogni modifica zone file
2. **Usare slave server** per ridondanza
3. **Configurare reverse DNS** per tutti gli host
4. **Monitorare log named** per errori

### Routing
1. **Documentare route statiche** in `/etc/rc.local`
2. **Usare routing dinamico** su reti complesse
3. **Verificare tabelle routing:** `netstat -rn`
4. **Monitorare ICMP redirect** per trovare errori configurazione