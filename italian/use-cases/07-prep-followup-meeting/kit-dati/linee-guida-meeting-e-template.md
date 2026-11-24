# Linee Guida Aziendali — Preparazione e Follow-up Riunioni (NovaServizi S.r.l.)

**Standard operativo per i Project Manager e gli Account Lead nella preparazione degli incontri ("Scheda Prep 5 minuti") e nella redazione delle email di follow-up.**

---

## 1. Quando produrre la "Scheda Prep" vs l'"Email di Follow-up"

- **Modalità PREP (Prima della riunione):** quando l'input riguarda un invito a calendario e/o uno storico di email precedenti all'incontro, produci la **Scheda Prep 5 minuti** ad uso interno.
- **Modalità FOLLOW-UP (Dopo la riunione):** quando l'input contiene appunti, note o esiti di una riunione già svolta, produci la **Tabella di Verifica Azioni** + la **Bozza Email di Follow-up** per i partecipanti.

---

## 2. Standard per la "Scheda Prep 5 minuti" (Pre-Meeting)

La scheda di preparazione pre-riunione deve contenere esattamente queste **5 sezioni** nell'ordine:

1. **Dati incontro e Partecipanti verificati:** titolo, data/ora, sede e tabella dei partecipanti incrociata con `rubrica-stakeholder-progetto.md` (Nome, Azienda, Ruolo, Ambito decisionale). Se nell'invito compare una persona assente dalla rubrica, segnalala come `PARTECIPANTE NON IN RUBRICA`.
2. **Stato attuale dalle ultime email:** sintesi oggettiva (massimo 5 punti) di cosa è successo negli ultimi scambi email sul progetto.
3. **Domande del cliente rimaste senza risposta:** elenco esplicito di quesiti posti dal cliente nelle email precedenti a cui il team NovaServizi non ha ancora dato riscontro scritto.
4. **Criticità aperte e Domande da porre in riunione:** blocchi operativi, ritardi nella consegna di materiali/dati e massimo 4 domande mirate per sbloccarli durante l'incontro.
5. **Argomenti fuori perimetro (NON decidere in seduta):** qualsiasi richiesta emersa nelle email che comporti **anticipi della data contrattuale di Go-Live**, **funzionalità/moduli gratuiti non a contratto** o **riduzioni di canone/budget**. Tali punti non possono essere approvati in riunione operativa ma vanno rimandati a valutazione formale separata (Change Request commerciale).

---

## 3. Regole di Governance per il Follow-up (Post-Meeting)

Ogni azione, decisione o richiesta presente negli appunti post-riunione deve superare questi controlli prima di entrare nell'email di follow-up:

### 3.1 Validazione di Owner e Partecipanti
- Incrocia ogni responsabile (Owner) citato negli appunti con `rubrica-stakeholder-progetto.md` per recuperarne ruolo e indirizzo email ufficiale.
- Se un'azione **non ha un responsabile esplicito** negli appunti (es. *"bisogna inviare..."*, *"qualcuno deve..."*), non attribuirla per deduzione: imposta Owner = **`DA ASSEGNARE`** e Stato = **`DA CONFERMARE`**.
- Se un'azione è assegnata a una persona nominata ma **non presente** in `rubrica-stakeholder-progetto.md`, non inventare il suo indirizzo email: mantieni il nome, scrivi Email = **`NON IN RUBRICA`** e Stato = **`OWNER NON IN RUBRICA`**.

### 3.2 Validazione delle Scadenze
- Una scadenza è valida solo se espressa come **data precisa di calendario** (`GG/MM/AAAA`).
- Se la scadenza è assente o espressa con formule vaghe (*"appena possibile"*, *"a breve"*, *"entro fine mese"* senza giorno), riporta l'espressione tra virgolette e imposta Stato = **`SCADENZA DA CONFERMARE`**.

### 3.3 Separazione tra Decisioni Confermate e Richieste Fuori Perimetro
- Inserisci in **Decisioni confermate** solo scelte operative concordate entro il perimetro attuale del progetto.
- Qualsiasi richiesta del cliente relativa a **moduli aggiuntivi gratuiti**, **estensioni di scopo senza costi** o **variazioni delle date contrattuali di Go-Live** (anche se in riunione si è detto *"verificheremo internamente"*) **NON deve MAI comparire tra le Decisioni confermate**: va isolata nell'apposita sezione **"Richieste fuori perimetro / Da valutare separatamente (Change Request)"**, specificando che non costituisce impegno approvato.

---

## 4. Template Ufficiale — Bozza Email di Follow-up

- **Lunghezza massima:** **200 parole** di testo (escluse le tabelle).
- **Destinatari:** esclusivamente gli indirizzi email verificati in `rubrica-stakeholder-progetto.md` per i partecipanti alla riunione (non inventare mai indirizzi).

```text
Oggetto: [FOLLOW-UP] <Titolo Riunione> — <Data Riunione>

Gentili tutti,

grazie per la partecipazione all'incontro di oggi. Di seguito il riepilogo condiviso dei punti allineati e delle prossime attività sul progetto <Nome/Codice Progetto>.

1. DECISIONI OPERATIVE CONFERMATE
- <Decisione 1>
- <Decisione 2>

2. PIANO D'AZIONE CONFERMATO
| Azione | Owner | Email | Scadenza |
|---|---|---|---|
| <Solo azioni con Stato CONFERMATA> | ... | ... | ... |

3. PUNTI DA CONFERMARE (ASSEGNAZIONI O SCADENZE APERTE)
- <Elenco delle azioni con Stato DA CONFERMARE, OWNER NON IN RUBRICA o SCADENZA DA CONFERMARE, oppure "Nessun punto in sospeso" se tutte regolari>

4. RICHIESTE FUORI PERIMETRO / DA VALUTARE SEPARATAMENTE
- <Eventuali richieste extra-contratto da sottoporre a valutazione commerciale/Change Request senza impegno, oppure ometti la sezione se assenti>

Vi chiediamo cortesemente di segnalarci eventuali integrazioni sui punti da confermare entro 24 ore.

Cordiali saluti,
Project Management Office — NovaServizi S.r.l.
```
