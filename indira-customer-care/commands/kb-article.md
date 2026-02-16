---
description: Creează sau actualizează un articol în baza de cunoștințe
argument-hint: "<problema rezolvată sau informația nouă>"
---

# KB Article — Indira

> Dacă vezi placeholder-e necunoscute, verifică [CONNECTORS.md](../CONNECTORS.md).

Creează sau actualizează un articol în baza de cunoștințe pe baza unei probleme rezolvate sau informații noi.

## Usage

```
/kb-article <problema rezolvată sau informația nouă>
```

Exemple:
- `/kb-article Am descoperit că inelele placate cu aur nu trebuie curățate cu bicarbonat`
- `/kb-article Clienta a întrebat despre garanție pentru pietre — nu aveam documentat`
- `/kb-article Procesul de retur s-a schimbat — acum acceptăm și retur prin curier`
- `/kb-article FAQ: de ce se înnegrește argintul?`

## Workflow

### 1. Analizează Input-ul

- Ce problemă a fost rezolvată sau ce informație nouă avem?
- E o situație recurentă? (dacă da, e prioritar să documentezi)
- Audiența: echipa suport intern sau conținut adaptat pentru client?

### 2. Identifică Fișierul Potrivit

Caută în `knowledge/` fișierul relevant:

| Topic | Director |
|-------|----------|
| Livrare, retur, plată, garanție, GDPR | `knowledge/policies/` |
| Materiale, pietre, mărimi, colecții | `knowledge/products/` |
| Pași interni, proceduri | `knowledge/processes/` |
| Ton, stil, personalitate | `knowledge/brand-voice.md` |

Citește fișierul existent pentru a înțelege structura și formatul.

Dacă nu există un fișier potrivit, propune crearea unuia nou cu nume descriptiv.

### 3. Propune Articolul

Folosește structura din skill-ul **knowledge-management** pentru tipul potrivit de articol.

```
## Articol Bază de Cunoștințe

**Fișier:** [calea fișierului]
**Acțiune:** [Actualizare / Creare nou]
**Secțiune:** [Unde în fișier]

### Conținut Propus
[Textul de adăugat/modificat — formatat conform standardelor]

### De Ce?
[Motivul — problemă recurentă, informație lipsă, corecție]
```

### 4. Confirmă și Aplică

Arată modificarea propusă și cere confirmare:
- „Aceasta e modificarea propusă. Arată bine?"
- Dacă da → aplică modificarea cu Edit tool
- Dacă nu → ajustează și propune din nou

### 5. După Aplicare

```
✅ Baza de cunoștințe actualizată!

**Fișier modificat:** [cale]
**Ce s-a schimbat:** [rezumat scurt]

Următorul /draft-response va folosi informația actualizată.

💡 Nu uita să commit-ezi:
git add [fișier] && git commit -m "knowledge: [descriere scurtă]"
```
