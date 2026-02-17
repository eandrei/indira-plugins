---
description: Îmbunătățește agentul — knowledge base, skills și commands
argument-hint: "<ce a fost greșit și care e răspunsul corect>"
---

# Agent Improve — Indira

Îmbunătățește agentul de customer care pe baza feedback-ului din conversația curentă. Analizează ce a fost greșit, găsește fișierul potrivit (knowledge, skills SAU commands), și propune o modificare.

**IMPORTANT:** Nu salva NICIODATĂ automat. Arată ÎNTOTDEAUNA modificarea propusă și cere confirmare.

## Usage

```
/agent-improve <ce a fost greșit și care e răspunsul corect>
```

Exemple:
- `/agent-improve Răspunsul a spus 30 zile retur dar e de fapt 14 zile`
- `/agent-improve Am ratat tonul — clienta era frustrată și am fost prea casual`
- `/agent-improve Lipsește informația despre cum se curăță bijuteriile cu opale`
- `/agent-improve Template-ul de retur nu menționează că trimitem etichetă de retur`

## Workflow

### 0. Citește Convențiile

Citește `CLAUDE.md` înainte de orice modificare — conține regulile de comunicare, structura fișierelor și cele 3 straturi (knowledge, skills, commands) care trebuie să rămână consistente.

### 1. Extrage Învățătura

Din conversația curentă și input-ul utilizatorului, identifică:

- **Ce a fost greșit?** — răspunsul incorect, informația lipsă, tonul nepotrivit
- **Care e răspunsul corect?** — informația corectă sau comportamentul dorit
- **De ce contează?** — e o situație recurentă? Afectează mulți clienți?

### 2. Clasifică Tipul de Învățare

**Knowledge base** (ce știe agentul):

| Tip | Fișier Țintă | Exemple |
|-----|-------------|---------|
| Corecție politică | `knowledge/policies/` | Termen retur greșit, condiție lipsă |
| Informație produs | `knowledge/products/` | Material greșit, piatră greșită, preț schimbat |
| Lipsă proces | `knowledge/processes/` | Pas lipsă, proces schimbat |
| Ton/voce greșit | `knowledge/brand-voice.md` | Prea formal, prea casual, lipsă empatie |

**Skills** (cum se comportă agentul):

| Tip | Fișier Țintă | Exemple |
|-----|-------------|---------|
| Pattern răspuns | `skills/response-drafting/SKILL.md` | Template nou, ajustare ton, instrucțiuni KB |
| Categorizare greșită | `skills/ticket-triage/SKILL.md` | Prioritate greșită, categorie greșită |
| Cercetare insuficientă | `skills/customer-research/SKILL.md` | Sursă lipsă, proces de căutare |
| Escalare ratată | `skills/escalation/SKILL.md` | Criteriu lipsă, format incomplet |
| Expertiză produs | `skills/product-knowledge/SKILL.md` | Materiale greșite, îngrijire, mărimi |
| Articole KB | `skills/knowledge-management/SKILL.md` | Format articol, structură, reguli |

**Commands** (ce face agentul la o comandă):

| Tip | Fișier Țintă | Exemple |
|-----|-------------|---------|
| Workflow greșit | `commands/draft-response.md` | Pași lipsă, ordine greșită |
| Triaj incomplet | `commands/triage.md` | Categorii lipsă, output format |
| Cercetare incompletă | `commands/research.md` | Surse noi, structură răspuns |
| Escalare incompletă | `commands/escalate.md` | Câmpuri lipsă, format brief |
| KB article flow | `commands/kb-article.md` | Proces creare/update articol |

### 3. Verifică Consistența

**IMPORTANT:** După ce identifici fișierul de modificat, verifică dacă informația e consistentă între cele 3 straturi:

1. **Citește knowledge/** — ce date concrete există (politici, procese, produse)
2. **Citește skills/** — cum instruiește agentul să folosească acele date
3. **Citește commands/** — ce workflow urmează agentul

Dacă găsești neconcordanțe (ex: skill-ul menționează o politică veche, sau command-ul referă un fișier KB care nu există), propune **TOATE** modificările necesare, nu doar cea raportată.

### 4. Caută Fișierul Potrivit

Citește fișierele din directorul relevant și găsește locul exact unde trebuie făcută modificarea.

Dacă niciun fișier existent nu e potrivit, propune crearea unui fișier nou.

### 5. Propune Modificarea

Arată CLAR ce se schimbă:

```
## Modificare Propusă

**Fișier:** [calea completă]
**Secțiune:** [secțiunea din fișier]
**Tip:** [Adăugare / Modificare / Ștergere]

### Înainte
[Textul curent — sau „Nu există, se adaugă"]

### După
[Textul propus]

### Motivul
[De ce facem această modificare]
```

### 6. Cere Confirmare

**Întreabă EXPLICIT:**
- „Această modificare arată corect? Confirm pentru a salva."
- Dacă utilizatorul confirmă → aplică modificarea cu Edit tool
- Dacă utilizatorul ajustează → refă propunerea
- Dacă utilizatorul anulează → nu face nimic

### 7. După Confirmare

- Aplică modificarea în fișier
- Execută comanda `./commit` din directorul rădăcină al proiectului
- Afișează un rezumat:

```
✅ Baza de cunoștințe actualizată!

**Fișier modificat:** [cale]
**Ce s-a schimbat:** [rezumat scurt]

Următorul /draft-response va folosi informația actualizată.

✅ Modificările au fost commit-uite și push-uite automat via ./commit
```

## Reguli Stricte

1. **NU salva automat** — confirmă ÎNTOTDEAUNA cu utilizatorul
2. **NU șterge informații** fără confirmare — adaugă sau modifică
3. **Păstrează formatul** markdown consistent cu restul fișierelor
4. **Limba română** cu diacritice corecte
5. **Verifică consistența** între knowledge/, skills/ și commands/ — dacă modifici într-un loc, verifică celelalte
6. **Propune toate modificările** necesare dintr-o dată, nu câte una
