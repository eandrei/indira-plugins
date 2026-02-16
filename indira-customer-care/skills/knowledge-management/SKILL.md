---
name: knowledge-management
description: >
  Write and maintain knowledge base articles from resolved support issues. Use when a ticket
  has been resolved and the solution should be documented, when updating existing KB articles,
  or when creating FAQ entries, troubleshooting docs, or process documentation.
---

# Indira Knowledge Management

Expert la crearea, organizarea și menținerea conținutului din baza de cunoștințe suport. Scrii articole care sunt găsibile, scanabile, și rezolvă problemele clientelor din prima lectură. Fiecare articol bun reduce volumul de tickete viitoare.

## Article Structure

### Elemente Universale

Fiecare articol din baza de cunoștințe trebuie să includă:

1. **Titlu**: Clar, descriptiv, în cuvintele clientei (nu jargon intern)
2. **Context**: 1-2 propoziții — ce acoperă articolul și pentru cine e
3. **Conținut**: Structurat conform tipului de articol
4. **Articole Conexe**: Link-uri către conținut relevant
5. **Ultima actualizare**: Data ultimei verificări

### Reguli de Formatare

- **Headere H2, H3** pentru secțiuni scanabile
- **Liste numerotate** pentru pași secvențiali
- **Liste cu puncte** pentru elemente non-secvențiale
- **Bold** pentru termeni cheie, nume produse, acțiuni importante
- **Tabele** pentru comparații și date de referință
- **Paragrafe scurte** — 2-4 propoziții max
- **O idee per secțiune** — dacă o secțiune acoperă două subiecte, împarte-o
- **Limba română** cu diacritice corecte

## Article Types

### Politici (knowledge/policies/)

**Scop**: Documentarea regulilor oficiale Indira.

**Structură**:
```markdown
# [Numele Politicii]

## Rezumat
[1-2 propoziții — esența politicii]

## Reguli
- [Regulă 1 — clară și specifică]
- [Regulă 2]

## Excepții
- [Când se aplică excepții]

## Exemple
- [Scenariul 1]: [Ce se întâmplă]

## Întrebări Frecvente
### [Întrebare]
[Răspuns]
```

### Procese (knowledge/processes/)

**Scop**: Pași interni pentru echipa de suport.

**Structură**:
```markdown
# [Numele Procesului]

## Când Se Aplică
[Situațiile care declanșează acest proces]

## Pași
### 1. [Acțiune]
[Instrucțiune cu detalii specifice]

### 2. [Acțiune]
[Instrucțiune]

## Verificare
[Cum confirmi că procesul a fost executat corect]

## Escalare
[Când și cum escaladezi dacă procesul nu funcționează]
```

### Informații Produs (knowledge/products/)

**Scop**: Detalii tehnice și practice despre produse.

**Structură**:
```markdown
# [Topic Produs]

## Rezumat
[Ce acoperă acest articol]

## Detalii
[Informația structurată — tabele, liste]

## Întrebări Frecvente
### [Întrebare clientă]
[Răspuns]

## Când Escaladezi
[Întrebări care depășesc acest articol]
```

### Troubleshooting

**Scop**: Rezolvarea unei probleme specifice.

**Structură**:
```markdown
# [Problema — în cuvintele clientei]

## Simptome
- [Ce vede/experimentează clienta]

## Cauză
[De ce se întâmplă — explicație simplă]

## Soluție
### Opțiunea 1: [Fix principal]
[Pași]

### Opțiunea 2: [Alternativă]
[Pași]

## Prevenție
[Cum se evită pe viitor]
```

## Writing for Searchability

### Titluri Bune vs. Proaste

| Titlu Bun | Titlu Prost | De Ce |
|-----------|-------------|-------|
| „Politica de retur — termen și condiții" | „Retururi" | Specific, include cuvinte cheie |
| „Cum aleg mărimea inelului" | „Mărimi" | Include acțiunea pe care clienta o caută |
| „Inelul s-a înnegrit — ce fac?" | „Oxidare" | În cuvintele clientei |
| „Comanda nu a ajuns — pași de urmat" | „Probleme livrare" | Include simptomul exact |

### Principii de Searchability

- Include **cuvintele exacte** pe care clienta le-ar folosi
- Folosește limbaj de client, nu terminologie internă
- Include sinonime comune: „retur/returnare", „schimb/înlocuire", „mărime/size"
- Prima propoziție a articolului să reformuleze problema/topic-ul

## When to Update vs. Create New

### Actualizează Existent Când:
- O politică s-a schimbat și pașii trebuie actualizați
- Articolul e corect dar lipsește un detaliu
- Feedback indică că o secțiune e confuză
- S-a găsit o soluție mai bună

### Creează Nou Când:
- Un ticket rezolvat relevă o lacună — nu există articol pentru acest topic
- O situație nouă necesită documentare (ex: nouă metodă de plată)
- Articolul existent acoperă prea multe subiecte și trebuie împărțit

## Knowledge Base Hygiene

### Verificare Regulată
- **Lunar**: Verifică articolele cu cele mai multe accesări — sunt actualizate?
- **La fiecare schimbare de politică**: Actualizează imediat articolele afectate
- **După tickete dificile**: Întreabă-te — „Exista un articol care ar fi ajutat?"

### Semnale de Articol Învechit
- Referințe la prețuri, produse, sau politici care s-au schimbat
- Pași care nu mai corespund procesului actual
- Răspunsuri care nu mai sunt corecte
- Articol nemenționat de nimeni de 6+ luni

## Directory Structure

```
knowledge/
├── brand-voice.md          → Ton, stil, personalitate Indira
├── policies/
│   ├── shipping.md         → Politică livrare
│   ├── returns-exchanges.md → Politică retur/schimb
│   ├── payments.md         → Metode de plată
│   ├── warranty.md         → Garanție
│   └── privacy-gdpr.md    → GDPR și confidențialitate
├── products/
│   ├── collections.md      → Catalog, colecții, prețuri
│   ├── materials-care.md   → Materiale și îngrijire
│   └── sizing-guide.md     → Ghid mărimi
└── processes/
    ├── order-issues.md     → Probleme comenzi
    ├── escalation.md       → Proces escalare
    ├── complaints.md       → Gestionare reclamații
    ├── custom-orders.md    → Comenzi personalizate
    └── gifting.md          → Opțiuni cadou
```

## Using This Skill

1. Scrie pentru clienta care e frustrată și caută un răspuns — fii clară, directă, utilă
2. Fiecare articol trebuie găsibil prin cuvintele pe care clienta le-ar folosi
3. Testează articolele — urmărește pașii tu sau dă-le cuiva care nu cunoaște subiectul
4. Păstrează articolele focusate — o problemă, o soluție
5. Menține agresiv — un articol greșit e mai rău decât niciun articol
6. Urmărește ce lipsește — fiecare ticket care ar fi putut fi un articol KB e o lacună
