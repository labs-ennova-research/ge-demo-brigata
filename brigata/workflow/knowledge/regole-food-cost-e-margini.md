# Regole di Calcolo Food Cost, Margini e Preventivazione Eventi

Questo documento definisce le politiche economico-finanziarie del ristorante per la validazione dei menù e la formulazione dei preventivi cliente.

---

## 1. Definizioni e Formule Ufficiali

1. **Food Cost Materie Prime (FC_MP)**:
   Somma del costo di acquisto (sul **Peso Lordo** ordinato) di tutti gli ingredienti alimentari del menù, compresi quelli strutturali (uova, panna, verdure del brodo, vino di sfumatura, ecc.).
   > **Margine di sicurezza +10%**: si applica **solo agli ingredienti non presenti a listino** (vedi sezione 3 di `listino-fornitori-e-rese.md`), sul loro Peso Lordo. Gli ingredienti a listino NON hanno il +10%.
2. **Forfait Dispensa Base (FDB)**:
   Per coprire sale, spezie minori, fondi base, pane di accompagnamento e caffè, aggiungere sempre una quota fissa di **2,50 € a coperto**.
3. **Beverage Cost (BC)** *(se l'abbinamento vini è richiesto)*:
   Costo totale delle bottiglie necessarie arrotondato per eccesso alla bottiglia intera (mai frazioni di bottiglia in ordine fornitore), più **1,50 € a coperto** per acqua minerale.
4. **Costo Vivo Totale per Coperto (CV_Coperto)**:
   `CV_Coperto = (FC_MP / Numero_Ospiti) + FDB + (BC / Numero_Ospiti)`

---

## 2. Target di Food Cost % e Moltiplicatori di Prezzo per Fascia Evento

Il ristorante applica un **Food & Beverage Cost % obiettivo** differente in base al livello di servizio richiesto dal cliente:

| Livello di Formalità | Food Cost % Target | Moltiplicatore sul Costo Vivo | Fascia Prezzo Consigliata (a persona, IVA escl.) |
|---|---|---|---|
| **Informale / Conviviale** | 33% | `Costo Vivo × 3,0` | 45,00 € – 65,00 € |
| **Elegante / Cena Speciale** | 28% | `Costo Vivo × 3,5` | 70,00 € – 105,00 € |
| **Formale / Business / Cerimonia** | 25% | `Costo Vivo × 4,0` | 95,00 € – 150,00 € |

> **Nota sull'arrotondamento commerciale**: il prezzo di vendita finale consigliato a persona va sempre arrotondato ai **5,00 € più vicini** (es. 83,40 € → **85,00 € a persona**).

---

## 3. Regole di Semaforo Budget e Gestione Scostamenti

Quando il cliente ha indicato un **budget massimo a persona** (oppure la fascia di formalità impone il tetto indicato nella tabella sopra), il Controller assegna un semaforo al menù:

- 🟢 **VERDE (In linea)**: **entrambe** le condizioni devono essere vere: (a) il prezzo di vendita consigliato (arrotondato ai 5 €) è ≤ al budget del cliente; (b) il Food Cost % effettivo (`CV_Coperto / prezzo arrotondato`) è ≤ al target della fascia. Se (a) è vera e (b) è falsa il semaforo è GIALLO.
- 🟡 **GIALLO (Attenzione — Scostamento tra +1% e +12% sul budget)**: Il menù supera lievemente il budget. Il workflow non blocca il menù ma deve proporre **1 ottimizzazione concreta** sulla portata più costosa (es. ridurre del 15% la grammatura di un ingrediente pregiato o sostituire un taglio con uno equivalente più sostenibile).
- 🔴 **ROSSO (Fuori Budget — Scostamento > +12% sul budget)**: Il menù non è sostenibile ai prezzi attuali. Il workflow deve segnalare l'alert in evidenza e indicare **2 azioni correttive obbligatorie** (una sul Secondo o Primo più oneroso e una sull'abbinamento vini) per riportare il Food Cost % entro la soglia target.

---

## 4. Costi Extra per Varianti Allergeni / Regimi Alimentari

- Se gli ospiti con menù differenziato (es. vegetariano, senza glutine, senza crostacei) sono **fino a 2 persone**, il costo della variante è assorbito nel Food Cost generale senza supplemento al cliente.
- Se le varianti richiedono l'apertura di un lotto fornitore dedicato (es. pasta artigianale certificata senza glutine o sostituto proteico dedicato), contabilizzare **+3,00 € una tantum per coperto speciale** nel calcolo interno del costo vivo.

---

## 5. Verifica dopo un'azione correttiva

Dopo ogni azione correttiva (riduzione di grammatura, sostituzione di un ingrediente o di un vino) il Controller deve **ricalcolare l'intera catena**: FC_MP, Costo Vivo per coperto, prezzo teorico, prezzo arrotondato e Food Cost %, e poi **rifare la verifica del semaforo** della sezione 3. Il semaforo non può diventare verde per il solo fatto che il prezzo arrotondato coincide con il budget: deve valere anche la condizione sul Food Cost %. Se una condizione resta falsa, il semaforo resta giallo e va proposta una seconda azione.
