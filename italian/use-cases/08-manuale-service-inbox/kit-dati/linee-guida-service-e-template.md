# Linee Guida Service, Smistamento Inbox, SLA e Template Risposte (`Heron-X 400`)

**Documento operativo per il Team After-Sales & Supporto Tecnico.**
*Ogni email in arrivo nella casella di supporto (`service@lfam-demo.example`) deve essere classificata e gestita seguendo rigorosamente questo documento e `manuale-uso-manutenzione-heron-x400.md`.*

---

## 1. Categorie di Smistamento e Caselle Interne Ufficiali

| Categoria | Quando applicarla | Casella interna di riferimento |
|---|---|---|
| **SUPPORTO TECNICO L1** | Quesiti operativi su uso, parametri materiali, manutenzione programmata, DPI, procedure e allarmi documentati nel manuale (`A201`–`A206`, `S-01`) | `service.l1@lfam-demo.example` |
| **ESCALATION INGEGNERIA L2** | Allarmi **non documentati** nel manuale (es. codici sconosciuti), interventi riservati L2 (riduttore, taratura laser, vite), fermo persistente dopo verifiche L1 o ripetizione allarme `>= 3` volte | `ingegneria.l2@lfam-demo.example` |
| **RICAMBI & TAGLIANDI** | Richieste di preventivo o ordine ricambi (`RIC-HX-...`) e kit tagliando (`RIC-HX-KIT1000`, `RIC-HX-KIT2500`) | `ricambi@lfam-demo.example` |
| **CONTRATTI & GARANZIE** | Richieste di sostituzione gratuita in garanzia fuori termine o su consumabili, note di credito, sconti `> 10%`, upgrade Piano Service | `contratti@lfam-demo.example` |
| **SOLO INFORMATIVA** | Newsletter, inviti a fiere/webinar, notifiche automatiche `no-reply` | *Nessun inoltro — nessuna bozza* |

> **Regola anti-invenzione sui contatti:** usa esclusivamente gli indirizzi interni elencati nella tabella sopra. Non inventare email personali o di altri uffici.

---

## 2. Matrice Priorità e SLA di Prima Risposta

| Priorità | SLA Prima Risposta | Criteri di assegnazione |
|---|---|---|
| **ALTA** | **Entro 2 ore lavorative** | Fermo macchina totale in produzione; allarme non documentato; richiesta pericolosa di bypass sicurezze; reclamo formale urgente |
| **MEDIA** | **Entro 1 giorno lavorativo** | Quesiti tecnici su manutenzione programmata, coppie/parametri o preventivi kit ricambi con macchina operativa |
| **BASSA** | **Entro 3 giorni lavorativi** | Richieste documentali generiche o informazioni commerciali non urgenti |
| **NESSUNA** | **Nessuna risposta** | Email `SOLO INFORMATIVA` (newsletter, webinar, notifiche automatiche) |

---

## 3. Dati Minimi Obbligatori per Segnalazioni di Fermo Macchina / Guasto

Per prendere in carico un guasto o verificare il diritto alla reperibilità `Premium H24`, l'email del cliente deve indicare:
1. **Ragione sociale** del cliente;
2. **Matricola della macchina** (formato `HX-YYYY-NNN`, indispensabile per verificare Piano `Standard` vs `Premium H24` e stato garanzia);
3. **Codice allarme** mostrato su HMI (oppure descrizione puntuale del sintomo senza codice);
4. **Ore macchina attuali** e **materiale in stampa** al momento del blocco.

Se uno o più dati mancano, scrivi `"non indicato"` nella scheda interna e chiedili esplicitamente nella bozza di risposta in un elenco puntato.

---

## 4. Limiti di Delega e Divieti di Sicurezza ("Regole Rosse")

Il supporto di primo livello **NON può mai**:
1. **Autorizzare o suggerire il bypass di sicurezze** (barriere ottiche, microinterruttori porta, emergenze) né l'uso di temperature `> 320 °C`, polimeri non ammessi (`PEEK`/`PEKK`) o procedure non presenti nel manuale → **rifiuto netto** citando il Capitolo/Sezione del manuale.
2. **Inventare procedure di verifica per codici allarme assenti dal manuale** → dichiarare esplicitamente che il codice non è documentato e scalare a `ingegneria.l2@lfam-demo.example`.
3. **Confermare garanzie gratuite, rimborsi, note di credito o sconti superiori al 10%** → marcare `DA SCALARE INTERNAMENTE` verso `contratti@lfam-demo.example` senza promettere né pre-approvare alcunché.
4. **Confermare l'uscita del tecnico in reperibilità H24 / serale / festiva** senza aver verificato la matricola macchina e un Piano `Premium H24` attivo (orario `Standard`: lun–ven `08:30–18:00`).

---

## 5. Template Ufficiali di Risposta Email

> **Regole generali di stile:** italiano, tono tecnico-professionale chiaro e cortese, **massimo 150 parole** di corpo email, firma `Team After-Sales & Supporto Tecnico — Reparto LFAM`.

### Template A — Risposta Tecnica L1 / Manutenzione Standard (Entro Delega)
```text
Oggetto: Re: <Oggetto originale>

Gentile <Nome Referente>,

grazie per averci scritto in merito alla vostra Heron-X 400 (<Matricola>).

Secondo il Manuale di Uso e Manutenzione Heron-X 400 (Rev. 3.1):
- <Indicazione tecnica puntuale, parametri/coppie/ricambi e riferimento Capitolo/Sezione>
- <Eventuali avvertenze di sicurezza e DPI obbligatori dal manuale>

<Se richiesto anche un kit/ricambio, precisare che abbiamo inoltrato il riferimento all'ufficio Ricambi per la quotazione formale.>

Restiamo a disposizione per qualsiasi ulteriore chiarimento.

Cordiali saluti,
Team After-Sales & Supporto Tecnico — Reparto LFAM
```

### Template B — Presa in Carico Fermo Macchina / Priorità ALTA con Dati Mancanti
```text
Oggetto: [PRIORITÀ ALTA] Re: <Oggetto originale>

Gentile <Nome Referente>,

abbiamo preso in carico con priorità alta la vostra segnalazione di fermo macchina e abbiamo già allertato il nostro team di Supporto Tecnico.

Per verificare il vostro Piano Service (Standard lun–ven 08:30–18:00 vs reperibilità Premium H24) e fornirvi subito la procedura corretta, vi chiediamo di risponderci indicando:
- <Dato obbligatorio mancante 1>
- <Dato obbligatorio mancante 2>
- <Dato obbligatorio mancante 3>

Non possiamo confermare interventi in reperibilità H24 prima della verifica della matricola e del contratto attivo. Non appena ricevuti i dati vi ricontatteremo immediatamente.

Cordiali saluti,
Team After-Sales & Supporto Tecnico — Reparto LFAM
```

### Template C — Risposta Interlocutoria per Escalation L2 / Richieste Fuori Delega (`DA SCALARE INTERNAMENTE`)
```text
Oggetto: Re: <Oggetto originale> — Presa in carico e avvertenza di sicurezza

Gentile <Nome Referente>,

confermiamo la ricezione della vostra segnalazione sulla macchina <Matricola>.

<Se presente richiesta pericolosa/vietata: precisazione ferma del divieto dal Manuale — es. divieto assoluto di bypass delle barriere ottiche (Cap. 2, Sez. 2.2) e mantenimento macchina in sicurezza.>
<Se presente codice allarme non nel manuale: precisare che il codice non è documentato nel manuale L1 e che la segnalazione è stata escalata con priorità alta all'Ingegneria L2.>
<Se presenti richieste di garanzia straordinaria, rimborsi o sconti > 10%: precisare che tali valutazioni economiche/contrattuali sono state trasmesse all'ufficio Contratti & Garanzie, senza anticipare alcuna conferma o sconto.>

Un nostro referente specializzato vi contatterà al più presto.

Cordiali saluti,
Team After-Sales & Supporto Tecnico — Reparto LFAM
```
