# Så fungerar AI-profil quiz — en visuell guide

> Den här filen förklarar i klartext vad appen gör, hur du rör dig genom den,
> och **exakt vad dina svar blir** i den färdiga prompten.
> Ingen programmeringskunskap krävs.

---

## På en mening

Du svarar på **10 korta steg** om dig själv och hur du vill att en AI ska
svara. Appen väver ihop svaren till en färdig text — en **"prompt"** — som du
klistrar in i din AI-chatt (Claude, ChatGPT, Gemini …) så att den förstår vem
du är och hur du vill bli bemött.

*Ordlista:* en **prompt** = den instruktion/text du ger till AI:n.

---

## 1. Helhetsbilden

Allt händer i din egen webbläsare. Inget skickas till någon server medan du
svarar, och dina svar sparas aldrig.

```text
  ┌─ DIN WEBBLÄSARE ───────────────────────────────────────────
  │
  │   Du svarar på 10 steg   ──►   en text-"prompt" byggs ihop
  │
  │   ✗ ingen server      ✗ ingen databas      ✗ ingen spårning
  │   ✗ dina svar lämnar aldrig sidan och sparas aldrig
  │
  └────────────────────────────────────────────────────────────
                       │
                       ▼   (bara när DU klickar "Kopiera prompt")
        du klistrar in prompten i Claude / ChatGPT / Gemini …
```

---

## 2. Resan genom appen

```text
   ● START  ·  startsidan
   │   "Bygg din AI-profil" + integritetslöfte
   │   ▸ knapp: "Börja bygga min profil →"
   │
   ├─▸ STEG  1/10  ·  Om dig
   ├─▸ STEG  2/10  ·  Hur du använder AI
   ├─▸ STEG  3/10  ·  Kommunikationsstil
   ├─▸ STEG  4/10  ·  Arbetsstil
   ├─▸ STEG  5/10  ·  Hur du tänker
   ├─▸ STEG  6/10  ·  Intressen & kontext
   ├─▸ STEG  7/10  ·  Mål & bakgrund
   ├─▸ STEG  8/10  ·  Vad som ska undvikas
   ├─▸ STEG  9/10  ·  Stil & exempel
   ├─▸ STEG 10/10  ·  Sista tanken
   │   ▸ knapp: "Skapa min prompt →"
   │
   ● KLAR  ·  resultatsidan
       • din färdiga prompt visas i en ruta
       • knapp: "Kopiera prompt"    • knapp: "Börja om"
       • "Granska & redigera svar ▾"  → ändra valfritt svar i efterhand
```

**Bra att veta medan du klickar dig fram:**

- En tunn **förloppsindikator** högst upp fylls i ju längre du kommer.
- **"← Tillbaka"** tar dig till föregående steg utan att tappa svar.
- Obligatoriska steg **låser "Nästa →"** tills du svarat. Valfria steg visar
  istället **"Hoppa över"**.
- **Välj ett** = ett runt val till höger fylls i (radioknapp).
  **Välj flera** = knapparna färgas när de är valda (kryssruta).

---

## 3. De 10 stegen

| Steg | Kategori | Vad steget handlar om | Hur du svarar |
|----:|----------|-----------------------|---------------|
| 1 | Om dig | Namn & roll, *(valfri)* arbetsplats, bransch, erfarenhet/expertis | Fritext + välj ett |
| 2 | Hur du använder AI | Vad du främst använder AI till | Välj flera (+ eget) |
| 3 | Kommunikationsstil | Svarslängd, ton, format | Välj ett (×3) |
| 4 | Arbetsstil | Hur mycket AI ska utmana dig, teknisk nivå | Välj ett (×2) |
| 5 | Hur du tänker | Hur du bäst tar in ny information | Välj ett |
| 6 | Intressen & kontext | Ämnen som betyder mest (upp till 5) | Välj flera (+ eget) |
| 7 | Mål & bakgrund | Dina mål just nu, övrig kontext | Fritext *(valfritt)* |
| 8 | Vad som ska undvikas | Vad som stör dig i AI-svar | Välj flera (+ eget) |
| 9 | Stil & exempel | Klistra in ett exempel på din ton | Fritext *(valfritt)* |
| 10 | Sista tanken | En önskan till din AI | Fritext *(valfritt)* |

---

## 4. Vad varje svar blir i prompten

Det här är kärnan i hela appen: varje svar hamnar i en bestämd rubrik i den
färdiga prompten. Lägg märke till att **steg 3 och steg 4 slås ihop** till
samma rubrik (`## Kommunikationsstil`).

```text
   DITT SVAR  (steg)                      BLIR I PROMPTEN

   namn & roll      (1) ┐
   arbetsplats      (1) ├──►  ## Vem jag är
   bransch          (1) │       Arbetsplats: / Område: / Expertis:
   erfarenhet       (1) ┘

   använder AI till (2) ────►  ## Hur jag använder AI

   svarslängd       (3) ┐
   ton              (3) │
   format           (3) ├──►  ## Kommunikationsstil
   teknisk nivå     (4) │       (steg 3 OCH steg 4 hamnar här!)
   utmana/feedback  (4) ┘

   inlärningsstil   (5) ────►  ## Hur jag lär mig bäst
   ämnen            (6) ────►  ## Ämnen jag bryr mig om
   mål              (7) ────►  ## Mina nuvarande mål
   bakgrund         (7) ────►  ## Kontext om mig
   stör dig         (8) ────►  ## Undvik gärna
   exempel          (9) ────►  ## Exempel på min stil
   önskan          (10) ────►  ## Stående instruktion
```

Exakt formulering, rad för rad:

| Ditt svar (steg) | Visas i prompten som |
|------------------|----------------------|
| Namn & roll (1) | Första raden under `## Vem jag är` |
| Arbetsplats (1, valfri) | `Arbetsplats: …` |
| Bransch (1) | `Område: …` (eller `Annat: …` om du valde "Annat" och skrev egen text) |
| Erfarenhet/expertis (1) | `Expertis: …` |
| Använder AI till (2) | `## Hur jag använder AI` → "Jag använder främst AI till: …" |
| Svarslängd (3) | `## Kommunikationsstil` → `- Svarslängd: …` |
| Ton (3) | `- Ton: …` |
| Format (3) | `- Format: …` |
| Teknisk nivå (4) | `- Teknisk djup: …` |
| Utmana/feedback (4) | `- Feedbackstil: …` |
| Inlärningsstil (5) | `## Hur jag lär mig bäst` |
| Ämnen (6) | `## Ämnen jag bryr mig om` |
| Mål (7, valfri) | `## Mina nuvarande mål` |
| Bakgrund (7, valfri) | `## Kontext om mig` |
| Stör dig (8) | `## Undvik gärna` (punktlista) |
| Exempel (9, valfri) | `## Exempel på min stil …` |
| Önskan (10, valfri) | `## Stående instruktion` |

**Två saker värda att veta:**

1. **Eget/"Annat"-text slås ihop.** I flervalsstegen (använder AI till, ämnen,
   stör dig) och i branschvalet kan du skriva eget i fritextfältet. Det läggs
   automatiskt till bland dina val, separerat med komma.
2. **Hoppar du över ett valfritt steg försvinner hela rubriken.** Tom ruta =
   ingen sektion i prompten. Du får alltså aldrig tomma `## rubriker`.

---

## 5. Anatomin av en färdig prompt (exempel)

Säg att någon svarar så här (och hoppar över "bakgrund" och "exempel"):

- **Namn & roll:** Jag heter Maja, frilansande UX-designer i Stockholm
- **Arbetsplats:** Northstar AB — en liten byrå som bygger appar för vårdsektorn
- **Bransch:** Kreativt & design
- **Erfarenhet:** Van — djup kunskap inom mitt område
- **Använder AI till:** Skriva & redigera, Brainstorming & idéer
- **Svarslängd:** Balanserat · **Ton:** Professionell men vänlig · **Format:** Punktlistor
- **Utmana:** Ibland — flagga bara verkliga problem · **Teknisk nivå:** Matcha nivån på min fråga
- **Inlärningsstil:** Konkret exempel först, sedan varför
- **Ämnen:** Konst & kultur, Personlig utveckling, Hälsa & välmående
- **Mål:** Lansera min egen designstudio nästa år
- **Stör dig:** För långt och utfyllt, Överdrivna reservationer & friskrivningar
- **Önskan:** Rekommendera bara ett alternativ istället för fem

Då blir den färdiga prompten exakt detta:

```text
Använd denna profil för att personalisera varje svar i vår konversation. Tillämpa den naturligt — inget behov av att nämna eller referera till denna uppsättning.

## Vem jag är
Jag heter Maja, frilansande UX-designer i Stockholm.
Arbetsplats: Northstar AB — en liten byrå som bygger appar för vårdsektorn
Område: Kreativt & design
Expertis: Van — djup kunskap inom mitt område

## Hur jag använder AI
Jag använder främst AI till: Skriva & redigera, Brainstorming & idéer.

## Kommunikationsstil
- Svarslängd: Balanserat — kontext utan överbelastning
- Ton: Professionell men vänlig
- Format: Punktlistor — jag skummar snabbt
- Teknisk djup: Matcha nivån på min fråga
- Feedbackstil: Ibland — flagga bara verkliga problem

## Hur jag lär mig bäst
Konkret exempel först, sedan varför

## Ämnen jag bryr mig om
Konst & kultur, Personlig utveckling, Hälsa & välmående

## Mina nuvarande mål
Lansera min egen designstudio nästa år

## Undvik gärna
- För långt och utfyllt
- Överdrivna reservationer & friskrivningar

## Stående instruktion
Rekommendera bara ett alternativ istället för fem
```

Lägg märke till att det inte finns någon `## Kontext om mig` eller
`## Exempel på min stil` — de stegen hoppades över, så rubrikerna föll bort.

---

## 6. Under huven (för nyfikna)

- **En enda fil:** allt ligger i `index.html`. Den innehåller tre saker:
  *struktur* (HTML), *utseende* (CSS) och *logik* (JavaScript).
- **Ingen server, ingen databas, ingen analytics.** Sidan är helt statisk.
- **Frågorna** definieras i en lista som heter `PAGES` högst upp i koden. Varje
  sida har en `category`, en `title` och en eller flera frågor (`qs`). Vill du
  ändra en fråga gör du det där.
- **Prompten** sätts ihop av funktionen `generatePrompt` — det är den som
  bestämmer rubrikerna i avsnitt 4 ovan.
- **Mörkt/ljust läge:** följer automatiskt din enhets inställning. Knappen
  uppe till höger (☀️ / 🌙) låter dig välja själv.
- **Inga omladdningar när du klickar:** att välja ett alternativ uppdaterar
  bara den knappen — sidan "hoppar" aldrig.

### Vad lagras egentligen?

| Sak | Lagras? | Var |
|-----|---------|-----|
| Dina svar | **Nej** — aldrig | Finns bara i minnet tills du laddar om |
| Den färdiga prompten | Nej | Skapas på skärmen; lämnar bara enheten om du själv kopierar |
| Ditt val av ljust/mörkt tema | Ja | `localStorage` i din webbläsare (bara temat, inget du skrivit) |

### En ärlig not om externa anrop

Sidan hämtar i nuläget typsnittet **Figtree** från Google Fonts när den laddas.
Det är ett externt anrop (din webbläsare kontaktar Google) — men det skickar
**inga** av dina svar, bara en vanlig begäran om en typsnittsfil. Inget annat
externt laddas, och ingen analytics eller spårning finns.

---

## 7. Integritet i korthet

- Dina svar **sparas aldrig** och skickas aldrig till någon server.
- Det enda som lämnar enheten är **prompten** — och bara när **du** klickar
  "Kopiera prompt".
- Det enda som lagras lokalt är ditt **temaval**, aldrig något du skrivit.
- Laddar du om sidan är alla svar borta.
