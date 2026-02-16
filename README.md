# Indira Plugins

Agent de customer care pentru [indira.ro](https://www.indira.ro) — răspunde la mesaje, triază tickete, cercetează și își îmbunătățește singur baza de cunoștințe.

## Instalare (3 pași, ~5 min)

### Pas 1 — Descarcă repo-ul

Deschide **Terminal** (Cmd+Space → scrie "Terminal" → Enter):

```
cd ~/Documents
git clone https://github.com/eandrei/indira-plugins.git
```

### Pas 2 — Adaugă plugin-ul în Cowork

1. **Plugins** → **Add marketplace from GitHub**
2. Introdu: `eandrei/indira-plugins`
3. Click **Sync** → instalează **indira-customer-care**

### Pas 3 — Conectează workspace-ul

1. **Work in a folder** → navighează la `Documents/indira-plugins/workspace`
2. Selectează directorul `workspace`

Gata. Agentul are acum acces la cunoștințe, și plugin-ul se actualizează automat.

---

## Comenzi disponibile

| Comandă | Ce face |
|---------|---------|
| `/draft-response` | Scrie un răspuns profesional pentru un mesaj de la client |
| `/triage` | Categorizează și prioritizează un ticket |
| `/research` | Cercetare multi-sursă pe o întrebare |
| `/escalate` | Creează un brief de escalare structurat |
| `/kb-article` | Creează sau actualizează un articol în baza de cunoștințe |
| `/agent-improve` | Îmbunătățește baza de cunoștințe pe baza feedback-ului |

---

## Cum se actualizează

Sunt **3 tipuri** de actualizări, fiecare cu un mecanism diferit:

| Ce se schimbă | Cum se actualizează | Când e disponibil |
|---------------|--------------------|--------------------|
| **Knowledge base** (politici, produse, procese) | Editezi fișierele din `workspace/knowledge/` | Instant |
| **Commands & Skills** (logica agentului) | `git commit && git push` | Automat, la push |
| **Self-improvement** (agentul se corectează singur) | `/agent-improve` → confirmă → `git push` | Instant local, permanent la push |

---

## Structura repo-ului

```
indira-plugins/
├── workspace/                ← Cowork "Work in a folder" pointează aici
│   ├── knowledge/            ← baza de cunoștințe (brand, produse, politici, procese)
│   ├── drafts/               ← draft-uri în lucru
│   ├── tickets/              ← note per ticket
│   └── research/             ← cercetări
├── indira-customer-care/     ← plugin source (instalat separat în Cowork)
│   ├── commands/
│   ├── skills/
│   └── .claude-plugin/
└── docs/
```

**Separare clară:**
- `workspace/` = ce folosește agentul la runtime (cunoștințe + fișiere de lucru)
- `indira-customer-care/` = codul plugin-ului (comenzi + skills)
