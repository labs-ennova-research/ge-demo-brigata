# 🧪 Esempi di Input per Testare il Workflow No-Code

Copia e incolla uno dei seguenti blocchi per avviare il **Workflow Operativo di Brigata** nella tab **Preview** di Gemini Enterprise (oppure incolla direttamente il menù finale che hai ottenuto conversando con l'agente della cartella `../chatagent/`).

---

## Scenario 1 — Il seguito diretto della Demo `chatagent` (Semaforo Budget 🟢/🟡 + Gestione Allergeni)

> 💡 **Ideale per una demo dal vivo in 2 tempi**: mostra come l'output conversazionale del *Responsabile di Brigata* (`chatagent`) diventi l'input strutturato del *Workflow Operativo* (`workflow`).

```text
Avvia il workflow operativo per il seguente menù confermato dal cliente:

- Occasione: Cena autunnale elegante (non eccessivamente formale)
- Numero ospiti: 6 persone totali
- Esigenze alimentari e allergie:
  * 1 ospite è vegetariano
  * 1 ospite ha un'allergia severa ai crostacei
- Budget indicativo del cliente: 90,00 € a persona (vini inclusi)

MENÙ APPROVATO:
- Antipasto (Chef Antipasti): Flan tiepido di zucca mantovana con fonduta leggera di Parmigiano Reggiano 24 mesi e granella di nocciole tostate.
- Primo (Chef Primi): Risotto Carnaroli Riserva ai funghi porcini freschi e timo.
- Secondo (Chef Secondi):
  * Per 5 ospiti (incluso l'allergico ai crostacei): Filetto di branzino selvaggio in crosta di erbe aromatiche.
  * Variante per l'ospite vegetariano: Millefoglie di melanzane, zucca e ricotta di bufala al forno.
- Contorno (Chef Contorni): Carciofi freschi spadellati alla romana con mentuccia.
- Dolce (Chef Pasticceria): Mousse al cioccolato fondente 70% con cuore di agrumi biologici.
- Abbinamento Vini (Sommelier):
  * Bollicine Metodo Classico Franciacorta per l'antipasto
  * Bianco Strutturato DOCG (Timorasso) per primo e secondo
  * Moscato d'Asti DOCG per il dolce
```

---

## Scenario 2 — Stress Test sul Food Cost (Semaforo Budget 🔴 ROSSO — Fuori Budget)

> 💡 **Ideale per mostrare il controllo deterministico delle regole aziendali**: il cliente chiede ingredienti molto costosi (ricciola, gamberi rossi, filetto di manzo, Barolo) ma con un budget basso (65 €/persona). Lo **Step 3** farà scattare il semaforo 🔴 ROSSO e proporrà le 2 azioni correttive obbligatorie previste da `regole-food-cost-e-margini.md`.

```text
Avvia il workflow operativo per il seguente menù:

- Occasione: Pranzo aziendale formale
- Stagione: Primavera
- Numero ospiti: 10 persone
- Esigenze alimentari: 1 ospite intollerante al lattosio
- Budget massimo cliente: 65,00 € a persona (vini inclusi)

MENÙ RICHIESTO:
- Antipasto: Crudo di ricciola fresca con gamberi rossi e agrumi biologici
- Primo: Risotto Carnaroli agli asparagi verdi e gamberi rossi
- Secondo: Filetto di manzo ai funghi porcini
- Contorno: Asparagi verdi glassati al burro di centrifuga
- Dolce: Tiramisù al mascarpone e cioccolato fondente 70%
- Vini: Bollicine Metodo Classico + Rosso da Invecchiamento (Barolo DOCG) + Passito
```

---

## Scenario 3 — Prompt per Esecuzione Pianificata (Tab "Schedule")

> 💡 **Ideale per mostrare l'automazione ricorrente**: da incollare nella configurazione della tab **Schedule** (es. *Ogni Lunedì alle 08:30*).

```text
Esegui il workflow settimanale di pianificazione della brigata per l'evento "Cena Degustazione del Venerdì":
- Numero prenotati standard: 20 ospiti (di cui 2 vegetariani)
- Stagione corrente: Autunno
- Fascia: Elegante (target 85,00 € a persona)
- Menù della settimana:
  1. Antipasto: Polpo verace arrosto su crema di patate a pasta gialla (per i 2 vegetariani: Carciofi dorati su crema di patate)
  2. Primo: Pasta artigianale trafilata al bronzo con crema di zucca, funghi porcini e granella di pistacchio
  3. Secondo: Guancia di manzo brasata al vino rosso (per i 2 vegetariani: Flan di carciofi e Parmigiano Reggiano 24 mesi)
  4. Contorno: Patate a pasta gialla al forno con erbe aromatiche
  5. Dolce: Cremoso di ricotta di bufala, cioccolato fondente 70% e scorza d'agrumi
  6. Vini: Rosso Elegante DOCG (Chianti Classico) + Vino da Dessert
Genera il Dossier Operativo completo per l'Economato e la Cucina e prepara la bozza email per i Capi Partita.
```
