# Indira CEO Workspace

## Cine sunt

Citește `about-me.md` pentru context complet.

## Cum lucrez

Citește `working-style.md` pentru preferințe de comunicare și output.

## Brand

Citește `brand-voice.md` pentru tonul și stilul brandului Indira.

## Plugin-uri disponibile

| Plugin | Director | Ce face |
|--------|----------|---------|
| Customer Care | `indira-customer-care/` | Răspunde la mesaje, triază tickete, cercetează, îmbunătățește KB |
| Interview Analysis | `interview-analysis/` | Analizează transcrieri JTBD |

## Routing

Când primesc un task:
1. Dacă e mesaj de la clientă → deschide `indira-customer-care/` și folosește comenzile de acolo
2. Dacă e transcriere de interviu → deschide `interview-analysis/` și folosește `/analyze-jtbd`
3. Altfel → lucrează direct din workspace/

## Conectori

- **Shopify** (Prism MCP): lookup clienți/comenzi pe `indira-bijuterii.myshopify.com`
- **Shopify** (Shop MCP): căutare produse, coș
- **Google Analytics**: trafic și conversii
- **Chrome**: browsing, tracking parcele

## Convenții

- Limba cu mine: română
- Fișiere tehnice: engleză
- Documente business: română cu diacritice
- Fii concis, nu repeta ce am zis
- Întreabă înainte de a presupune
- Salvează fișierele gata de folosit, nu le descrie doar
