# Manuale di Troubleshooting — Estrusori e Celle Robotizzate LFAM (Rev. 4.2)

Documento riservato agli operatori di supporto tecnico di Primo Livello (L1).
Seguire rigorosamente l'ordine dei controlli indicati. **Se un codice allarme non compare in questo manuale, non tentare procedure a intuito e procedere immediatamente con l'escalation al Secondo Livello (L2).**

---

## Sezione 1 · Codici Allarme Serie E100 (Gruppo Estrusione e Termoregolazione)

### Allarme `E101` — Sottotemperatura Zona 1 (Alimentazione Granulo)
- **Descrizione:** La temperatura della Zona 1 del cilindro di plastificazione è scesa di oltre 15 °C sotto il setpoint.
- **Cause probabili:**
  1. Fascia riscaldante Zona 1 interrotta o morsetto allentato.
  2. Flusso eccessivo di acqua nel circuito di raffreddamento gola di carico.
- **Procedura di verifica:**
  1. Mettere la macchina in stato `HOLD` e verificare a pannello HMI la corrente assorbita dalla Zona 1 (valore nominale: `4,2 A`).
  2. Controllare che la valvola parzializzatrice del circuito acqua gola sia regolata a `2,5 l/min`.
  3. Se la corrente letta è `0,0 A`, spegnere il quadro potenza, attendere 10 minuti e verificare il fusibile `F11` nel quadro bordo macchina.
- **Quando chiamare il tecnico (L2):** Se il fusibile `F11` salta nuovamente al riavvio o se la fascia riscaldante risulta in dispersione (ricambio ipotizzato: `Fascia riscaldante 800W cod. RIC-HT01`).

---

### Allarme `E102` — Sovratemperatura Zona 3 (Ugello)
- **Descrizione:** Temperatura letta sull'ugello superiore a 320 °C o incremento termico fuori controllo.
- **Cause probabili:**
  1. Relè allo stato solido (SSR) della Zona 3 bloccato in chiusura.
  2. Deriva o cortocircuito della termocoppia `TC3`.
- **Procedura di verifica:**
  1. Premere immediatamente il pulsante di arresto riscaldatori `HEAT OFF` su HMI.
  2. Osservare se la temperatura su `TC3` inizia a scendere entro 2 minuti.
  3. Verificare visivamente che il cavo della termocoppia `TC3` non sia schiacciato contro il blocco ugello.
- **Quando chiamare il tecnico (L2):** Sempre, se la temperatura non scende dopo `HEAT OFF` (richiede sostituzione `Modulo SSR 25A cod. RIC-SSR25` o `Termocoppia Tipo J cod. RIC-TC03`).

---

### Allarme `E103` — Mancanza Granulo in Tramoggia Essiccatore
- **Descrizione:** Il sensore capacitivo di livello minimo sulla tramoggia bordo testa non rileva materiale da oltre 60 secondi.
- **Cause probabili:**
  1. Big-bag o serbatoio principale esaurito.
  2. Filtro ciclone del caricatore pneumatico intasato da polvere di fibra.
  3. Lente del sensore capacitivo sporca di polvere elettrostatica.
- **Procedura di verifica:**
  1. Verificare il livello materiale nel serbatoio a terra.
  2. Aprire il coperchio ispezione del caricatore e pulire la cartuccia filtro con aria compressa a max `2 bar`.
  3. Pulire la superficie del sensore capacitivo `S-LEV1` con panno asciutto.
- **Quando chiamare il tecnico (L2):** Solo se, a tramoggia piena e sensore pulito, l'ingresso digitale `DI_08` su pagina diagnostica resta a `0`.

---

### Allarme `E104` — Sovrapressione Melt / Coppia Vite Estrusore Elevata
- **Descrizione:** Il trasduttore di pressione in testa supera `180 bar` oppure la coppia del servomotore vite supera il `92%` per più di 5 secondi.
- **Cause probabili:**
  1. Ostruzione parziale dell'ugello per corpo estraneo o materiale carbonizzato.
  2. Temperatura reale del melt troppo bassa per staratura della termocoppia ugello (`TC3`).
  3. Usura o cedimento del trasduttore di pressione `PT-MELT1`.
- **Procedura di verifica:**
  1. Arrestare il percorso robot e portare i giri vite a `0 rpm`.
  2. Mantenere i riscaldatori accesi al setpoint per 10 minuti per uniformare il calore in testa.
  3. A vite ferma, leggere il valore del sensore `PT-MELT1` su pagina diagnostica: deve scendere sotto `5 bar`. Se resta sopra `25 bar` a vite ferma, il trasduttore è starato o guasto.
  4. Se la pressione a vite ferma è corretta (`< 5 bar`), eseguire uno spurgo manuale a bassa velocità (`15 rpm`) in area di purga e verificare che il cordolo esca fluido e rettilineo.
- **Quando chiamare il tecnico (L2):** Se durante lo spurgo a `15 rpm` la coppia supera nuovamente l'`85%`, oppure se il trasduttore `PT-MELT1` segna più di `25 bar` a vite ferma (ricambi ipotizzati: `Ugello temprato cod. RIC-NOZ04` oppure `Trasduttore pressione melt 200bar cod. RIC-PT200`).

---

### Allarme `E105` — Anomalia Flusso Chiller Raffreddamento Riduttore
- **Descrizione:** Flusso liquido refrigerante sul riduttore estrusore inferiore a `4,0 l/min`.
- **Cause probabili:**
  1. Filtro a Y sulla linea di mandata chiller intasato.
  2. Livello glicole basso nella vasca del chiller esterno.
- **Procedura di verifica:**
  1. Controllare sul display del chiller che non vi siano allarmi attivi e che il manometro segni almeno `1,8 bar`.
  2. Chiudere le valvole di intercettazione, smontare e pulire la retina metallica del filtro a Y posto sul fianco sinistro della cella.
  3. Ripristinare il flusso e verificare che la portata su HMI torni sopra `5,5 l/min`.
- **Quando chiamare il tecnico (L2):** Se la pompa del chiller gira ma la pressione resta sotto `1,0 bar` dopo la pulizia del filtro.

---

### Allarme `E108` — Scostamento Inseguimento Asse Esterno (Tavola Rotante E1)
- **Descrizione:** Errore di posizione dell'asse esterno `E1` superiore a `1,5 mm` durante il movimento interpolato.
- **Cause probabili:**
  1. Accumulo di sfridi di fresatura o bave di polimero sulle guide prismatiche della tavola.
  2. Allentamento cinghia di trasmissione riduttore asse `E1`.
- **Procedura di verifica:**
  1. Eseguire una pulizia completa delle guide e dei raschiaolio della tavola rotante.
  2. Muovere l'asse `E1` in modalità JOG al 10% di velocità e verificare l'assenza di rumori anomali o impuntamenti.
- **Quando chiamare il tecnico (L2):** Se il rumore meccanico persiste a guide pulite (necessaria verifica precarico pignone/cremagliera).

---

### Allarme `E110` — Intervento Barriera Ottica Sicurezza Cabina
- **Descrizione:** Interruzione del fascio delle barriere fotoelettriche perimetrali durante il ciclo automatico.
- **Cause probabili:**
  1. Ingresso operatore in area presidiata senza richiesta di accesso porta.
  2. Polvere o trucioli depositati sulle colonnine ottiche TX/RX.
- **Procedura di verifica:**
  1. Verificare che nessuno si trovi all'interno del perimetro cella.
  2. Pulire i vetrini delle colonnine ottiche con panno in microfibra.
  3. Premere il pulsante blu `RESET BARRIERE` esterno cella e poi `ACK` su HMI.
- **Quando chiamare il tecnico (L2):** Se i LED rossi `OSSDs OFF` sulla barriera restano accesi fissi anche ad area sgombra e lenti pulite.

---

## Sezione 2 · Sintomi Senza Codice di Allarme a Pannello

### Sintomo `S-01` — L'estrusore si ferma a metà stampa senza alcun codice di allarme su HMI
- **Descrizione del fenomeno:** Il robot continua a muoversi lungo la traiettoria di stampa ma la vite dell'estrusore si arresta improvvisamente senza generare fault nella pagina Allarmi.
- **Cause probabili:**
  1. Perdita temporanea del segnale di consenso analogico `0–10 V` tra controller robot e inverter estrusore (morsettiera `X42`).
  2. Attivazione silenziosa della soglia di protezione termica interna del drive estrusore per filtro ventola quadro intasato.
- **Procedura di verifica:**
  1. Mettere in pausa il programma robot e aprire la pagina `Diagnostica I/O -> Uscite Analogiche`.
  2. Verificare se l'uscita `AO_01 (Riferimento velocità vite)` mostra un valore maggiore di `0 V` mentre il drive segna `0 rpm`.
  3. Controllare il filtro ventola sulla portella del quadro elettrico estrusore: se ostruito da polvere di lavorazione, rimuovere e soffiare il pannello filtrante.
  4. Verificare il serraggio del connettore multipolare `X42` alla base del polso robot.
- **Quando chiamare il tecnico (L2):** Se il filtro quadro è pulito e il connettore `X42` è ben serrato ma l'arresto si ripresenta (necessaria sostituzione `Cavo ibrido polso robot cod. RIC-CAB42`).
