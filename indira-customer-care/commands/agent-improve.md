---
description: Îmbunătățește baza de cunoștințe pe baza feedback-ului
argument-hint: "<ce a fost greșit și care e răspunsul corect>"
---

# Agent Improve — Indira

Îmbunătățește agentul de customer care pe baza feedback-ului din conversația curentă. Analizează ce a fost greșit, găsește fișierul potrivit, și propune o modificare.

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

### 1. Extrage Învățătura

Din conversația curentă și input-ul utilizatorului, identifică:

- **Ce a fost greșit?** — răspunsul incorect, informația lipsă, tonul nepotrivit
- **Care e răspunsul corect?** — informația corectă sau comportamentul dorit
- **De ce contează?** — e o situație recurentă? Afectează mulți clienți?

### 2. Clasifică Tipul de Învățare

| Tip | Fișier Țintă | Exemple |
|-----|-------------|---------|
| Corecție politică | `knowledge/policies/` | Termen retur greșit, condiție lipsă |
| Informație produs | `knowledge/products/` | Material greșit, piatră greșită, preț schimbat |
| Lipsă proces | `knowledge/processes/` | Pas lipsă, proces schimbat |
| Ton/voce greșit | `knowledge/brand-voice.md` | Prea formal, prea casual, lipsă empatie |
| Pattern răspuns | `skills/response-drafting/SKILL.md` | Template nou, ajustare ton |
| Categorizare greșită | `skills/ticket-triage/SKILL.md` | Prioritate greșită, categorie greșită |
| Cercetare insuficientă | `skills/customer-research/SKILL.md` | Sursă lipsă, proces de căutare |
| Escalare ratată | `skills/escalation/SKILL.md` | Criteriu lipsă, format incomplet |

### 3. Caută Fișierul Potrivit

Citește fișierele din directorul relevant și găsește locul exact unde trebuie făcută modificarea.

Dacă niciun fișier existent nu e potrivit, propune crearea unui fișier nou.

### 4. Propune Modificarea

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

### 5. Cere Confirmare

**Întreabă EXPLICIT:**
- „Această modificare arată corect? Confirm pentru a salva."
- Dacă utilizatorul confirmă → aplică modificarea cu Edit tool
- Dacă utilizatorul ajustează → refă propunerea
- Dacă utilizatorul anulează → nu face nimic

### 6. După Confirmare

- Aplică modificarea în fișier
- Afișează un rezumat:

```
✅ Baza de cunoștințe actualizată!

**Fișier modificat:** [cale]
**Ce s-a schimbat:** [rezumat scurt]

Următorul /draft-response va folosi informația actualizată.

💡 Nu uita să commit-ezi schimbarea în git:
git add [fișier] && git commit -m "knowledge: [descriere scurtă]"
```

## Reguli Stricte

1. **NU salva automat** — confirmă ÎNTOTDEAUNA cu utilizatorul
2. **NU modifica structura plugin-ului** (commands/ sau skills/) fără aprobare explicită
3. **NU șterge informații** fără confirmare — adaugă sau modifică
4. **Păstrează formatul** markdown consistent cu restul bazei de cunoștințe
5. **Limba română** cu diacritice corecte
6. **Verifică** că modificarea nu contrazice alte informații din baza de cunoștințe
