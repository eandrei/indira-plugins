# Indira Plugins

Agent de customer care pentru [indira.ro](https://www.indira.ro) — răspunde la mesaje, triază tickete, cercetează și își îmbunătățește singur baza de cunoștințe.

## Instalare (~5 min)

### Pas 1 — Instalează Git (o singură dată)

Deschide **Terminal** (Cmd+Space → scrie "Terminal" → Enter) și rulează:

```
git --version
```

Dacă apare o versiune (ex: `git version 2.x.x`), treci la pasul 2.

Dacă nu, macOS te va întreba dacă vrei să instalezi developer tools. Apasă **Install** și așteaptă (~2 min).

### Pas 2 — Descarcă repo-ul

În același Terminal, copiază și lipește:

```
cd ~/Documents
git clone https://github.com/eandrei/indira-plugins.git
```

### Pas 3 — Adaugă plugin-ul în Cowork

1. Deschide **Claude Cowork**
2. **Plugins** → **Add marketplace from GitHub**
3. Introdu: `eandrei/indira-plugins`
4. Click **Sync**
5. Instalează **indira-customer-care**

### Pas 4 — Conectează workspace-ul

1. În Cowork, click **Work in a folder**
2. Navighează la **Documents** → **indira-plugins** → **indira-customer-care**
3. Selectează directorul `indira-customer-care`

Gata. Agentul are acum acces la cunoștințe, comenzi și skills — totul într-un singur loc.

---

## Comenzi disponibile

| Comandă | Ce face |
|---------|---------|
| `/draft-response` | Scrie un răspuns profesional pentru un mesaj de la client |
| `/triage` | Categorizează și prioritizează un ticket |
| `/research` | Cercetare multi-sursă pe o întrebare |
| `/escalate` | Creează un brief de escalare structurat |
| `/kb-article` | Creează sau actualizează un articol în baza de cunoștințe |
| `/agent-improve` | Îmbunătățește agentul pe baza feedback-ului |

---

## Cum se actualizează

| Ce se schimbă | Cum se actualizează | Când e disponibil |
|---------------|--------------------|--------------------|
| **Knowledge base** (politici, produse, procese) | Editezi fișierele din `knowledge/` | Instant |
| **Commands & Skills** (logica agentului) | `git commit && git push` | Automat, la push |
| **Self-improvement** (agentul se corectează singur) | `/agent-improve` → confirmă → `git push` | Instant local, permanent la push |

---

## Structura repo-ului

```
indira-plugins/
├── indira-customer-care/     ← Cowork "Work in a folder" pointează aici
│   ├── CLAUDE.md             ← convenții agent
│   ├── knowledge/            ← baza de cunoștințe (brand, produse, politici, procese)
│   ├── commands/             ← workflow-uri (/draft-response, /triage, etc.)
│   ├── skills/               ← instrucțiuni de comportament
│   ├── drafts/               ← draft-uri în lucru
│   ├── tickets/              ← note per ticket
│   ├── research/             ← cercetări
│   └── .claude-plugin/       ← metadata plugin
└── docs/
```

Totul e într-un singur director — agentul are acces la cunoștințe, comenzi și skills.
