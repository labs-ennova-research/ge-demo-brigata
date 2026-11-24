# Linee Guida Ufficiali — Smistamento Inbox, SLA e Limiti di Delega (NovaServizi S.r.l.)

**Documento operativo interno per la gestione delle email in ingresso da clienti, partner e fornitori.**
Ogni messaggio ricevuto deve essere classificato e gestito attenendosi esclusivamente alle regole riportate in questo documento.

---

## 1. Categorie di Smistamento e Caselle Interni di Riferimento

Ogni email deve essere assegnata a **una sola** categoria principale (più un eventuale secondo reparto in copia se il testo tocca due ambiti distinti):

| Categoria | Quando applicarla | Casella interna di riferimento |
|---|---|---|
| **COMMERCIALE** | Richieste di preventivo, attivazione moduli aggiuntivi, upgrade di piano o licenze, appuntamenti commerciali | `commerciale@novaservizi-demo.example` |
| **AMMINISTRAZIONE** | Chiarimenti su fatture, copie di cortesia, scadenze di pagamento, variazione IBAN o dati fiscali, note di credito | `amministrazione@novaservizi-demo.example` |
| **SUPPORTO OPERATIVO** | Malfunzionamenti della piattaforma, errori di accesso, blocchi operativi, rallentamenti o anomalie tecniche | `supporto.urgente@novaservizi-demo.example` |
| **CONTRATTI & LEGALE** | Disdette, recessi, rinnovi contrattuali, modifiche alle clausole di preavviso, contestazioni formali o penali | `ufficio.legale@novaservizi-demo.example` |
| **SOLO INFORMATIVA** | Newsletter, rassegne stampa, notifiche automatiche "no-reply", conferme di lettura o inviti generici a webinar | *Nessun inoltro — nessuna risposta richiesta* |

> **Regola anti-invenzione sui contatti:** Non inventare mai indirizzi email personali o di altri uffici non elencati nella tabella sopra.

---

## 2. Matrice di Priorità e SLA di Prima Risposta

| Priorità | SLA Prima Risposta | Criteri oggettivi di assegnazione |
|---|---|---|
| **ALTA** | **Entro 2 ore lavorative** | Blocco operativo totale o multi-utente della piattaforma; scadenza contrattuale/legale entro 48 ore; reclamo formale indirizzato alla Direzione |
| **MEDIA** | **Entro 1 giorno lavorativo** | Richieste commerciali di upgrade/offerta; verifiche puntuali su fatture o addebiti; anomalie parziali con operatività garantita |
| **BASSA** | **Entro 3 giorni lavorativi** | Richieste informative generali (FAQ); aggiornamenti anagrafici o cambio IBAN; richiesta copie documenti storici |
| **NESSUNA** | **Nessuna risposta** | Messaggi classificati come `SOLO INFORMATIVA` (newsletter, notifiche automatiche, promozioni esterne) |

---

## 3. Dati Minimi Obbligatori per Categoria

Prima di confermare una lavorazione nel merito, verifica che nell'email del cliente siano presenti i dati minimi richiesti:

- **AMMINISTRAZIONE (verifica fatture):** Numero fattura + Ragione sociale + Motivo puntuale della segnalazione.
- **SUPPORTO OPERATIVO (guasti/blocchi):** Ragione sociale + **Codice Contratto** (formato `NS-XXXX`, necessario per verificare il livello di servizio *Standard* o *Premium*) + Descrizione dell'errore o schermata/messaggio restituito dal sistema.
- **COMMERCIALE (upgrade/nuovi moduli):** Ragione sociale + Modulo o numero di utenze richieste.

Se manca uno dei dati minimi obbligatori, la bozza di risposta deve **chiederlo esplicitamente al cliente** in un elenco puntato chiaro.

---

## 4. Limiti di Delega e Regole di Escalation ("Regole Rosse")

Chi gestisce la prima risposta via email **NON ha alcuna delega economica o legale** sui seguenti punti:

1. **Rimborsi, storni o note di credito** di qualsiasi importo.
2. **Sconti commerciali superiori al 10%** rispetto al listino in vigore (gli sconti fino al 10% richiedono comunque offerta formale dell'ufficio `COMMERCIALE`).
3. **Deroghe contrattuali**, annullamento di penali o riduzione/azzeramento dei termini di preavviso di disdetta (`60 giorni`).
4. **Conferma di reperibilità tecnica H24 / festiva** se nell'email non è documentato e verificato un contratto con piano **Premium** attivo.

> **Procedura obbligatoria per richieste fuori delega (`DA SCALARE INTERNAMENTE`):**
> Se un cliente chiede uno qualsiasi dei punti 1–3 (anche se sollecita una conferma scritta urgente in giornata):
> - Marca l'esito interno come **`DA SCALARE INTERNAMENTE`** indicando le caselle interne competenti (`amministrazione@novaservizi-demo.example` per note di credito/storni; `ufficio.legale@novaservizi-demo.example` per clausole/preavvisi; `commerciale@novaservizi-demo.example` per sconti).
> - Usa **esclusivamente il Template C** (risposta interlocutoria neutra): conferma la sola presa in carico e il passaggio agli uffici competenti, **senza mai promettere, pre-approvare o lasciare intendere l'accoglimento** di rimborsi, sconti o deroghe contrattuali.
