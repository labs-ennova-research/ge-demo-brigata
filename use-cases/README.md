# Workshop "Crea il tuo agente": guida alla costruzione dei casi

Guida per il facilitatore del modulo **Gemini Enterprise e agenti no-code**. Spiega come preparare il kit dati e come costruire, gradino per gradino, i cinque casi presentati nelle slide 21–25 del deck.

Ogni caso segue la stessa progressione in tre gradini:

| Gradino | Strumento | Cosa si costruisce |
|---|---|---|
| 1 · Chat agent | Agent Designer | Un agente singolo con istruzioni e una fonte di conoscenza |
| 2 · Root agent | Agent Designer (Flow) | L'agente del gradino 1 diventa un sub-agent; si aggiungono altri sub-agent e un agente principale che li coordina |
| 3 · Workflow | Workflow Builder | Il processo diventa un flusso con trigger, passaggi e un punto di approvazione umana prima di ogni azione in scrittura |

Tutti i gruppi partono dal gradino 1. Si sale al gradino successivo solo quando l'agente supera il **test per salire**: il facilitatore fa da "cancello" e verifica il test di persona prima di dare il via libera.

> **Nota sull'interfaccia.** I nomi di menu e pulsanti citati qui seguono la documentazione Google di Agent Designer e Workflow Builder, che è in inglese e cambia spesso. Prima della prima edizione, fai un giro completo nella sandbox e allinea le etichette a quello che vedono davvero i partecipanti.

---

## 0. Struttura di questa cartella (`use-cases/`)

Per facilitare il workshop e la preparazione, ogni caso ha una propria sottocartella con:
- **`README.md`**: tutte le configurazioni pronte da copiare/incollare per **Gradino 1** (Chat Agent), **Gradino 2** (Root Agent + Sub-agent completi di Nome, Descrizione, Istruzioni e collegamento al bucket dati) e **Gradino 3** (Workflow), oltre ai prompt di test.
- **`kit-dati/`**: i file fittizi pronti all'uso (testi, tabelle Markdown, schede tecniche, trascrizioni) già allineati con i casi limite richiesti dai test.

| Caso | Cartella e Guida Agenti | Kit Dati |
|---|---|---|
| **Caso 1 · Richiesta d'offerta** | [`01-richiesta-offerta/README.md`](./01-richiesta-offerta/README.md) | [`01-richiesta-offerta/kit-dati/`](./01-richiesta-offerta/kit-dati/) |
| **Caso 2 · Assistenza tecnica** | [`02-assistenza-tecnica/README.md`](./02-assistenza-tecnica/README.md) | [`02-assistenza-tecnica/kit-dati/`](./02-assistenza-tecnica/kit-dati/) |
| **Caso 3 · Offerte fornitori** | [`03-offerte-fornitori/README.md`](./03-offerte-fornitori/README.md) | [`03-offerte-fornitori/kit-dati/`](./03-offerte-fornitori/kit-dati/) |
| **Caso 4 · Dal verbale alle azioni** | [`04-verbale-azioni/README.md`](./04-verbale-azioni/README.md) | [`04-verbale-azioni/kit-dati/`](./04-verbale-azioni/kit-dati/) |
| **Caso 5 · Stato commesse** | [`05-stato-commesse/README.md`](./05-stato-commesse/README.md) | [`05-stato-commesse/kit-dati/`](./05-stato-commesse/kit-dati/) |

---

## 1. Tempi e progressione

La slide dei tempi prevede 40 minuti di costruzione (20–60') e 15 di test (60–75'). Con i gradini, costruzione e test si alternano a ogni passaggio. Una scansione realistica:

| Tempo | Gruppo medio | Gruppo veloce |
|---|---|---|
| 20–40' | Gradino 1 e test | Gradino 1 e test |
| 40–60' | Gradino 2 | Gradino 2 e test |
| 60–75' | Test del gradino 2 | Gradino 3 e test di chiusura |

Chi non arriva al gradino 3 non ha perso nulla: ha comunque un agente funzionante da mostrare in restituzione. Nella versione da 3 ore l'obiettivo realistico è il gradino 2.

**Regola d'oro da ripetere in aula:** non si passa al gradino successivo per noia, si passa perché il test è superato. Un root agent costruito sopra un sub-agent che inventa i dati moltiplica l'errore.

---

## 2. Prima del workshop

### 2.1 Prerequisiti in sandbox

Verifica con l'IT, almeno qualche giorno prima:

- **Agent Designer abilitato** per l'app della sandbox. È una funzione che l'amministratore attiva dalle impostazioni delle funzionalità della web app.
- **Workflow Builder abilitato**, necessario per il gradino 3. Va attivato a parte e, secondo quanto comunicato da Google, può richiedere che il progetto sia in allowlist. Se non è disponibile, il gradino 3 si fa in versione ridotta (vedi la variante in ogni caso).
- **Connettori della sandbox**: almeno Google Drive in lettura per il kit dati. Per il gradino 3 servono, a seconda del caso, Gmail (o Outlook), Google Chat e Google Sheets. Controlla anche quali azioni in scrittura sono consentite.
- **Account dei partecipanti**: accesso all'app sandbox e alla cartella del kit, e connettori già autorizzati. Il "primo accesso" e l'autorizzazione dei connettori sono già nella demo: facci ripetere l'operazione all'inizio se qualcuno non l'ha fatta.

### 2.2 Il kit dati

Crea una cartella condivisa, per esempio `Workshop agenti – Kit dati`, con una sottocartella per caso:

```
Kit dati/
├── 01-richiesta-offerta/
├── 02-assistenza-tecnica/
├── 03-offerte-fornitori/
├── 04-verbale-azioni/
└── 05-stato-commesse/
```

Regole per il kit:

- **Solo dati fittizi.** Nessun cliente, fornitore, nome di persona o numero reale. I valori tecnici di esempio in questa guida sono inventati: adattali in modo che siano verosimili per Caracol, ma senza usare dati veri.
- **Ogni kit contiene almeno un caso limite**, cioè il documento che fa fallire un agente scritto male. È quello che rende utile il test.
- **File piccoli**: pochi documenti, brevi. L'obiettivo è imparare a costruire, non stressare il modello.

Nei paragrafi dei singoli casi trovi il contenuto da preparare per ogni file.

### 2.3 Materiale per i partecipanti

- Le slide 21–25 a schermo durante la costruzione.
- Un foglio stampato o un documento condiviso con il **template di istruzioni** (paragrafo 3.3) e i **prompt di prova** del proprio caso.

---

## 3. Gli strumenti in cinque minuti

### 3.1 Agent Designer (gradini 1 e 2)

Agent Designer è lo strumento no-code di Gemini Enterprise per creare agenti singoli e agenti multi-step, cioè un agente principale che coordina uno o più sub-agent.

**Due modi per creare un agente** (dalla web app, voce *Create agent*):

1. **Da prompt**: si descrive l'agente nella chat a sinistra e Agent Designer genera una prima versione. È veloce, ma il risultato va sempre rivisto.
2. **Dal builder** (*Proceed to builder*): si apre direttamente il canvas, con un agente vuoto da configurare a mano. È più adatto quando si vogliono controllare istruzioni e sub-agent.

**Per il workshop consiglia il builder**, oppure il prompt usato solo come bozza. Le istruzioni scritte dai partecipanti sono il cuore dell'esercizio, e lasciarle generare interamente toglie l'apprendimento.

**Il canvas** ha tre schede principali:

- **Flow**: la rappresentazione visiva dell'agente. Cliccando sul nodo dell'agente principale si configurano nome, descrizione, istruzioni, modello, sorgenti dati e strumenti. Passando il puntatore sul nodo compare *Add subagent*.
- **Preview**: l'ambiente di test interattivo. È qui che si eseguono i prompt di prova.
- **Schedule**: le esecuzioni pianificate (non servono nei gradini 1 e 2).

**Campi principali di un agente:**

| Campo | Cosa scriverci |
|---|---|
| Name | Nome breve e parlante, con il prefisso del gruppo per evitare conflitti in sandbox: `G3 – Prequalifica RFQ` |
| Description | Una frase su cosa fa. Nel gradino 2 è importante: aiuta l'agente principale a capire a chi delegare |
| Instructions | Le istruzioni complete (template al paragrafo 3.3). C'è anche *Help me write*, utile per rifinire, non per partire da zero |
| Model | Lascia il modello predefinito, salvo indicazioni diverse dell'IT |
| Data sources & tools | I connettori e i bucket dati che l'agente o i sub-agent possono usare |
| Knowledge | *Add files*: i file del kit da caricare per l'agente singolo (Gradino 1) |

**Come dare i dati agli agenti:**

- **Agente singolo (Gradino 1)**: si caricano i file in *Knowledge*. È semplice e immediato: l'agente vede solo quei file.
- **Sub-agent (Gradino 2)**: per i sub-agent non si carica manualmente la *Knowledge*, ma si fanno puntare direttamente a un **bucket** dove sono ospitati i dati.

### 3.2 Workflow Builder (gradino 3)

Workflow Builder crea **workflow agent**: agenti che eseguono una sequenza di passaggi, con un mix di automazione AI e intervento umano, a partire da un trigger.

**Trigger disponibili:**

| Trigger | Quando si attiva | Uso nel workshop |
|---|---|---|
| Manual | Su richiesta: l'utente richiama il workflow con `@nome-workflow` dalla chat, eventualmente compilando dei campi di input | La scelta più sicura in aula, per tutti i casi |
| Schedule | A una frequenza stabilita | Caso 5 |
| Event | Quando cambiano i dati in un'app connessa, con un filtro | Casi 1, 2 e 3, se l'evento del connettore è disponibile in sandbox |

**Passaggi principali:**

- **Gemini Agent**: un passaggio AI con istruzioni proprie.
- **Agente esistente**: richiama un agente già costruito, come quello del gradino 2. Riceve solo ciò che gli si passa esplicitamente nel prompt del passaggio, anche facendo riferimento all'output dei passaggi precedenti con la sintassi `${nome_step.output}`. Se l'agente di origine viene aggiornato, il workflow usa automaticamente la versione più recente.
- **Human in the loop**, in due tipi:
  - **Request info**: mette in pausa il flusso e fa una o più domande a una persona.
  - **Approval**: mette in pausa il flusso e presenta l'output per approvazione prima dei passaggi successivi.
- **Azioni sui connettori**: invio email, messaggi, aggiornamento di file. Disponibilità e nomi dipendono dai connettori abilitati in sandbox.

Quando un'esecuzione arriva a un passaggio umano, si ferma e compare con stato *Needs Review* nella scheda *Runs* del workflow. Fai vedere ai partecipanti dove trovarla: è lì che si approva o si rifiuta.

### 3.3 Template di istruzioni

Fai usare a tutti la stessa struttura. Le istruzioni sotto, per ogni caso, la seguono.

```
RUOLO
Chi sei, in una frase.

OBIETTIVO
Che cosa produci e per chi.

INPUT
Che cosa ricevi (testo incollato, file, richiesta dell'utente).

PROCEDURA
1. ...
2. ...

FORMATO DELL'OUTPUT
Struttura esatta della risposta (tabella, sezioni, lunghezza).

REGOLE
- Usa solo le informazioni presenti in [fonte]. Non inventare dati.
- Se un'informazione manca, scrivi "non indicato" / chiedila.
- ...

CASI LIMITE
- Se succede X, fai Y.
```

Tre principi da far passare in aula:

1. **Le regole contro l'invenzione vanno scritte esplicitamente.** Il modello tende a "completare" i dati mancanti con valori plausibili, ed è proprio quello che i test vanno a cercare.
2. **Il formato dell'output va descritto con precisione**, soprattutto nel gradino 2, dove l'output di un sub-agent diventa l'input di un altro.
3. **I casi limite si scrivono prima di costruire**, non dopo aver visto l'errore.

---

## 4. Schema comune dei tre gradini

### Gradino 1 · Chat agent

1. Crea l'agente dal builder.
2. Compila nome, descrizione e istruzioni.
3. Carica in *Knowledge* i file del kit indicati nel caso.
4. Salva e prova in *Preview* con tutti i prompt di prova, **incluso il caso limite**.
5. Correggi le istruzioni finché il test per salire non passa, poi chiama il facilitatore.

### Gradino 2 · Root agent

1. **Riapri lo stesso agente** del gradino 1, oppure duplicalo se l'interfaccia lo consente e vuoi tenere la versione precedente.
2. Trasformalo in sub-agent: la soluzione più pulita è creare un nuovo agente principale ("root") e riportare le istruzioni del gradino 1 in un sub-agent con lo stesso compito. In alternativa, si aggiungono sub-agent all'agente esistente e si riscrivono le sue istruzioni da "esecutore" a "coordinatore". Scegli una delle due modalità e usala per tutti i gruppi.
3. Aggiungi gli altri sub-agent con *Add subagent*, ognuno con nome, descrizione e istruzioni proprie, facendoli puntare al bucket dove sono ospitati i dati.
4. Scrivi le istruzioni del root agent: **quando** chiamare ciascun sub-agent e **come** combinare le risposte.
5. Prova in *Preview* con i prompt di prova, poi chiama il facilitatore.

**Il punto da far capire al gradino 2:** il root agent non sa fare il lavoro, sa a chi affidarlo. Se il root agent risponde "da solo" senza delegare, le descrizioni dei sub-agent sono troppo vaghe, oppure le istruzioni del root non dicono quando delegare.

### Gradino 3 · Workflow

1. Crea un nuovo workflow in Workflow Builder.
2. Scegli il trigger. In aula, il **manuale con campi di input** è il più affidabile; l'evento o la pianificazione sono un plus.
3. Aggiungi i passaggi: tipicamente un passaggio *agente esistente* che richiama l'agente del gradino 2, poi un passaggio *Gemini Agent* per preparare l'output finale, poi **Approval**, poi l'azione.
4. Esegui il workflow, vai in *Runs*, apri l'esecuzione in *Needs Review* e prova sia l'approvazione sia il rifiuto.

**Variante senza connettori in scrittura:** il flusso si chiude con l'approvazione e l'output finale visibile nell'esecuzione. Il valore didattico, cioè dove e perché mettere l'umano, resta intatto.

---

## 5. Caso 1 · Richiesta d'offerta

**Obiettivo:** dalla prima email di un potenziale cliente, capire se la richiesta è fattibile, cosa manca e come rispondere.

### 5.1 Kit dati (`01-richiesta-offerta/`)

| File | Contenuto da preparare |
|---|---|
| `scheda-capacita-macchine.md` | Una pagina con: volume massimo di stampa (es. 4000 × 2000 × 1500 mm, valore fittizio), materiali supportati (5–6 voci), tolleranze tipiche, tempi indicativi di produzione per fascia dimensionale, cosa *non* si fa (es. pezzi trasparenti, certificazioni alimentari) |
| `email-01-completa.txt` | Richiesta con tutti i dati: settore nautico, stampo per scafo, dimensioni dentro il volume, materiale indicato, quantità 1, consegna in 8 settimane |
| `email-02-incompleta.txt` | Richiesta generica: "ci serve un preventivo per un componente in composito, potete aiutarci?", senza dimensioni né quantità |
| `email-03-fuori-capacita.txt` | Pezzo con una dimensione oltre il volume massimo di stampa, scritta in modo poco evidente (es. in metri, dentro un paragrafo) |
| `datasheet-materiali.md` | 3 materiali fittizi con proprietà principali e applicazioni tipiche |
| `case-study.md` | 4 casi applicativi fittizi, uno per settore: nautico, aerospazio, architettura, automotive |

Il caso limite è l'email 3: la dimensione fuori capacità deve essere "nascosta" abbastanza da sfuggire a un agente che non confronta davvero i valori.

### 5.2 Gradino 1 · Agente "Pre-qualifica RFQ"

**Knowledge:** `scheda-capacita-macchine.md`

**Description:** Pre-qualifica le richieste d'offerta dei clienti confrontandole con la scheda capacità macchine.

**Instructions:**

```
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

**Prompt di prova:**

1. Incolla `email-01-completa.txt` → atteso: FATTIBILE, tabella completa.
2. Incolla `email-02-incompleta.txt` → atteso: DA CHIARIRE, domande pertinenti.
3. Incolla `email-03-fuori-capacita.txt` → atteso: NON FATTIBILE, con la dimensione che sfora.

**Test per salire:** il prompt 3 restituisce NON FATTIBILE, indica il requisito che sfora e non propone soluzioni inventate.

**Errori frequenti:** l'agente non converte metri in millimetri; l'agente propone di "dividere il pezzo in più parti". La correzione si fa nelle istruzioni (passo 2 e regola 3), non nel prompt.

### 5.3 Gradino 2 · Root agent "Desk pre-vendita"

| Agente | Ruolo | Sorgente dati |
|---|---|---|
| **Desk pre-vendita** (root) | Capisce la richiesta e la smista | Nessuna |
| Pre-qualifica | L'agente del gradino 1 | Bucket dati (`scheda-capacita-macchine.md`) |
| Materiali | Risponde su proprietà e scelta dei materiali | Bucket dati (`datasheet-materiali.md`) |
| Casi applicativi | Trova referenze pertinenti per settore | Bucket dati (`case-study.md`) |
| Redattore | Scrive la risposta al cliente a partire dagli output degli altri | Nessuna |

**Instructions del root:**

```
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

**Instructions dei sub-agent (sintesi da sviluppare):**

- **Materiali:** "Rispondi solo con le informazioni dei datasheet. Per ogni materiale suggerito indica la proprietà che lo rende adatto. Se nessun materiale è adatto, dillo."
- **Casi applicativi:** "Cerca nei case study quelli dello stesso settore o di un'applicazione simile. Restituisci al massimo 2 casi con titolo e una frase di sintesi. Se non ce ne sono, dillo."
- **Redattore:** "Scrivi una risposta al cliente in italiano, tono professionale, massimo 150 parole. Usa solo le informazioni ricevute. Se ci sono domande per il cliente, mettile in un elenco alla fine."

**Prompt di prova:**

1. `email-01-completa.txt` + "Il cliente chiede anche quale materiale consigliamo per uno stampo nel nautico e se abbiamo esempi di lavori simili."
2. `email-03-fuori-capacita.txt`

**Test per salire:** il prompt 1 coinvolge Materiali e Casi applicativi e produce **una sola** bozza coerente; il prompt 2 produce una bozza che non promette alternative.

### 5.4 Gradino 3 · Workflow "Intake RFQ"

| # | Passaggio | Configurazione |
|---|---|---|
| 0 | Trigger | **Manuale** con campo di input `testo_email`. Variante avanzata: **Event** sul connettore email, con filtro sull'oggetto (es. contiene "RFQ") |
| 1 | Agente esistente | Desk pre-vendita. Prompt: `Analizza questa richiesta d'offerta: ${trigger.testo_email}` (adatta il riferimento alla sintassi mostrata nel builder) |
| 2 | Approval | Mostra all'approvatore la bozza di risposta e l'esito della pre-qualifica |
| 3 | Azione | Invio della risposta via connettore email; oppure, se l'invio non è abilitato, creazione di una bozza o semplice chiusura con output |

**Test di chiusura:** con `email-02-incompleta.txt` il flusso si ferma all'approvazione con le domande per il cliente; rifiutando, nulla parte.

---

## 6. Caso 2 · Assistenza tecnica

**Obiettivo:** aiutare il primo livello di assistenza a rispondere a una segnalazione dal campo e a preparare l'escalation quando serve.

### 6.1 Kit dati (`02-assistenza-tecnica/`)

| File | Contenuto da preparare |
|---|---|
| `manuale-troubleshooting.md` | 3–4 pagine con una tabella allarmi: codice (es. E101–E110, fittizi), descrizione, cause probabili, procedura di verifica passo passo, quando chiamare il tecnico. Il codice **E199** non deve comparire |
| `storico-ticket.md` | Tabella di 20 righe con colonne `id_ticket, data, matricola_macchina, codice_allarme, descrizione_cliente, soluzione, tempo_risoluzione_ore`. Almeno 3 ticket sullo stesso allarme (es. E104) |
| `modello-scheda-intervento.md` | Campi: cliente, matricola, codice allarme, descrizione, verifiche già fatte, priorità, ricambi ipotizzati |

I casi limite sono due: l'allarme E199, assente dal manuale, e una segnalazione senza matricola, che serve al gradino 3.

### 6.2 Gradino 1 · Agente "Supporto manuale"

**Knowledge:** `manuale-troubleshooting.md`

**Instructions:**

```
RUOLO
Sei un assistente di primo livello per il supporto tecnico sulle macchine.

OBIETTIVO
Guidare l'operatore nella verifica di un allarme usando esclusivamente il manuale di troubleshooting.

PROCEDURA
1. Individua il codice allarme o il sintomo descritto.
2. Cerca la voce corrispondente nel manuale.
3. Riporta le cause probabili e la procedura di verifica nell'ordine del manuale.

FORMATO DELL'OUTPUT
- Allarme: codice e descrizione.
- Cause probabili.
- Procedura di verifica (passi numerati).
- Quando chiamare il tecnico.
- Fonte: sezione del manuale.

REGOLE
- Cita sempre la sezione del manuale da cui prendi la procedura.
- Non suggerire interventi che non sono nel manuale, anche se ti sembrano ragionevoli.

CASI LIMITE
- Se il codice o il sintomo non sono nel manuale, scrivi che la procedura non è documentata e consiglia l'escalation al tecnico. Non proporre verifiche generiche.
```

**Prompt di prova:**

1. "La macchina segnala E104, cosa devo controllare?"
2. "Il cliente dice che l'estrusore si ferma a metà stampa senza codice." (sintomo descritto nel manuale)
3. "Allarme E199, come procedo?"

**Test per salire:** il prompt 3 dichiara che la procedura non c'è e suggerisce l'escalation, senza verifiche inventate.

### 6.3 Gradino 2 · Root agent "Triage assistenza"

| Agente | Ruolo | Sorgente dati |
|---|---|---|
| **Triage assistenza** (root) | Classifica la segnalazione e coordina | Nessuna |
| Manuale | L'agente del gradino 1 | Bucket dati (`manuale-troubleshooting.md`) |
| Storico ticket | Trova i ticket simili e come sono stati risolti | Bucket dati (`storico-ticket.md`) |
| Escalation | Compila la scheda intervento per il tecnico | Bucket dati (`modello-scheda-intervento.md`) |

**Instructions del root:**

```
RUOLO
Fai il triage delle segnalazioni di assistenza tecnica.

PROCEDURA
1. Chiama sempre Manuale con il codice o il sintomo.
2. Chiama sempre Storico ticket per verificare se il problema si è già presentato.
3. Chiama Escalation se: il manuale non documenta il problema, oppure il manuale dice di chiamare il tecnico, oppure lo storico mostra che il problema si è ripetuto più di 2 volte sulla stessa matricola.

FORMATO DELL'OUTPUT
- Priorità: ALTA / MEDIA / BASSA, con motivazione.
- Cosa fare subito (dal Manuale).
- Precedenti (dallo Storico ticket).
- Scheda intervento (da Escalation), solo se prevista.

REGOLE
- Non riformulare le procedure del manuale: riportale.
- Se i sub-agent danno informazioni in contrasto, segnalalo.
```

**Sub-agent:**

- **Storico ticket:** "Cerca in `storico-ticket.md` i ticket con lo stesso codice allarme o una descrizione simile. Restituisci al massimo 3 ticket con id, data, soluzione e tempo di risoluzione. Se non ce ne sono, dillo."
- **Escalation:** "Compila la scheda intervento con i soli dati ricevuti. Lascia 'da completare' nei campi senza dati. Non assegnare ricambi se non sono indicati dal manuale o dallo storico."

**Test per salire:** per "E104 sulla matricola M-0042" la risposta unisce la procedura del manuale e almeno un ticket simile dallo storico.

### 6.4 Gradino 3 · Workflow "Nuova segnalazione"

| # | Passaggio | Configurazione |
|---|---|---|
| 0 | Trigger | Manuale con campi `descrizione`, `codice_allarme`, `matricola` (quest'ultimo **non obbligatorio**) |
| 1 | Request info | Se la matricola è vuota, chiede all'operatore di inserirla. Se il builder non permette una condizione, mettilo sempre e fai rispondere "già indicata" quando c'è |
| 2 | Agente esistente | Triage assistenza, con descrizione, codice e matricola nel prompt |
| 3 | Approval | Il responsabile del service approva priorità e scheda intervento |
| 4 | Azione | Notifica al tecnico (email o messaggio in Chat), oppure chiusura con output |

**Test di chiusura:** una segnalazione senza matricola fa partire la richiesta di informazioni prima del triage.

---

## 7. Caso 3 · Offerte fornitori

**Obiettivo:** leggere e confrontare le offerte dei fornitori in modo uniforme e preparare la rinegoziazione.

### 7.1 Kit dati (`03-offerte-fornitori/`)

| File | Contenuto da preparare |
|---|---|
| `offerta-fornitore-A.md` | Offerta completa: prezzo unitario, quantità, tempi di consegna, condizioni di pagamento, validità, garanzia |
| `offerta-fornitore-B.md` | Offerta completa ma con prezzo più alto e tempi più brevi |
| `offerta-fornitore-C.md` | Offerta **senza condizioni di pagamento** e con la validità scritta in un punto poco evidente |
| `criteri-valutazione-acquisti.md` | I criteri con un peso: prezzo 40%, tempi 30%, condizioni di pagamento 20%, garanzia 10% (valori di esempio) |

Il caso limite è l'offerta C.

### 7.2 Gradino 1 · Agente "Estrattore offerte"

**Knowledge:** nessuna, l'utente allega o incolla un'offerta per volta. In alternativa, carica le tre offerte e chiedi all'utente di indicare quale analizzare.

**Instructions:**

```
RUOLO
Sei un assistente dell'ufficio acquisti che estrae i dati dalle offerte dei fornitori.

OBIETTIVO
Restituire i dati di un'offerta in una tabella standard, sempre uguale, per poterla confrontare con le altre.

FORMATO DELL'OUTPUT
Tabella con due colonne, Campo | Valore, e queste righe nell'ordine:
Fornitore, Prezzo unitario, Quantità, Prezzo totale, Tempi di consegna, Condizioni di pagamento, Validità dell'offerta, Garanzia, Note.

REGOLE
- Riporta i valori come sono scritti nell'offerta, con l'unità di misura.
- Se un campo non è presente, scrivi "non indicato". Mai un valore stimato o "tipico".
- Calcola il prezzo totale solo se prezzo unitario e quantità sono entrambi presenti.
- Nelle Note segnala ambiguità o condizioni particolari.
```

**Test per salire:** sull'offerta C le condizioni di pagamento risultano "non indicato" e la validità viene trovata.

### 7.3 Gradino 2 · Root agent "Analisi offerte"

| Agente | Ruolo | Sorgente dati |
|---|---|---|
| **Analisi offerte** (root) | Coordina estrazione, confronto e negoziazione | Nessuna |
| Estrattore | L'agente del gradino 1 | Bucket dati (le tre offerte) |
| Analista | Costruisce la matrice di confronto pesata | Bucket dati (`criteri-valutazione-acquisti.md`) |
| Negoziatore | Individua i punti da rinegoziare | Nessuna |

**Instructions del root:**

```
PROCEDURA
1. Chiama Estrattore per ciascuna offerta disponibile.
2. Passa tutte le tabelle ad Analista.
3. Passa la matrice a Negoziatore.

FORMATO DELL'OUTPUT
- Matrice di confronto (da Analista).
- Classifica con punteggio.
- Punti da rinegoziare per fornitore (da Negoziatore).

REGOLE
- Un'offerta con campi "non indicato" va marcata come INCOMPLETA in classifica, non esclusa né completata.
```

**Sub-agent:**

- **Analista:** "Costruisci una tabella con i fornitori in colonna e i criteri in riga. Assegna un punteggio da 1 a 5 per criterio secondo i criteri di valutazione e calcola il totale pesato. Se un criterio è 'non indicato', assegna 0 e scrivi INCOMPLETA."
- **Negoziatore:** "Per ogni fornitore indica al massimo 3 punti su cui chiedere un miglioramento, motivandoli con il confronto con gli altri fornitori. Usa solo i valori della matrice."

**Test per salire:** la matrice confronta tutte e tre le offerte e marca C come incompleta.

### 7.4 Gradino 3 · Workflow "Nuova offerta"

| # | Passaggio | Configurazione |
|---|---|---|
| 0 | Trigger | Manuale con il nome del fornitore e il riferimento al file; variante avanzata: Event su nuovo file nella cartella del kit, se disponibile |
| 1 | Agente esistente | Analisi offerte |
| 2 | Gemini Agent | "Scrivi una bozza di email di rinegoziazione al fornitore usando solo i punti indicati dal Negoziatore. Tono professionale, massimo 120 parole." |
| 3 | Approval | Il buyer approva la bozza |
| 4 | Azione | Invio via email, oppure chiusura con output |

**Test di chiusura:** la bozza cita solo punti presenti nel confronto e non esce senza approvazione.

---

## 8. Caso 4 · Dal verbale alle azioni

**Obiettivo:** trasformare la trascrizione di una riunione in decisioni e azioni verificate, e mandare il follow-up.

### 8.1 Kit dati (`04-verbale-azioni/`)

| File | Contenuto da preparare |
|---|---|
| `trascrizione-riunione-1.txt` | Riunione di avanzamento di 20–30 battute, con 3 decisioni e 4 azioni tutte con owner e scadenza |
| `trascrizione-riunione-2.txt` | Riunione con 5 azioni: una **senza owner** ("qualcuno dovrebbe sentire il fornitore"), una con owner **non presente** tra i partecipanti, una con scadenza vaga ("a breve") |
| `partecipanti.md` | Tabella con `nome, ruolo, email` dei partecipanti, con nomi ed email fittizi |

### 8.2 Gradino 1 · Agente "Estrattore verbale"

**Instructions:**

```
OBIETTIVO
Dalla trascrizione di una riunione estrai decisioni, azioni e punti aperti.

FORMATO DELL'OUTPUT
1. Decisioni (elenco).
2. Azioni: tabella Azione | Owner | Scadenza | Stato. Stato è OK oppure DA VERIFICARE.
3. Punti aperti (elenco).

REGOLE
- Un'azione senza un responsabile esplicito ha Owner "NON ASSEGNATO" e Stato DA VERIFICARE.
- Una scadenza vaga ("a breve", "appena possibile") si riporta tra virgolette con Stato DA VERIFICARE.
- Non dedurre l'owner da chi ha parlato per ultimo o da chi sembra competente.
```

**Test per salire:** sulla trascrizione 2 l'azione senza owner è marcata NON ASSEGNATO e non attribuita a una persona.

### 8.3 Gradino 2 · Root agent "Follow-up riunioni"

| Agente | Ruolo | Sorgente dati |
|---|---|---|
| **Follow-up riunioni** (root) | Coordina | Nessuna |
| Estrattore | L'agente del gradino 1 | Nessuna |
| Verificatore | Incrocia owner e partecipanti, controlla le scadenze | Bucket dati (`partecipanti.md`) |
| Redattore | Scrive il follow-up | Nessuna |

**Sub-agent:**

- **Verificatore:** "Per ogni azione controlla che l'owner sia nell'elenco partecipanti e aggiungi la sua email. Se non c'è, segna OWNER NON IN ELENCO. Se la scadenza non è una data, segna SCADENZA DA DEFINIRE. Non correggere i dati: segnala."
- **Redattore:** "Scrivi l'email di follow-up: decisioni, tabella delle azioni verificate, poi una sezione 'Da chiarire' con le azioni segnalate. Massimo 200 parole oltre alla tabella."

**Instructions del root:** chiama in ordine Estrattore → Verificatore → Redattore; mostra in testa il numero di azioni da chiarire.

**Test per salire:** l'owner non presente tra i partecipanti viene segnalato prima della stesura del follow-up, e compare nella sezione "Da chiarire".

### 8.4 Gradino 3 · Workflow "Follow-up riunione"

| # | Passaggio | Configurazione |
|---|---|---|
| 0 | Trigger | Manuale con campo `trascrizione` |
| 1 | Agente esistente | Follow-up riunioni |
| 2 | Approval | L'organizzatore della riunione approva |
| 3 | Azione | Invio ai partecipanti, oppure chiusura con output |

**Test di chiusura:** rifiutando l'approvazione, il flusso si chiude senza inviare nulla. Fai provare esplicitamente il rifiuto, non solo l'approvazione.

---

## 9. Caso 5 · Stato commesse

**Obiettivo:** avere risposte rapide sullo stato delle commesse e un report settimanale dei rischi.

### 9.1 Kit dati (`05-stato-commesse/`)

| File | Contenuto da preparare |
|---|---|
| `stato-commesse.md` | Tabella di 15 righe, colonne: `codice_commessa, cliente, macchina, fase, data_consegna_prevista, stato, avanzamento_%, note`. Fasi possibili: progettazione, approvvigionamento, assemblaggio, collaudo, spedizione. Includi **una commessa con data già passata e stato "in corso"**, 2–3 commesse con note che indicano un rischio (es. "ritardo fornitore componenti") |
| `soglie.md` | Regole di esempio: ritardo se la data è passata e lo stato non è "consegnata"; rischio se mancano meno di 15 giorni e l'avanzamento è sotto il 70%, o se le note citano fornitori o ricambi |
| `stato-commesse-settimana-tranquilla.md` | Tabella con le stesse colonne, nessuna commessa in ritardo né a rischio. Serve al test del gradino 3 |

Nota: al Gradino 1 il file `stato-commesse.md` può essere caricato in Knowledge, mentre al Gradino 2 i sub-agent puntano al bucket dove sono ospitati i dati.

### 9.2 Gradino 1 · Agente "Consultazione commesse"

**Instructions:**

```
OBIETTIVO
Rispondere a domande puntuali sullo stato delle commesse usando solo i dati del foglio commesse.

REGOLE
- Rispondi sempre citando il codice commessa.
- Se la commessa richiesta non è nel foglio, dillo esplicitamente. Non cercare commesse "simili".
- Se la domanda richiede un dato che non è nel foglio (es. margine, costo), dillo.
- Considera la data di oggi per stabilire se una consegna è passata.
```

**Prompt di prova:** "Quali commesse sono in collaudo?", "Quando consegniamo la C-2026-014?", "Qual è lo stato della C-2026-099?" (inesistente).

**Test per salire:** per la commessa inesistente l'agente dichiara che non è presente nello Sheet.

### 9.3 Gradino 2 · Root agent "Report commesse"

| Agente | Ruolo | Sorgente dati |
|---|---|---|
| **Report commesse** (root) | Coordina e decide il formato | Nessuna |
| Consultazione | L'agente del gradino 1 | Bucket dati (`stato-commesse.md`) |
| Analista ritardi | Applica la regola di ritardo | Bucket dati (`stato-commesse.md`, `soglie.md`) |
| Analista rischi | Applica le regole di rischio | Bucket dati (`stato-commesse.md`, `soglie.md`) |
| Redattore report | Scrive il report | Nessuna |

**Instructions del root:**

```
PROCEDURA
- Domanda puntuale su una commessa → solo Consultazione.
- Richiesta di report o di situazione generale → Analista ritardi, Analista rischi, poi Redattore report.

FORMATO DEL REPORT
1. In ritardo (ordinate per giorni di ritardo, il più grave in cima).
2. A rischio (con il motivo).
3. Regolari (solo il numero).

REGOLE
- Una commessa con data passata e stato diverso da "consegnata" è in ritardo, anche se lo stato è "in corso".
- Se non ci sono commesse in ritardo o a rischio, scrivilo. Non inventare criticità.
```

**Test per salire:** la commessa scaduta ma "in corso" compare in cima al report.

### 9.4 Gradino 3 · Workflow "Report settimanale"

| # | Passaggio | Configurazione |
|---|---|---|
| 0 | Trigger | **Schedule** settimanale (es. lunedì alle 8:00). In aula, per provarlo subito, aggiungi o usa un trigger manuale |
| 1 | Agente esistente | Report commesse, prompt: "Prepara il report settimanale" |
| 2 | Approval | Il responsabile OPS approva |
| 3 | Azione | Invio al team (email o Chat), oppure chiusura con output |

**Test di chiusura:** sulla copia "settimana tranquilla" il report dice che non ci sono criticità, senza inventare rischi.

---

## 10. Checklist del facilitatore

### Il giorno prima

- [ ] Agent Designer e Workflow Builder visibili con un account di prova dei partecipanti
- [ ] Kit dati completo nelle cinque sottocartelle, accessibile dagli account dei partecipanti
- [ ] Ogni caso costruito almeno una volta fino al gradino 2, con i test che passano
- [ ] Almeno un workflow del gradino 3 provato fino all'approvazione in *Runs*
- [ ] Etichette dell'interfaccia allineate a questa guida

### Durante la costruzione

- [ ] Ogni gruppo usa il prefisso nei nomi degli agenti
- [ ] Il facilitatore verifica il test di persona prima del passaggio di gradino
- [ ] Chi è bloccato da più di 5 minuti riceve un suggerimento sulle istruzioni, non la soluzione

### Prima della restituzione

- [ ] Ogni gruppo sa dire a quale gradino è arrivato e quale test ha superato
- [ ] Gli agenti restano in sandbox: nessuna pubblicazione o condivisione fuori dal perimetro previsto

---

## 11. Problemi frequenti

| Sintomo | Causa probabile | Cosa suggerire |
|---|---|---|
| L'agente inventa valori mancanti | Manca una regola esplicita | Aggiungere "Se un valore non c'è, scrivi 'non indicato'" e un caso limite |
| L'agente usa conoscenze generali invece dei file | Le istruzioni non limitano la fonte | Aggiungere "Usa solo [file]"; verificare che i file siano in Knowledge |
| Il root agent risponde senza delegare | Descrizioni dei sub-agent vaghe o istruzioni del root senza regole di delega | Riscrivere le descrizioni con il compito preciso; nel root, una regola "quando → chi" per ogni sub-agent |
| Due sub-agent danno risposte diverse | Fonti sovrapposte | Far puntare ogni sub-agent solo ai dati nel bucket che gli servono |
| Il workflow non riceve i dati del trigger | Riferimento all'output mancante nel prompt del passaggio | Passare esplicitamente i campi con il riferimento all'output del passaggio precedente |
| Nessuno trova l'approvazione | Non si guarda in *Runs* | Mostrare lo stato *Needs Review* e dove si apre l'esecuzione |
| Il connettore non può scrivere | Azione non abilitata in sandbox | Chiudere il flusso dopo l'approvazione con l'output finale |
