# AI-profil quiz

Ett enkelt, helt webbläsarbaserat quiz som hjälper en användare att bygga en personaliseringsprompt för AI-chattar (Claude, ChatGPT, Gemini m.fl.). Allt på svenska.

## Integritet — viktigt

Det här är en helt statisk sida. Den:

- gör **inga** nätverksanrop — typsnittet Figtree är inbakat direkt i filen, inga externa resurser laddas,
- **sparar aldrig användarens svar** (varken localStorage, cookies, server eller liknande),
- laddar **inga** externa resurser (ingen CDN, ingen analytics, inga externa typsnitt),
- är **helt körbar offline** efter att sidan laddats.

Det enda som sparas lokalt är **temapreferensen** (ljust/mörkt läge) i `localStorage` — enbart ett enda ord, aldrig något du skrivit. Svaren finns bara i minnet under tiden quizet är öppet och försvinner direkt vid omladdning. Det enda som någonsin lämnar enheten är den färdiga prompten — och bara när användaren själv klickar på "Kopiera prompt". Den här garantin förklaras också för användaren direkt i gränssnittet (på start- och slutsidan).

## Deploya på GitHub Pages

1. Lägg `index.html` och `.nojekyll` i roten av repot (t.ex. `promt-personality`).
2. Gå till repots **Settings → Pages**.
3. Under **Build and deployment → Source**, välj **Deploy from a branch**.
4. Välj branch (oftast `main`) och mapp `/ (root)`. Spara.
5. Efter en minut eller två publiceras sidan på:
   `https://<ditt-användarnamn>.github.io/<repo-namn>/`
   I ditt fall blir det ungefär: `https://jensenjr.github.io/promt-personality/`

Filen `.nojekyll` säger åt GitHub Pages att servera filerna rakt av utan Jekyll-bearbetning. För ren statisk HTML är det säkrast så.

## Bädda in i en sida (t.ex. SharePoint)

GitHub Pages serverar HTML med rätt typ, så en vanlig iframe räcker — ingen omväg behövs:

```html
<iframe
  src="https://jensenjr.github.io/promt-personality/"
  width="100%"
  height="900"
  style="border:none;"
  title="AI-profil quiz">
</iframe>
```

Justera `height` efter behov. Quizet är responsivt och fungerar ner till mobilbredd.

### Om du bäddar in i SharePoint

Använd webbdelen **Embed** och klistra in iframe-koden ovan. Eftersom innehållet nu laddas från github.io (en extern, betrodd källa över https) slipper du SharePoints inbyggda filvisare som tidigare la till en verktygsrad och nedladdningsknapp.

Obs: vissa tenants begränsar vilka externa domäner som får bäddas in via en lista över tillåtna HTML-källor (**SharePoint admin → ... → HTML Field Security**). Om iframen är blockerad kan en admin behöva lägga till `github.io` där.

## Ändra quizet

Allt ligger i en enda fil, `index.html`:

- **Frågorna** finns i arrayen `QUESTIONS` högst upp i `<script>`. Varje fråga har `id`, `category`, `question`, `type` (`text`, `single` eller `multi`) och `options`. Flervalsfrågor kan ha `allowOther: true` för ett fritextfält, och `maxSelect` för att begränsa antalet val.
- **Hur prompten byggs** styrs av funktionen `generatePrompt`.
- **Färger** ligger som CSS-variabler i `:root` (`--bg`, `--acc`, osv.) och i `CAT_CLR` för kategorifärgerna.

Frågeräknaren på startsidan räknas automatiskt utifrån antalet frågor, så du behöver inte uppdatera några siffror manuellt när du lägger till eller tar bort frågor.
