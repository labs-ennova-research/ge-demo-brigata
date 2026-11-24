# Soglie e Regole di Classificazione Stato Commesse (Direzione Operations)

Documento normativo per la compilazione del Report Settimanale Commesse.
Ogni commessa presente nel foglio `stato-commesse` deve essere classificata in una sola delle seguenti tre categorie (valutate in ordine di priorità: prima Ritardo, poi Rischio, infine Regolare).

---

## 1. Regola di RITARDO (Priorità 1)

Una commessa è classificata **IN RITARDO** se sono vere **entrambe** le seguenti condizioni:
1. La `data_consegna_prevista` è **antecedente alla data di oggi** (`data_consegna_prevista < OGGI`).
2. Il campo `stato` è **diverso da `"consegnata"`**.

> **Attenzione (Caso frequente):** Anche se il campo `stato` riporta `"in corso"`, se la `data_consegna_prevista` è già passata rispetto a oggi, la commessa **è IN RITARDO** e deve essere inserita nella sezione "1. In ritardo", ordinata per numero di giorni di ritardo decrescente (dal ritardo maggiore al minore).

---

## 2. Regole di RISCHIO (Priorità 2)

Una commessa **non in ritardo** e con `stato` diverso da `"consegnata"` è classificata **A RISCHIO** se si verifica **almeno una** delle seguenti condizioni:

- **Condizione R1 (Soglia Avanzamento / Scadenza ravvicinata):**
  Mancano **meno di 15 giorni** di calendario alla `data_consegna_prevista` (`0 <= giorni_mancanti < 15`) **E** la percentuale di avanzamento (`avanzamento_%`) è **strettamente inferiore al 70%** (`avanzamento_% < 70`).
- **Condizione R2 (Criticità Fornitori o Ricambi nelle Note):**
  Il campo `note` menziona problemi, attese o ritardi legati a **fornitori** (es. *"ritardo fornitore"*, *"attesa fornitore"*) oppure a **ricambi** / componenti mancanti.

---

## 3. Commesse REGOLARI (Priorità 3)

Tutte le commesse che **non** rientrano nella categoria "In ritardo" e **non** rientrano nella categoria "A rischio" (incluse le commesse già nello stato `"consegnata"` o `"in corso"` prive di anomalie) sono classificate come **REGOLARI**.
Nel report settimanale, per le commesse regolari va indicato **esclusivamente il numero totale**, senza elencarle singolarmente.
