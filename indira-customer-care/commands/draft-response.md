---
description: Scrie un răspuns profesional pentru un mesaj de la client
argument-hint: "<mesajul clientului>"
---

# Draft Response — Indira

> Dacă vezi placeholder-e necunoscute, verifică [CONNECTORS.md](../CONNECTORS.md).

Scrie un răspuns profesional, cald și empatic în limba română pentru un client Indira.

## Usage

```
/draft-response <mesajul clientei sau contextul situației>
```

Exemple:
- `/draft-response Clienta întreabă dacă inelul cu safir e disponibil în mărimea 7`
- `/draft-response Reclamație — bijuteria s-a înnegrit după 2 săptămâni`
- `/draft-response Clienta vrea retur dar a trecut termenul de 14 zile`
- `/draft-response Comanda #1234 nu a ajuns, clienta e frustrată`

## Workflow

### 1. Înțelege Contextul

Analizează mesajul clientei și determină:

- **Clientă**: Cine e? Clientă nouă sau fidelă?
- **Tip situație**: Întrebare, problemă, escalare, cerere, veste proastă, veste bună
- **Urgență**: E time-sensitive? De cât timp așteaptă?
- **Canal**: Delight Chat, email, sau altceva (ajustează formalitatea)
- **Stare emoțională**: Frustrată? Confuză? Entuziastă? Neutră?

### 2. Consultă Baza de Cunoștințe

Citește fișierele relevante din `knowledge/` ÎNAINTE de a scrie răspunsul:

- Brand voice → citește ÎNTOTDEAUNA `knowledge/brand-voice.md`
- Întrebare produs → `knowledge/products/collections.md`, `knowledge/products/materials-care.md`
- Mărime → `knowledge/products/sizing-guide.md`
- Livrare → `knowledge/policies/shipping.md`
- Retur/schimb → `knowledge/policies/returns-exchanges.md`
- Plată → `knowledge/policies/payments.md`
- Garanție → `knowledge/policies/warranty.md`

### 3. Generează Draft-ul

```
## Răspuns Draft

**Către:** [Numele clientei]
**Subiect:** [Topic]
**Canal:** [Delight Chat / Email]
**Ton:** [Empatic / Informativ / Entuziast / Responsabil / Sincer]

---

[Textul răspunsului]

---

### Note Interne (nu trimite)
- **De ce acest ton:** [Raționament pentru alegerea de ton și conținut]
- **De verificat:** [Fapte sau angajamente de confirmat înainte de trimitere]
- **Factori de risc:** [Orice e sensibil la acest răspuns]
- **Follow-up:** [Acțiuni de luat după trimitere]
- **Escalare:** [Dacă ar trebui revizuit de altcineva înainte de trimitere]
```

### 4. Abordări pe Tip de Situație

**Întrebare despre produs:**
- Începe cu răspunsul direct
- Include detalii concrete (material, piatră, preț, disponibilitate)
- Oferă sugestii complementare dacă e natural

**Problemă cu comanda:**
- Recunoaște impactul asupra clientei
- Spune ce știi despre status
- Oferă workaround dacă e disponibil
- Setează așteptări pentru timeline

**Reclamație / escalare:**
- Recunoaște severitatea și frustrarea
- Asumă-ți responsabilitatea (fără scuze, fără deflecție)
- Plan de acțiune clar cu timeline
- Oferă un call dacă e cazul

**Veste proastă (stoc epuizat, nu se poate face retur):**
- Fii directă — nu ascunde vestea
- Explică sincer
- Recunoaște impactul
- Oferă alternative
- Lasă ușa deschisă

**Veste bună (comandă livrată, produs disponibil):**
- Începe cu vestea bună
- Conectează la interesul clientei
- Sugerează pași următori
- Entuziasm sincer

### 5. Quality Checks

Înainte de a prezenta draft-ul, verifică:

- [ ] Limba română cu diacritice corecte
- [ ] Tonul potrivește situația și relația cu clienta
- [ ] Nicio promisiune dincolo de ce e în baza de cunoștințe
- [ ] Referințe corecte la politici / produse
- [ ] Pași următori clari
- [ ] Lungime potrivită canalului (scurt pentru chat, mai detaliat pentru email)
- [ ] Specific cu date, sume, nume produse
- [ ] Citit din perspectiva clientei — are sens? E clar?
- [ ] Urmărește brand voice din `knowledge/brand-voice.md`

### 6. Oferă Iterații

După prezentarea draft-ului:
- „Vrei să ajustez tonul? (mai formal, mai casual, mai empatic, mai direct)"
- „Să adaug sau să scot ceva?"
- „Să-l fac mai scurt/lung?"
- „Vrei un draft pentru un alt stakeholder?"
- „Să pregătesc și un mesaj de follow-up?"
