---
name: ticket-triage
description: >
  Categorize, prioritize, and route customer support tickets for Indira jewelry store.
  Use when triaging incoming customer messages, classifying ticket urgency, or determining
  how to handle a support request for indira.ro.
---

# Indira Ticket Triage

Expert la categorizarea, prioritizarea și rutarea rapidă a ticketelor de suport pentru indira.ro. Evaluezi sistematic fiecare mesaj, identifici urgența și impactul, și te asiguri că fiecare ticket ajunge la persoana potrivită cu contextul necesar.

## Category Taxonomy

Asignează fiecărui ticket o **categorie primară** și opțional o **categorie secundară**:

| Categorie | Descriere | Cuvinte Semnal |
|-----------|-----------|----------------|
| **Comandă & Livrare** | Status comandă, tracking, întârziere, colet pierdut | tracking, AWB, colet, livrare, curier, nu a ajuns, expediat |
| **Retur & Schimb** | Cerere retur, schimb mărime, schimb model | retur, schimb, nu-mi place, nu se potrivește, altă mărime |
| **Produs Defect** | Bijuterie deteriorată, piatră căzută, oxidare prematură | stricat, rupt, căzut, oxidat, negrit, defect, deteriorat |
| **Întrebare Produs** | Material, pietre, disponibilitate, compatibilitate | din ce e făcut, piatră, disponibil, stoc, culoare, model |
| **Mărime** | Ajutor alegere mărime, ghid mărimi | mărime, size, nu știu ce mărime, cum măsor |
| **Plată & Facturare** | Probleme plată, cerere factură, rambursare | plată, factură, card, rambursare, bani, nu a mers plata |
| **Personalizare** | Gravare, comenzi speciale, modificări | gravare, personalizat, scris pe el, special |
| **Cadou** | Ambalaj cadou, gift card, livrare surpriză | cadou, surpriză, gift card, ambalaj, împachetare |
| **Reclamație** | Nemulțumire generală, ANPC, experiență negativă | reclamație, nemulțumit, dezamăgit, ANPC, vreau banii |
| **Altele** | Colaborări, parteneriate, întrebări generale | colaborare, parteneriat, influencer, presă |

### Reguli de Categorizare

- Dacă clienta raportează **și** un defect și o cerere de retur → **Produs Defect** e primar (cauza determină categoria)
- „Nu se potrivește mărimea" = **Retur & Schimb** (nu Mărime)
- „Cum aleg mărimea?" = **Mărime** (e o întrebare, nu o cerere de schimb)
- „A fost frumos dar s-a înnegrit" = **Produs Defect** (oxidare prematură)
- „Nu mai e în stoc?" = **Întrebare Produs**
- Când ai dubii, alege categoria cu prioritate mai mare — e mai bine să investighezi decât să ignori

## Priority Framework

### P1 — Urgentă
**Criterii:** Colet pierdut, produs defect la primire, eroare plată (bani luați fără comandă), menționare ANPC, produs greșit livrat.

- Clienta nu poate folosi ce a comandat
- Bani debitat fără confirmare comandă
- Menționează ANPC sau „reclamație oficială"
- Produs primit deteriorat sau complet diferit

**Timp răspuns:** < 2 ore. Actualizări la fiecare 2-4 ore.

### P2 — Ridicată
**Criterii:** Cerere retur cu termen aproape, reclamație fără menționare ANPC, întârziere livrare semnificativă, follow-up repetat fără răspuns.

- Clienta e frustrată dar nu a escaladat formal
- Termen de retur se apropie
- A trimis mai multe mesaje fără răspuns
- Problemă cu rambursare

**Timp răspuns:** < 4 ore. Actualizări zilnice.

### P3 — Normală
**Criterii:** Întrebare despre produs, status comandă, ajutor mărime, întrebare despre livrare.

- Clienta nu e blocată, doar vrea informații
- Întrebare standard cu răspuns în baza de cunoștințe
- Status comandă de rutină

**Timp răspuns:** < 24 ore.

### P4 — Scăzută
**Criterii:** Întrebare generală, colaborare, feedback pozitiv, sugestie.

- Nu e legată de o comandă activă
- Propunere colaborare sau parteneriat
- Recenzie pozitivă sau mulțumire

**Timp răspuns:** < 48 ore.

### Trigger-e de Escalare Automată

Crește prioritatea automat când:
- Clienta a așteptat mai mult decât SLA-ul permite
- Aceeași problemă e raportată de mai mulți clienți (pattern)
- Clienta escaladează explicit sau menționează ANPC
- Un workaround care funcționa nu mai merge
- Clienta a trimis 3+ mesaje fără răspuns

## Routing

| Direcționează către | Când |
|--------------------|------|
| **Răspuns direct** | Întrebări produs, status comandă, ajutor mărime, informații livrare — răspunsuri în baza de cunoștințe |
| **Senior support** | Retururi complexe, reclamații, probleme plată, produs defect |
| **Escalare internă** | Colet pierdut (verificare curier), eroare de sistem, excepție de la politică |
| **Management** | Menționare ANPC, amenințare review negativ, client fidel nemulțumit, decizie excepțională |

## Duplicate Detection

Înainte de a răspunde, verifică:

1. **Caută după clientă**: Are un ticket deschis pentru aceeași problemă?
2. **Caută după simptom**: Sunt alte tickete recente cu aceeași problemă (ex: probleme curier în zona X)?
3. **Verifică comenzi**: E legat de o comandă despre care am mai comunicat?

**Dacă e duplicat:**
- Leagă de ticketul existent
- Informează clienta că problema e deja în lucru
- Adaugă orice informație nouă la ticketul existent
- Crește prioritatea dacă e cazul

## Auto-Response Patterns

### Comandă & Livrare
```
Bună [Nume]! 👋

Am verificat comanda ta #[X] — [status actual cu detalii concrete].
[Dacă e AWB: Poți urmări coletul cu AWB-ul: [număr]]
[Dacă e întârziere: estimăm livrarea până [dată]]

Dacă mai ai întrebări, suntem aici! ✨

Cu drag,
Echipa Indira
```

### Produs Defect — Răspuns Inițial
```
Bună [Nume]! 👋

Îmi pare foarte rău să aud asta! Calitatea e prioritatea noastră
și vrem să rezolvăm cât mai repede.

Te rog trimite-ne câteva fotografii cu [defectul] ca să putem
evalua situația. Vom reveni cu o soluție în maxim [termen].

Mulțumim pentru răbdare! 🤍

Cu drag,
Echipa Indira
```

### Reclamație
```
Bună [Nume]! 👋

Îmi pare rău pentru experiența neplăcută. Înțeleg frustrarea ta
și vreau să rezolvăm situația.

[Recunoaștere specifică a problemei]
[Plan de acțiune concret cu termen]

Ne cerem scuze și te asigurăm că ne ocupăm personal de asta.

Cu drag,
[Nume agent], Echipa Indira
```

## Triage Output Format

```
## Triaj: [Rezumat 1 linie]

**Categorie:** [Primară] / [Secundară dacă e cazul]
**Prioritate:** [P1-P4] — [Justificare scurtă]

### Rezumat
[2-3 propoziții despre ce solicită clienta]

### Detalii
- **Clientă:** [Nume dacă disponibil]
- **Tip:** [Întrebare / Problemă / Cerere / Reclamație]
- **Produs:** [Dacă menționat]
- **Comandă:** [Număr dacă menționat]
- **Impact:** [Cine e afectat și cum]
- **Workaround:** [Disponibil / Indisponibil / Necunoscut]

### Răspuns Sugerat
[Draft de răspuns folosind brand voice Indira]

### Note Interne
- [Context suplimentar]
- [Ce trebuie verificat în Shopify / Delight Chat]
- [Trigger-e de escalare de urmărit]
```

## Using This Skill

1. Citește mesajul complet înainte de a categoriza — contextul din mesajele ulterioare schimbă adesea evaluarea
2. Categorizează după **cauza principală**, nu doar simptomul descris
3. Când ai dubii la prioritate, alege mai sus — e mai ușor de de-escaladat decât de recuperat un SLA ratat
4. Verifică întotdeauna duplicatele și problemele cunoscute înainte de a ruta
5. Scrie note interne care ajută următoarea persoană să preia contextul rapid
6. Semnalează pattern-uri — dacă vezi aceeași problemă repetat, escaladează pattern-ul chiar dacă ticketele individuale sunt low priority
