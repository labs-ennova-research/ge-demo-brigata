# 🤖 Demo e Workshop Agenti No-Code — Gemini Enterprise

Questo repository raccoglie il materiale didattico, i prompt e i kit dati per le sessioni di demo e workshop pratico su **Gemini Enterprise (Agent Designer & Workflow Builder)**.

Il repository è organizzato in due sezioni principali:

```text
ge-demo-brigata/
├── brigata/        <- Caso didattico guidato ("Brigata di Cucina": Chat Agent + Workflow)
└── use-cases/      <- 9 casi d'uso aziendali per il workshop pratico ("Crea il tuo agente")
```

---

## 🍽️ 1. Caso Didattico: Brigata di Cucina (`brigata/`)

Metafora guidata per mostrare in plenaria la differenza tra un sistema **Multi-Agente Conversazionale** (Orchestratore + Chef di Partita) e un **Workflow Operativo Sequenziale** (lista della spesa, allergeni, food cost e *mise en place*).

- 👉 **[Vai alla guida del caso didattico (`brigata/README.md`)](./brigata/README.md)**
  - 💬 [Parte 1 · Chat Agent (`brigata/chatagent/README.md`)](./brigata/chatagent/README.md)
  - ⚙️ [Parte 2 · Workflow No-Code (`brigata/workflow/README.md`)](./brigata/workflow/README.md)

---

## 🛠️ 2. Casi d'Uso per il Workshop (`use-cases/`)

Guida completa e kit dati fittizi per costruire i casi aziendali su **3 livelli progressivi di complessità**, disponibili in tre percorsi didattici:

- 👉 **[Vai alla guida generale del workshop (`use-cases/README.md`)](./use-cases/README.md)**

### Percorso Avanzato (Gradino 1: Chat Agent → Gradino 2: Root Agent + Sub-agent → Gradino 3: Workflow)
- 📋 [Caso 1 · Richiesta d'offerta (RFQ)](./use-cases/01-richiesta-offerta/README.md)
- 🔧 [Caso 2 · Assistenza tecnica](./use-cases/02-assistenza-tecnica/README.md)
- 📊 [Caso 3 · Offerte fornitori](./use-cases/03-offerte-fornitori/README.md)
- 📝 [Caso 4 · Dal verbale alle azioni](./use-cases/04-verbale-azioni/README.md) *(utilizzabile anche come sfida avanzata nel Workshop 2h, lavorando sempre con trascrizione incollata senza connettore Teams)*
- 🏭 [Caso 5 · Stato commesse](./use-cases/05-stato-commesse/README.md)

### Percorso "Modalità Semplice" — Solo Connettore Outlook (Gradino 1: Prompt → Gradino 2: Agente senza connettori → Gradino 3: Agente con solo Outlook)
- 📥 [Caso 6 · Smistamento Inbox e Bozze di Risposta](./use-cases/06-smistamento-inbox/README.md)
- 📅 [Caso 7 · Preparazione e Follow-up Meeting](./use-cases/07-prep-followup-meeting/README.md)

### Percorso Workshop 2h — Progetto + Manuale Tecnico + Solo Outlook (Gradino 1: Progetto Gemini → Gradino 2: Agente Tecnico senza connettori su Manuale Macchina → Gradino 3: Agente con solo Outlook)
- 🛠️ [Caso 8 · Assistenza Tecnica Macchine e Smistamento Inbox (`Heron-X 400`)](./use-cases/08-manuale-service-inbox/README.md)
- 🏗️ [Caso 9 · Collaudo Macchina, Supporto Tecnico e Gestione Meeting (`Kestrel-500 Hybrid`)](./use-cases/09-manuale-commessa-meeting/README.md)
