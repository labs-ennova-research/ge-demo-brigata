# Report Prove Interne Pre-FAT — Commessa `COMM-2026-088` (`Kestrel-500 Hybrid`)

**Data esecuzione prove:** `12/11/2026` · **Matricola macchina:** `KS-2026-011` · **Sede:** Officina Collaudi Fornitore.
*Nota: questo report registra i soli valori misurati durante le 6 prove interne `FAT-01` – `FAT-06`. I requisiti minimi contrattuali sono definiti in `dossier-01-capitolato-ordine-cliente.md`; email e ruoli dei responsabili sono in `dossier-03-rubrica-stakeholder-e-piano.md`.*

---

## Tabella Riepilogativa delle Prove Pre-FAT

| ID Prova | Oggetto della Verifica | Valore Rilevato in Officina / Documenti | Esito | Severità Anomalia | Responsabile Verifica | Note Operative |
|---|---|---|---|---|---|---|
| `FAT-01` | Test barriere fotoelettriche, arresto emergenza e interblocco cambio testa | Tempo arresto rilevato: **`0,42 s`**; interblocco cono `HSK-63F` attivo | `SUPERATA` | `Nessuna` | Sara Fontana | Conforme alla norma EN ISO 10218-2 |
| `FAT-02` | Stampa provino qualifica `CaraCarb-CF40` (`285 °C`, portata `32 kg/h`) | Cordolo uniforme, zero vuoti, delaminazione `0%` | `SUPERATA` | `Nessuna` | Luca Visconti | Provino raffreddato e inviato a fresatura `FAT-03` |
| `FAT-03` | Fresatura CNC 5 assi su provino `CaraCarb-CF40` (verifica tolleranza dimensionale) | Errore massimo misurato a CMM: **`± 0,34 mm`** | **`NON SUPERATA`** | **`CRITICA`** | Luca Visconti | Deriva di compensazione termica su elettromandrino `KM-18`; necessario riallineamento laser L2 e riprova entro il `26/11/2026` |
| `FAT-04` | Misura rugosità superficiale post-fresatura su provino `CaraCarb-CF40` | Rugosità media rilevata: **`Ra 1,35 µm`** | `SUPERATA` | `Nessuna` | Luca Visconti | Finitura superficiale idonea per laminazione stampo |
| `FAT-05` | Stampa provino `PC-CF20` (`295 °C`) + 5 cicli di cambio automatico testa | Cambio testa completato in `48 s`; registrato **1 falso allarme `K404`** (pressione aria `6,1 bar` al picco) | **`SUPERATA CON RISERVA`** | **`MINORE`** | Sara Fontana | Richiesta taratura del pressostato `PS-AIR1` a `6,8 bar` prima della spedizione |
| `FAT-06` | Verifica documentale prontezza sito stabilimento cliente (*Aerospace Tooling Nord*) | Dichiarazione portata pavimento inviata dal cliente: **`2.800 kg/m²`**; linea elettrica `63 A` OK; aspirazione `2.400 m³/h` (`HEPA H13`) OK; **certificato qualità aria compressa (`ISO 8573-1`) non ancora ricevuto** | **`NON SUPERATA`** | **`CRITICA`** | Giulia Moretti | Bloccante per l'installazione del `14/12/2026`: serve verifica strutturale / piastra ripartizione carico + invio certificato aria compressa da parte dell'Ing. Chiara Galli |

---

## Note di Chiusura Report
- Le prove previste dal piano Pre-FAT sono esclusivamente **6** (`FAT-01` – `FAT-06`). Non esistono ulteriori prove numerate oltre `FAT-06`.
- Nessuna prova è stata eseguita su polimeri fuori contratto.
