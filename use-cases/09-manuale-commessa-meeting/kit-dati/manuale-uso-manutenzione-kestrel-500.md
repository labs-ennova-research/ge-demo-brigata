# Manuale di Uso e Manutenzione — Centro Robotizzato Ibrido `Kestrel-500 Hybrid` (Rev. 2.4)

**Configurazione:** Testa di Estrusione Alta Temperatura `HT-380` + Elettromandrino CNC 5 Assi `KM-18` (18 kW).
*Documento tecnico fittizio ad uso didattico. Ogni installazione, manovra operativa o risposta tecnica al cliente deve attenersi rigorosamente a questo manuale. Per codici allarme o lavorazioni non documentate, scalare all'Ingegneria L2 (`luca.visconti@lfam-demo.example` / `sara.fontana@lfam-demo.example`).*

---

## Capitolo 1 · Specifiche Macchina e Requisiti Obbligatori del Sito di Installazione

### Sezione 1.1 — Dati Tecnici Principali
- **Area utile di lavoro (stampa + fresatura 5 assi):** `5000 × 2500 × 1800 mm`.
- **Massa complessiva della cella (inclusa cabina e basamento):** `14.200 kg`.
- **Testa di estrusione `HT-380`:** temperatura massima continua **`360 °C`** (blocco hardware `365 °C`), portata massima `38 kg/h`.
- **Elettromandrino CNC `KM-18`:** potenza `18 kW`, attacco utensile **`HSK-63F`**, velocità massima **`18.000 rpm`**, raffreddamento a liquido dedicato (`22 °C ± 1 °C`).

### Sezione 1.2 — Requisiti Vincolanti del Sito di Installazione
Prima di posizionare la cella `Kestrel-500 Hybrid`, il sito del cliente deve soddisfare **tutti** i seguenti requisiti certificati:
1. **Pavimentazione industriale:** portata certificata minima **`3.500 kg/m²`**, planarità `<= 3 mm` su `2 m`.
   - **VINCOLO DI INSTALLAZIONE:** se la portata del pavimento è inferiore a `3.500 kg/m²`, l'installazione è **VIETATA** salvo progettazione e posa di una **piastra di ripartizione del carico** (o rinforzo soletta) certificata da ingegnere strutturista abilitato.
2. **Alimentazione elettrica:** `400V AC trifase + N + PE`, `50 Hz`, protezione dedicata **`63 A`**, potenza assorbita `42 kW`.
3. **Impianto aria compressa:** pressione di linea **`6,5 – 8,0 bar`**, aria filtrata ed essiccata con certificazione **`ISO 8573-1 Classe 4`** (punto di rugiada in pressione **`<= +3 °C`**). Umidità o olio nell'aria danneggiano il cambio testa automatico e i cuscinetti pneumatici del cono `HSK-63F`.
4. **Impianto di aspirazione polveri CNC:** portata minima **`2.200 m³/h`** con cartucce di filtrazione certificate **`HEPA H13`** idonee alla cattura di polveri fini di fibra di carbonio e vetro.

---

## Capitolo 2 · Sicurezza, Cambio Testa Automatico e Lavorazioni Vietate

### Sezione 2.1 — Sicurezza e DPI Obbligatori
- Il cambio testa automatico (`HT-380` ↔ `KM-18`) è ammesso **esclusivamente** in posizione parcheggio `HOME-PARK`, a porte cabina chiuse e interbloccate e con pressione aria blocco cono **`>= 6,5 bar`**.
- **DPI obbligatori** durante cambio utensile fresatura, pulizia cabina e sostituzione filtri polveri:
  1. **Guanti antitaglio `EN 388 livello D`** (maneggio frese carburo);
  2. **Occhiali a tenuta chiusa anti-polvere**;
  3. **Maschera filtrante `FFP3`** obbligatoria ogni volta che si manipolano o aspirano polveri di fibra di carbonio.

### Sezione 2.2 — Lavorazioni, Materiali e Pratiche ESPRESSAMENTE VIETATE
1. **DIVIETO FRESATURA METALLI (INCLUSO ALLUMINIO):** È **severamente vietato** fresare materiali metallici — incluse **leghe di alluminio**, acciaio, ottone o titanio — sull'elettromandrino `KM-18`. La cella è progettata esclusivamente per polimeri termoplastici caricati e materiali compositi non metallici: la fresatura di metalli provoca grippaggio dei cuscinetti ceramici del mandrino e rischio di innesco incendio nelle condotte di aspirazione polveri.
2. **DIVIETO TEMPERATURE > `360 °C`:** È **vietato** estrudere polimeri che richiedono temperature superiori a **`360 °C`** (come `PEEK` puro a `390–400 °C`).
3. **DIVIETO SOFFIAGGIO POLVERI CON ARIA COMPRESSA:** È **severamente vietato** utilizzare pistole ad aria compressa libera per pulire la cabina o il pezzo dalle polveri di fibra di carbonio: le microfibre di carbonio sono **elettricamente conduttive**, penetrano negli azionamenti e causano cortocircuiti nei quadri elettrici. Utilizzare **esclusivamente un aspiratore industriale certificato `ATEX / HEPA H13`**.

---

## Capitolo 3 · Setup Operativo, Mandrino CNC e Calibrazione

### Sezione 3.1 — Ciclo di Warm-up Obbligatorio Mandrino `KM-18`
Dopo ogni fermo superiore a `4 ore`, prima di avviare qualsiasi fresatura di precisione, eseguire il ciclo automatico di riscaldamento cuscinetti (**durata `15 minuti`**):
1. `5 minuti` a **`3.000 rpm`**;
2. `5 minuti` a **`8.000 rpm`**;
3. `5 minuti` a **`14.000 rpm`**.

### Sezione 3.2 — Attacco Utensili `HSK-63F` e Tastatore `TP-OPT1`
- Prima di ogni montaggio pulire il cono `HSK-63F` con panno privo di pelucchi e verificare che la forza del tirante sia **`>= 18 kN`**.
- **Azzeramento pezzo:** eseguire tramite tastatore ottico **`TP-OPT1`** (ripetibilità nominale `± 0,08 mm`).
- **Compensazione termica e riallineamento laser assi:** operazione **riservata esclusivamente a Tecnici L2** mediante interferometro laser certificato (vietata all'operatore di linea).

---

## Capitolo 4 · Piano di Manutenzione Preventiva Programmata

| Frequenza | Operazioni Obbligatorie | Ricambi / Kit Ufficiali | Esecutore |
|---|---|---|---|
| **Fine turno (ogni 8 h)** | Aspirazione completa cabina e piano con aspiratore **`ATEX / HEPA H13`** *(mai aria compressa!)*; pulizia cono `HSK-63F`; scarico manuale trappola condensa gruppo FRL aria compressa | Nessuno | Operatore L1 |
| **Ogni 500 ore** | Sostituzione cartuccia filtro aspirazione **`HEPA H13`** (`RIC-K5-HEPA`, indossando maschera `FFP3`); sostituzione cartuccia disoleatore linea aria (`RIC-K5-AIR4`); controllo forza tirante `HSK-63F` (`>= 18 kN`); verifica livello olio centralina lubrificazione guide | **`RIC-K5-KIT500`** | Operatore L1 qualificato |
| **Ogni 2.000 ore** | Tutto il tagliando 500 h + revisione guarnizioni rotanti elettromandrino `KM-18`, controllo stato cuscinetti ceramici (`RIC-K5-BRG18`), sostituzione tubo essiccatore (`RIC-K5-TUB8`) e taratura certificata tastatore `TP-OPT1` | **`RIC-K5-KIT2000`** | **Tecnico L2 obbligatorio** |

---

## Capitolo 5 · Diagnostica Errori e Allarmi Principali (`K401`–`K406`)

### Allarme `K401` — Mancato Aggancio Cono `HSK-63F`
- **Cause:** Pressione aria blocco cono `< 6,5 bar`, trucioli sul cono o sensore finecorsa `S-HSK2` sporco.
- **Procedura L1:** Verificare pressione su manometro FRL (`>= 6,5 bar`), pulire il cono con panno privo di pelucchi, controllare il segnale `S-HSK2` su pagina diagnostica. Se persiste → escalare a L2.

### Allarme `K402` — Sovratemperatura Cuscinetti Elettromandrino `KM-18` (`> 65 °C`)
- **Cause:** Anomalia chiller mandrino (`22 °C`) o usura cuscinetti ceramici.
- **Procedura L1:** Arrestare immediatamente la fresatura, verificare la temperatura di mandata chiller (`22 °C ± 1 °C`) e l'assenza di allarmi portata. **Escalation obbligatoria a Tecnico L2** prima di riprendere la lavorazione (ricambio ipotizzato: `RIC-K5-BRG18`).

### Allarme `K403` — Intasamento Filtro Aspirazione `HEPA H13` (`ΔP > 1.200 Pa`)
- **Cause:** Cartuccia `RIC-K5-HEPA` satura di polveri di fibra carbonio/vetro.
- **Procedura L1:** Arrestare l'aspiratore, indossare **maschera `FFP3`, occhiali chiusi e guanti `EN 388 liv. D`**, sostituire la cartuccia `RIC-K5-HEPA` e azzerare il contaore filtro su HMI.

### Allarme `K404` — Calo Pressione Linea Aria Compressa (`< 6,2 bar`)
- **Cause:** Calo di rete stabilimento, condensa accumulata nel gruppo FRL o taratura bassa del pressostato `PS-AIR1`.
- **Procedura L1:**
  1. Verificare che la linea stabilimento eroghi almeno `6,5 bar` stabili.
  2. Scaricare la tazza condensa del gruppo FRL e verificare che non vi siano tracce di olio (altrimenti sostituire `RIC-K5-AIR4`).
  3. Controllare su HMI la soglia del pressostato **`PS-AIR1`** (valore nominale di taratura: **`6,8 bar`**).
- **Escalation L2:** Se la pressione a monte è stabile (`>= 7,0 bar`) ma l'allarme persiste o il pressostato `PS-AIR1` richiede ritaratura.

### Allarme `K405` — Sovratemperatura Testa Estrusione `HT-380` (`> 360 °C`)
- **Cause:** Setpoint errato oltre limite o guasto termocoppia `TC-HT3`.
- **Procedura L1:** Premere immediatamente **`HEAT OFF`**, verificare il profilo materiale caricato (nessun polimero oltre `360 °C`), ispezionare il cavo `TC-HT3` a testa fredda. Se la temperatura non cala in `2 minuti` → escalare a L2.

### Allarme `K406` — Errore Segnale Tastatore Ottico `TP-OPT1`
- **Cause:** Finestra ottica sporca di polvere composita o batteria scarica.
- **Procedura L1:** Pulire la finestra ottica del ricevitore e del tastatore con alcool isopropilico e panno morbido; se il LED rosso lampeggia, sostituire la batteria al litio `3,6V` cod. **`RIC-K5-BAT1`**.
