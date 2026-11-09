# 🧪 Esempi di Input per Testare il Workflow No-Code

Questi blocchi vanno incollati nel campo **`Menu_approvato`** del **trigger Manuale**, nella tab **Test** (clic su **Start a test run**), oppure in una chat di Gemini Enterprise dopo `@Workflow Operativo di Brigata`.

> ⚠️ **Non incollare nella casella "What would you like to change?"** a sinistra dell'editor: quella serve a modificare il workflow, non a lanciarlo.

Ogni blocco deve contenere **tutto ciò che serve agli step**: occasione, stagione, numero ospiti, allergie, formalità, budget e menù. Il workflow non fa domande: se manca un dato, fa un'assunzione e la dichiara.

---

## Scenario 1 — Il seguito diretto della demo `chatagent` (Semaforo 🟡 + gestione allergeni)

```text
Occasione: Cena autunnale elegante (non eccessivamente formale)
Stagione: Autunno
Livello di formalità: Elegante
Numero ospiti: 6 persone totali
Esigenze alimentari e allergie:
  * 1 ospite è vegetariano
  * 1 ospite ha un'allergia severa ai crostacei
Budget indicativo del cliente: 90,00 € a persona (vini inclusi)

MENÙ APPROVATO:
- Antipasto: Flan tiepido di zucca mantovana con fonduta leggera di Parmigiano Reggiano 24 mesi e granella di nocciole tostate.
- Primo: Risotto Carnaroli Riserva ai funghi porcini freschi e timo.
- Secondo:
  * Per 5 ospiti (incluso l'allergico ai crostacei): Filetto di branzino selvaggio in crosta di erbe aromatiche.
  * Variante per l'ospite vegetariano: Millefoglie di melanzane, zucca e ricotta di bufala al forno.
- Contorno: Carciofi freschi spadellati alla romana con mentuccia.
- Dolce: Mousse al cioccolato fondente 70% con cuore di agrumi biologici.
- Vini: Franciacorta per l'antipasto, Timorasso per primo e secondo, Moscato d'Asti per il dolce.
```

---

## Scenario 2 — Stress test sul Food Cost (Semaforo 🔴 ROSSO)

Ingredienti molto costosi (ricciola, gamberi rossi, filetto di manzo, Barolo) con budget basso (65 €/persona). Lo Step 3 deve far scattare il rosso e proporre le 2 azioni correttive obbligatorie (una sul piatto più oneroso, una sul vino).

```text
Occasione: Pranzo aziendale formale
Stagione: Primavera
Livello di formalità: Formale
Numero ospiti: 10 persone
Esigenze alimentari: 1 ospite intollerante al lattosio
Budget massimo cliente: 65,00 € a persona (vini inclusi)

MENÙ RICHIESTO:
- Antipasto: Crudo di ricciola fresca con gamberi rossi e agrumi biologici
- Primo: Risotto Carnaroli agli asparagi verdi e gamberi rossi
- Secondo: Filetto di manzo ai funghi porcini
- Contorno: Asparagi verdi glassati al burro di centrifuga
- Dolce: Tiramisù al mascarpone e cioccolato fondente 70%
- Vini: Bollicine Metodo Classico + Rosso da Invecchiamento (Barolo DOCG) + Passito
```

---

## Scenario 3 — Cena a 20 coperti (test di scala)

Utile per verificare arrotondamenti a bottiglia intera (vino da dessert: 1 bottiglia ogni 8 ospiti) e il comportamento con più ospiti vegetariani.

```text
Occasione: Cena Degustazione del Venerdì
Stagione: Autunno
Livello di formalità: Elegante (target 85,00 € a persona)
Numero ospiti: 20 (di cui 2 vegetariani)
Budget: 85,00 € a persona

MENÙ:
1. Antipasto: Polpo verace arrosto su crema di patate a pasta gialla (per i 2 vegetariani: Carciofi dorati su crema di patate)
2. Primo: Pasta artigianale trafilata al bronzo con crema di zucca, funghi porcini e granella di pistacchio
3. Secondo: Guancia di manzo brasata al vino rosso (per i 2 vegetariani: Flan di carciofi e Parmigiano Reggiano 24 mesi)
4. Contorno: Patate a pasta gialla al forno con erbe aromatiche
5. Dolce: Cremoso di ricotta di bufala, cioccolato fondente 70% e scorza d'agrumi
6. Vini: Rosso Elegante DOCG (Chianti Classico) + Vino da Dessert
```

---

## Note sulla modalità Schedule

Il trigger **Schedule** non ha campi di input e non può ricevere un menù incollato. Per eseguire il workflow in automatico servirebbe una fonte esterna (ad esempio un file su Drive con il relativo connettore) e prompt dei nodi scritti per leggerla. Per la demo si usa il trigger Manuale.
