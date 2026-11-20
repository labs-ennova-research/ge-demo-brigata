# Manuale di Uso e Manutenzione — Cella Robotizzata LFAM `Heron-X 400` (Rev. 3.1)

**Unità di Estrusione:** Testa `HF-Pro 60` · **Destinatari:** Operatori qualificati e supporto tecnico di Primo Livello (L1).
*Documento tecnico fittizio ad uso didattico. Seguire rigorosamente ogni procedura nell'ordine indicato. Per qualsiasi codice allarme o operazione non documentata in questo manuale, arrestare la macchina in sicurezza e richiedere l'escalation al Secondo Livello (`ingegneria.l2@lfam-demo.example`).*

---

## Capitolo 1 · Dati Tecnici di Targa e Limiti Operativi

### Sezione 1.1 — Specifiche Principali
- **Volume massimo di stampa:** `4000 × 2000 × 1500 mm` (L × P × H) su piano fisso con tavola rotante asse esterno `E1`.
- **Testa di estrusione `HF-Pro 60`:** vite bimetallica Ø45 mm, portata massima `45 kg/h`, ugello standard temprato Ø6 mm (`RIC-HX-NOZ06`).
- **Temperatura massima di esercizio ugello e testa:** **`320 °C`** (soglia di blocco automatico hardware a `325 °C`).
- **Pressione massima nominale melt:** `180 bar` (soglia allarme `190 bar`).

### Sezione 1.2 — Requisiti di Alimentazione
- **Alimentazione elettrica:** `400V AC trifase + N + PE`, `50 Hz`, potenza installata `45 kW` (protezione a monte `80 A`).
- **Aria compressa (caricatore pneumatico e pulizia filtri):** `6,0 – 7,5 bar`, aria filtrata e deumidificata.
- **Circuito raffreddamento (Chiller acqua-glicole 25%):** temperatura mandata `20 °C ± 2 °C`, portata minima sul riduttore `5,0 l/min`, pressione `1,8 – 2,5 bar`, valvola gola di carico regolata a `2,5 l/min`.

### Sezione 1.3 — Limiti Operativi e Materiali Non Ammessi
- **DIVIETO TERMICO:** È vietato impostare setpoint superiori a **`320 °C`** o tentare l'estrusione di tecnopolimeri ad altissima temperatura (es. **PEEK, PEKK, PEI/ULTEM**) sulla testa `HF-Pro 60`: danneggiano irreversibilmente le fasce ceramiche e le tenute del cilindro.
- **DIVIETO MATERIALI NON CARICATI / ALIMENTARI:** La cella lavora esclusivamente polimeri termoplastici caricati in granulo certificati in Sezione 3.2. Non è certificata per materiali a contatto alimentare.

---

## Capitolo 2 · Norme di Sicurezza, DPI e Divieti Assoluti

### Sezione 2.1 — Dispositivi di Protezione Individuale (DPI) Obbligatori
Durante le operazioni di **spurgo manuale**, **pulizia ugello** e **smontaggio/serraggio ugello a caldo**, l'operatore deve indossare obbligatoriamente:
1. **Guanti antitaglio e antitermici** certificati **`EN 407 livello 4`** (resistenza al calore da contatto fino a `350 °C`);
2. **Visiera in policarbonato a schermo intero** (protezione da schizzi di polimero fuso);
3. **Calzature antinfortunistiche `S3`** e abbigliamento ignifugo a maniche lunghe.

### Sezione 2.2 — Divieti Assoluti di Sicurezza
1. **DIVIETO DI BYPASS SICUREZZE:** È **severamente vietato** ponticellare, disattivare o bypassare le barriere fotoelettriche perimetrali, i microinterruttori porta cabina o il fungo di emergenza per continuare la produzione in caso di guasto o allarme.
2. **SERRAGGIO UGELLO SOLO A CALDO:** È **vietato** svitare o serrare l'ugello `RIC-HX-NOZ06` a macchina fredda (rischio rottura filettatura testa). L'ugello va serrato **esclusivamente a caldo alla temperatura di `210 °C`** utilizzando una chiave dinamometrica tarata a **`45 Nm`**.
3. **PULIZIA UGELLO (SOLO OTTONE):** È **vietato** utilizzare spazzole in acciaio o raschietti metallici duri sull'orifizio dell'ugello (rigano il carburo e alterano il flusso). Utilizzare esclusivamente una **spazzola con setole in ottone**.
4. **OPERAZIONI RISERVATE A TECNICI L2:** Lo smontaggio del riduttore del robot, la sostituzione della vite bimetallica, la taratura del trasduttore `PT-MELT1` e la ricalibrazione laser TCP sono **vietati all'operatore L1** e riservati esclusivamente a tecnici certificati `L2`.

---

## Capitolo 3 · Avviamento, Parametri Materiali e Spegnimento (Purga Fine Turno)

### Sezione 3.1 — Procedura di Avviamento a Freddo
1. Accendere il chiller esterno e verificare che la portata su HMI sia `>= 5,0 l/min` e la pressione sia tra `1,8` e `2,5 bar`.
2. Attivare il riscaldamento zone (`Zona 1`, `Zona 2`, `Zona 3 / Ugello`) al setpoint del materiale caricato.
3. Una volta raggiunte le temperature su tutte e 3 le zone, attendere obbligatoriamente **`20 minuti` di stabilizzazione termica** (*soak time*) prima di abilitare la rotazione vite.
4. Eseguire uno spurgo iniziale di verifica a **`15 rpm`** in area di purga finché il cordolo non risulta continuo e privo di bolle.

### Sezione 3.2 — Tabella Parametri Materiali Certificati (`HF-Pro 60`)

| Materiale | Base Polimerica | Essiccazione Obbligatoria | Zona 1 | Zona 2 | Zona 3 / Ugello |
|---|---|---|---|---|---|
| **`CaraComp-GF30`** | PP + 30% fibra vetro | `80 °C` per `4 ore` | `205 °C` | `220 °C` | `235 °C` |
| **`CaraCarb-CF40`** | PA6 + 40% fibra carbonio | `90 °C` per `6 ore` | `255 °C` | `270 °C` | `285 °C` |
| **`PETG-GF20`** | PETG + 20% fibra vetro | `65 °C` per `4 ore` | `225 °C` | `240 °C` | `250 °C` |

### Sezione 3.3 — Procedura di Spegnimento e Purga di Fine Turno
1. Chiudere la serranda di alimentazione del polimero principale e caricare `2 kg` di compound di lavaggio **`Purge-PP`**.
2. Estrudere in area di purga a **`15 rpm` per `5 minuti`** fino a completa eliminazione del polimero caricato (soprattutto dopo `CaraCarb-CF40` per evitare carbonizzazioni).
3. Portare i giri vite a `0 rpm` e disattivare i riscaldatori (`HEAT OFF`).
4. **REGOLA CHILLER:** Non spegnere **MAI** il chiller finché tutte le zone della testa non sono scese **sotto gli `80 °C`** (lo spegnimento precoce surriscalda i cuscinetti del riduttore).

---

## Capitolo 4 · Piano di Manutenzione Preventiva Programmata

| Frequenza | Operazioni Obbligatorie | Ricambi / Materiali Ufficiali | Esecutore |
|---|---|---|---|
| **Giornaliera (ogni 8 h)** | Pulizia esterna ugello a caldo con **spazzola in ottone** (mai acciaio); pulizia vetrini barriere ottiche con panno microfibra; controllo visivo livello glicole chiller | Nessuno | Operatore L1 |
| **Ogni 250 ore** | Smontaggio e soffiaggio cartuccia filtro ciclone `RIC-HX-FLT02` con aria compressa a **max `2 bar`**; controllo integrità tubo flessibile granulo; verifica serraggio connettore polso `X42` | Eventuale `RIC-HX-FLT02` se danneggiata | Operatore L1 |
| **Ogni 1.000 ore** | Sostituzione delle **2 cartucce filtro ciclone** (`RIC-HX-FLT02`); pulizia retina metallica filtro a Y chiller; ingrassaggio guide tavola `E1` con grasso al litio **`NLGI-2`**; sostituzione guarnizioni piane ugello e **serraggio ugello a `45 Nm` alla temperatura di `210 °C`** | **`RIC-HX-KIT1000`** | Operatore L1 qualificato |
| **Ogni 2.500 ore** | Tutte le attività delle 1.000 ore + sostituzione preventiva fascia riscaldante Zona 1 (`RIC-HX-HT12`), sostituzione 3 termocoppie testa (`RIC-HX-TC04`), sostituzione cinghia asse tavola `E1` (`RIC-HX-CING1`) e verifica coppia/gioco riduttore | **`RIC-HX-KIT2500`** | **Tecnico L2 consigliato / obbligatorio per verifica riduttore** |

---

## Capitolo 5 · Tabella Allarmi e Troubleshooting Primo Livello (L1)

### Sezione 5.1 — Codici Allarme Serie `A200`

#### Allarme `A201` — Sottotemperatura Zona 1 (Alimentazione Granulo)
- **Descrizione:** Temperatura Zona 1 inferiore di oltre `15 °C` rispetto al setpoint per più di `90 secondi`.
- **Cause probabili:** (1) Fascia riscaldante Zona 1 interrotta o morsetto allentato; (2) Flusso eccessivo nel raffreddamento gola di carico (`> 2,5 l/min`).
- **Procedura di verifica L1:**
  1. Mettere la cella in `HOLD` e leggere su HMI la corrente assorbita dalla Zona 1 (valore nominale: **`5,5 A`**).
  2. Verificare che la valvola parzializzatrice acqua gola segni **`2,5 l/min`**.
  3. Se la corrente è `0,0 A`, togliere tensione al quadro potenza, attendere `10 minuti` e controllare il fusibile **`F12`**.
- **Quando scalare a Tecnico L2:** Se il fusibile `F12` interviene nuovamente al riavvio o la fascia risulta interrotta (ricambio: `RIC-HX-HT12`).

#### Allarme `A202` — Sovratemperatura Zona 3 / Ugello (`> 320 °C`)
- **Descrizione:** Temperatura letta sull'ugello superiore a `320 °C` o salita incontrollata della temperatura.
- **Cause probabili:** (1) Modulo relè SSR Zona 3 bloccato in chiusura; (2) Guasto o schiacciamento termocoppia `TC3`.
- **Procedura di verifica L1:**
  1. Premere immediatamente **`HEAT OFF`** su pannello HMI.
  2. Verificare che la temperatura scenda entro `2 minuti` (mantenendo il chiller acceso!).
  3. A testa raffreddata sotto `60 °C`, ispezionare visivamente il cavo della termocoppia `TC3`.
- **Quando scalare a Tecnico L2:** Sempre se la temperatura non scende dopo `HEAT OFF` (ricambi: `RIC-HX-SSR30` o `RIC-HX-TC04`).

#### Allarme `A203` — Errore Lettura Termocoppia Testa (`TC-OPEN`)
- **Descrizione:** Segnale interrotto o instabile da una delle termocoppie della testa `HF-Pro 60`.
- **Cause probabili:** Connettore `TC-BUS` allentato sul polso robot o guasto sonda termocoppia.
- **Procedura di verifica L1:**
  1. Arrestare il ciclo di riscaldamento (`HEAT OFF`).
  2. Verificare il serraggio meccanico del connettore multipolare **`TC-BUS`** alla base della testa.
  3. Riavviare la diagnostica HMI e verificare la stabilità della lettura ambiente.
- **Quando scalare a Tecnico L2:** Se la lettura resta a `999 °C` o `0 °C` dopo il controllo connettore (ricambio: `RIC-HX-TC04`).

#### Allarme `A204` — Sovrapressione Melt (`> 190 bar`) o Coppia Vite Elevata (`> 90%`)
- **Descrizione:** Il trasduttore `PT-MELT1` supera `190 bar` oppure la coppia motore vite supera il `90%` per oltre `5 secondi`.
- **Cause probabili:** (1) Ugello parzialmente ostruito da materiale carbonizzato; (2) Soak time inferiore a `20 minuti` o temperatura melt bassa; (3) Staratura o guasto trasduttore `PT-MELT1`.
- **Procedura di verifica L1:**
  1. Fermare il robot e portare i giri vite a **`0 rpm`**.
  2. Mantenere i riscaldatori al setpoint per **`10 minuti`** (indossando i DPI della Sez. 2.1 se ci si avvicina alla testa).
  3. A vite ferma, leggere `PT-MELT1` su `Diagnostica -> Estrusore`: il valore deve scendere **sotto `5 bar`**. Se resta **sopra `20 bar` a vite ferma**, il trasduttore è guasto o starato.
  4. Se a vite ferma è `< 5 bar`, eseguire uno spurgo a **`15 rpm`** in area di purga verificando la fluidità del cordolo.
- **Quando scalare a Tecnico L2:** Se durante lo spurgo a `15 rpm` la coppia supera `85%`, oppure se `PT-MELT1` supera `20 bar` a vite ferma, **oppure se l'allarme `A204` si ripete 3 o più volte in un anno sulla stessa matricola** (ricambi: `RIC-HX-NOZ06` oppure `RIC-HX-PT250`).

#### Allarme `A205` — Mancanza Granulo Tramoggia (`> 60 s`)
- **Descrizione:** Il sensore capacitivo `S-LEV1` sulla tramoggia bordo testa non rileva granulo da oltre `60 secondi`.
- **Cause probabili:** (1) Big-bag vuoto; (2) Cartuccia filtro ciclone `RIC-HX-FLT02` intasata da polvere di fibra; (3) Lente sensore `S-LEV1` sporca.
- **Procedura di verifica L1:**
  1. Verificare il livello nel serbatoio/big-bag a terra.
  2. Smontare e soffiare la cartuccia filtro ciclone `RIC-HX-FLT02` con aria compressa a **max `2 bar`**.
  3. Pulire con panno asciutto la superficie del sensore capacitivo **`S-LEV1`**.
- **Quando scalare a Tecnico L2:** Se a tramoggia piena e filtro pulito l'ingresso `DI_08` su HMI resta a `0`.

#### Allarme `A206` — Scostamento Inseguimento Tavola Rotante `E1` (`> 1,2 mm`)
- **Descrizione:** Errore di posizionamento asse esterno `E1` superiore a `1,2 mm` durante l'interpolazione.
- **Cause probabili:** (1) Bave di polimero sulle guide prismatiche; (2) Allentamento o usura cinghia trasmissione `RIC-HX-CING1`.
- **Procedura di verifica L1:**
  1. Pulire accuratamente guide prismatiche e raschiaolio della tavola `E1`.
  2. Muovere l'asse `E1` in modalità **`JOG` al `10%`** e verificare l'assenza di impuntamenti o rumori anomali.
- **Quando scalare a Tecnico L2:** Se l'impuntamento o il rumore persiste a guide pulite (ricambio: `RIC-HX-CING1`).

---

### Sezione 5.2 — Sintomi Senza Codice di Allarme a Pannello

#### Sintomo `S-01` — Arresto Improvviso Vite Estrusore Senza Codice Allarme su HMI
- **Descrizione:** Il robot prosegue il percorso ma la vite si ferma a `0 rpm` senza alcun codice nella pagina Allarmi.
- **Cause probabili:** (1) Perdita segnale analogico `0–10 V` sul connettore `X42`; (2) Protezione termica silenziosa del drive per filtro ventola quadro intasato.
- **Procedura di verifica L1:**
  1. Mettere in pausa il programma e aprire `Diagnostica I/O -> Uscite Analogiche`.
  2. Verificare se l'uscita **`AO_01`** è `> 0 V` mentre il drive legge `0 rpm`.
  3. Rimuovere e soffiare il pannello filtrante della ventola quadro estrusore.
  4. Controllare il serraggio del connettore multipolare **`X42`** alla base del polso robot.
- **Quando scalare a Tecnico L2:** Se a filtro pulito e connettore `X42` serrato il fermo si ripete.
