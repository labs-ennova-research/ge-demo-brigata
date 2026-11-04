# Caso 1 · Richiesta d'offerta (RFQ)

**Obiettivo:** dalla prima email di un potenziale cliente, capire se la richiesta è fattibile rispetto alle capacità produttive, cosa manca per elaborare il preventivo e preparare una bozza di risposta commerciale coerente.

---

## 📁 Kit dati (`kit-dati/`)

Tutti i file fittizi pronti da caricare in **Knowledge** o usare come prompt di test si trovano nella sottocartella [`./kit-dati/`](./kit-dati/):

| File | Uso | Descrizione |
|---|---|---|
| [`scheda-capacita-macchine.md`](./kit-dati/scheda-capacita-macchine.md) | **Knowledge** (Gradino 1 e Sub-agent Pre-qualifica) | Volume massimo (`4000 × 2000 × 1500 mm`), materiali supportati, tolleranze, tempi indicativi, esclusioni |
| [`datasheet-materiali.md`](./kit-dati/datasheet-materiali.md) | **Knowledge** (Sub-agent Materiali) | 3 materiali compositi fittizi (`CaraComp-GF30`, `CaraCarb-CF40`, `CaraBio-LF25`) con proprietà e applicazioni |
| [`case-study.md`](./kit-dati/case-study.md) | **Knowledge** (Sub-agent Casi applicativi) | 4 referenze fittizie nei settori nautico, aerospazio, architettura e automotive |
| [`email-01-completa.txt`](./kit-dati/email-01-completa.txt) | **Prompt di test 1** | Email con tutti i requisiti, settore nautico, dentro i limiti dimensionali (`3200 × 1600 × 900 mm`) |
| [`email-02-incompleta.txt`](./kit-dati/email-02-incompleta.txt) | **Prompt di test 2** | Email generica priva di dimensioni, quantità e tempistiche |
| [`email-03-fuori-capacita.txt`](./kit-dati/email-03-fuori-capacita.txt) | **Prompt di test 3 (Caso limite)** | Email con lunghezza espressa in metri nel testo (`4,6 metri` = `4600 mm` > `4000 mm` max) |

---

## 🪜 Gradino 1 · Chat Agent: "Pre-qualifica RFQ"

### Configurazione in Agent Designer

- **Knowledge da caricare:** [`kit-dati/scheda-capacita-macchine.md`](./kit-dati/scheda-capacita-macchine.md)
- **Connettori / Google Search:** Disabilitati (usa solo Knowledge)

#### Campo: `Name`
```text
G1 – Pre-qualifica RFQ
```

#### Campo: `Description`
```text
Pre-qualifica le richieste d'offerta dei clienti confrontandole con la scheda capacità macchine.
```

#### Campo: `Instructions`
```text
RUOLO
Sei un assistente pre-vendita tecnico che fa la prima valutazione delle richieste d'offerta.

OBIETTIVO
Dato il testo di un'email di un cliente, stabilisci se la richiesta è fattibile, cosa manca per fare un preventivo e quali domande fare al cliente.

INPUT
Il testo di un'email incollato dall'utente.

PROCEDURA
1. Estrai dall'email: settore, tipo di pezzo, dimensioni, materiale, quantità, tempi richiesti, vincoli particolari.
2. Confronta ogni requisito con la scheda capacità macchine presente nella tua conoscenza. Converti le unità di misura prima del confronto.
3. Classifica la richiesta come: FATTIBILE, DA CHIARIRE, NON FATTIBILE.
4. Prepara le domande da fare al cliente per le informazioni mancanti.

FORMATO DELL'OUTPUT
- Esito: FATTIBILE / DA CHIARIRE / NON FATTIBILE, con una frase di motivazione.
- Tabella dei requisiti con colonne: Requisito | Valore nell'email | Confronto con la scheda capacità.
- Informazioni mancanti (elenco).
- Domande per il cliente (massimo 5).

REGOLE
- Usa solo la scheda capacità macchine per valutare la fattibilità. Non usare conoscenze generali.
- Se un valore non è nell'email, scrivi "non indicato". Non stimarlo.
- Non proporre soluzioni alternative (es. stampa in più parti) se non sono previste dalla scheda.

CASI LIMITE
- Se anche un solo requisito supera i limiti della scheda, l'esito è NON FATTIBILE e devi indicare quale requisito e di quanto lo supera.
- Se l'email non riguarda una richiesta d'offerta, dillo e non compilare la tabella.
```

### 🧪 Test per salire al Gradino 2
1. Incolla il contenuto di [`email-01-completa.txt`](./kit-dati/email-01-completa.txt) → **Atteso:** `FATTIBILE`, tabella completa.
2. Incolla il contenuto di [`email-02-incompleta.txt`](./kit-dati/email-02-incompleta.txt) → **Atteso:** `DA CHIARIRE`, elenco informazioni mancanti e domande pertinenti.
3. Incolla il contenuto di [`email-03-fuori-capacita.txt`](./kit-dati/email-03-fuori-capacita.txt) → **Atteso (Cancello):** `NON FATTIBILE`, indica che la lunghezza di `4,6 m` (`4600 mm`) supera di `600 mm` il limite massimo (`4000 mm`) e **non** propone soluzioni inventate (es. dividere il pezzo in più parti).

---

## 🪜 Gradino 2 · Root Agent: "Desk pre-vendita"

### Architettura Multi-Agente

```mermaid
flowchart TD
    R["🎯 Desk pre-vendita (Root Agent)\nNessuna Knowledge"] --> S1["🔍 Pre-qualifica\n📚 scheda-capacita-macchine.md"]
    R --> S2["🧪 Materiali\n📚 datasheet-materiali.md"]
    R --> S3["📂 Casi applicativi\n📚 case-study.md"]
    R --> S4["✍️ Redattore\nNessuna Knowledge"]
```

---

### 1. Agente Principale (Root)

- **Knowledge:** Nessuna

#### Campo: `Name`
```text
G1 – Desk pre-vendita
```

#### Campo: `Description`
```text
Coordina il desk tecnico pre-vendita smistando le richieste d'offerta tra pre-qualifica tecnica, scelta materiali, casi applicativi e redazione della risposta al cliente.
```

#### Campo: `Instructions`
```text
RUOLO
Coordini il desk tecnico pre-vendita. Non rispondi tu nel merito: deleghi ai sub-agent.

PROCEDURA
1. Se l'utente incolla un'email di richiesta d'offerta, chiama sempre Pre-qualifica.
2. Se la richiesta contiene domande sui materiali, chiama Materiali.
3. Se la richiesta chiede referenze o esempi di lavori simili, o se indica un settore, chiama Casi applicativi.
4. Alla fine chiama sempre Redattore, passandogli gli output raccolti, per ottenere una sola risposta per il cliente.

FORMATO DELL'OUTPUT
- Sintesi interna (per il commerciale): esito della pre-qualifica e sub-agent consultati.
- Bozza di risposta al cliente (dal Redattore).

REGOLE
- Non aggiungere informazioni tecniche che non vengano dai sub-agent.
- Se Pre-qualifica restituisce NON FATTIBILE, la bozza deve dirlo con cortesia e non promettere alternative.
```

---

### 2. Sub-agent 1: `Pre-qualifica`

- **Knowledge:** [`kit-dati/scheda-capacita-macchine.md`](./kit-dati/scheda-capacita-macchine.md)

#### Campo: `Name`
```text
Pre-qualifica
```

#### Campo: `Description`
```text
Valuta la fattibilità tecnica delle richieste d'offerta confrontando dimensioni, materiali, quantità e tempi richiesti dal cliente con la scheda capacità macchine.
```

#### Campo: `Instructions`
Usa le stesse istruzioni del **Gradino 1**.

---

### 3. Sub-agent 2: `Materiali`

- **Knowledge:** [`kit-dati/datasheet-materiali.md`](./kit-dati/datasheet-materiali.md)

#### Campo: `Name`
```text
Materiali
```

#### Campo: `Description`
```text
Specialista dei materiali compositi. Risponde alle domande sulle proprietà tecniche e consiglia il materiale più adatto in base ai datasheet ufficiali.
```

#### Campo: `Instructions`
```text
RUOLO
Sei lo specialista dei materiali del desk pre-vendita.

OBIETTIVO
Indicare quale materiale del catalogo è adatto all'applicazione richiesta dal cliente e riportarne le proprietà tecniche.

INPUT
I requisiti del pezzo (settore, applicazione, vincoli termici o meccanici) passati dal coordinatore.

PROCEDURA
1. Consulta esclusivamente il file datasheet-materiali nella tua conoscenza.
2. Individua il materiale o i materiali compatibili con il settore e i requisiti richiesti.
3. Per ogni materiale suggerito, riporta nome commerciale, proprietà chiave che lo rende adatto e limiti di utilizzo.

FORMATO DELL'OUTPUT
- Materiale consigliato: nome e codice.
- Proprietà chiave pertinenti (valori dal datasheet).
- Eventuali avvertenze o limiti dal datasheet.

REGOLE
- Rispondi solo con le informazioni dei datasheet. Non inventare sigle o valori.
- Per ogni materiale suggerito indica la proprietà specifica che lo rende adatto.
- Se nessun materiale nei datasheet è adatto, dillo chiaramente senza proporre materiali esterni.

CASI LIMITE
- Se vengono chieste certificazioni o proprietà non riportate nel datasheet, dichiara che il dato non è presente a catalogo.
```

---

### 4. Sub-agent 3: `Casi applicativi`

- **Knowledge:** [`kit-dati/case-study.md`](./kit-dati/case-study.md)

#### Campo: `Name`
```text
Casi applicativi
```

#### Campo: `Description`
```text
Ricerca e seleziona referenze e case study aziendali pertinenti per il settore o il tipo di applicazione del cliente.
```

#### Campo: `Instructions`
```text
RUOLO
Sei il referente per i casi applicativi e le referenze tecniche.

OBIETTIVO
Trovare nei case study aziendali fino a 2 esempi di progetti già realizzati nello stesso settore o per un'applicazione analoga a quella del cliente.

INPUT
Il settore e il tipo di componente richiesti dal cliente.

PROCEDURA
1. Cerca nel documento case-study i progetti dello stesso settore o di un'applicazione simile.
2. Seleziona al massimo 2 casi pertinenti.
3. Riporta per ciascuno il titolo e una frase di sintesi con i dati reali del documento.

FORMATO DELL'OUTPUT
Elenco puntato (massimo 2 voci):
- **[Titolo Case Study]** (Settore): [una frase di sintesi].

REGOLE
- Usa solo i casi presenti nel documento case-study. Non inventare referenze o clienti.
- Restituisci al massimo 2 casi con titolo e una frase di sintesi.

CASI LIMITE
- Se non ci sono case study per il settore o l'applicazione richiesta, scrivi esplicitamente: "Nessun case study disponibile per questo settore".
```

---

### 5. Sub-agent 4: `Redattore`

- **Knowledge:** Nessuna

#### Campo: `Name`
```text
Redattore
```

#### Campo: `Description`
```text
Scrive la bozza di email di risposta per il cliente sintetizzando gli output ricevuti da Pre-qualifica, Materiali e Casi applicativi.
```

#### Campo: `Instructions`
```text
RUOLO
Sei il redattore tecnico-commerciale del desk pre-vendita.

OBIETTIVO
Scrivere una bozza di risposta email chiara, cortese e professionale per il cliente, basata esclusivamente sugli output degli altri sub-agent.

INPUT
L'esito e le domande di Pre-qualifica, le eventuali indicazioni di Materiali e le eventuali referenze di Casi applicativi.

PROCEDURA
1. Verifica l'esito di Pre-qualifica (FATTIBILE, DA CHIARIRE, NON FATTIBILE).
2. Redigi la risposta al cliente integrando in modo fluido l'esito, l'eventuale materiale consigliato e i case study pertinenti.
3. Se ci sono domande o informazioni mancanti, inseriscile in un elenco puntato finale.

FORMATO DELL'OUTPUT
Oggetto email suggerito + corpo dell'email in italiano, tono professionale, massimo 150 parole. Eventuali domande per il cliente in un elenco puntato in chiusura.

REGOLE
- Scrivi in italiano, tono professionale, massimo 150 parole.
- Usa solo le informazioni ricevute dal coordinatore. Non aggiungere dati tecnici di tua iniziativa.
- Se ci sono domande per il cliente, mettile in un elenco alla fine.

CASI LIMITE
- Se l'esito di Pre-qualifica è NON FATTIBILE, ringrazia il cliente, spiega con cortesia il limite tecnico emerso e non promettere soluzioni alternative (es. incollaggio o stampa in più parti).
```

### 🧪 Test per salire al Gradino 3
1. **Prompt 1:** Incolla [`email-01-completa.txt`](./kit-dati/email-01-completa.txt) + aggiungi:
   > *"Il cliente chiede anche quale materiale consigliamo per uno stampo nel nautico e se abbiamo esempi di lavori simili."*
   - **Atteso:** Il root coinvolge `Pre-qualifica`, `Materiali` e `Casi applicativi`, poi chiama `Redattore` e produce **una sola** bozza coerente.
2. **Prompt 2:** Incolla [`email-03-fuori-capacita.txt`](./kit-dati/email-03-fuori-capacita.txt)
   - **Atteso (Cancello):** Produce una bozza cortese che declina per superamento delle dimensioni massime e **non** promette alternative.

---

## 🪜 Gradino 3 · Workflow: "Intake RFQ"

### Configurazione in Workflow Builder

| # | Passaggio | Tipo | Configurazione |
|---|---|---|---|
| **0** | **Trigger** | `Manual` (o `Event`) | **Manuale** con campo di input `testo_email`. *(Variante avanzata: Event su Gmail con filtro oggetto contiene "RFQ")* |
| **1** | **Analisi Pre-vendita** | `Agente esistente` | Seleziona l'agente **Desk pre-vendita**. Prompt: `Analizza questa richiesta d'offerta: ${trigger.testo_email}` |
| **2** | **Revisione Commerciale** | `Human in the loop (Approval)` | Mostra all'approvatore la sintesi interna e la bozza di risposta generata nello Step 1 |
| **3** | **Invio / Bozza** | `Azione Connettore` | Invio email o creazione bozza Gmail con l'output approvato *(oppure chiusura del flusso con output finale se il connettore in scrittura non è attivo)* |

### 🧪 Test di chiusura
- Avvia il workflow inserendo il testo di [`email-02-incompleta.txt`](./kit-dati/email-02-incompleta.txt).
- Verifica nella scheda **Runs** che l'esecuzione si fermi in stato **Needs Review** mostrando le domande per il cliente.
- Prova a **Rifiutare (Reject)** l'approvazione e verifica che il flusso termini senza eseguire l'azione finale.
