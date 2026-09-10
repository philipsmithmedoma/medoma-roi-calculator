# Medoma ROI Calculator – deploy till calculator.medoma.com

Statisk sida på engelska och svenska med automatiskt språkval, inga byggsteg, ingen databas.

## 1. Repo
1. Skapa ett nytt GitHub-repo (t.ex. `medoma/roi-calculator`, privat går bra).
2. Lägg in innehållet i den här mappen (`index.html`, `favicon.svg`, `README.md`) i repots rot och pusha.

## 2. Hosting (Cloudflare Pages – gratis)
1. dash.cloudflare.com → Workers & Pages → Create → Pages → Connect to Git → välj repot.
2. Build settings: Framework preset **None**, build command tomt, output directory `/`.
3. Deploy. Du får en `*.pages.dev`-adress – verifiera att kalkylatorn fungerar där.

(Vercel fungerar likvärdigt: Add New Project → importera repot → inga build-inställningar.)

## 3. Egen subdomän
1. Cloudflare Pages → projektet → Custom domains → Add → `calculator.medoma.com`.
2. I er DNS (där medoma.com hanteras): lägg en CNAME `calculator` → `<projekt>.pages.dev`.
   Ligger DNS redan i Cloudflare sker detta automatiskt när du klickar Add.
3. Vänta på certifikatet (minuter). Klart.

## 4. Lead-formuläret
`index.html` innehåller `const LEAD_ENDPOINT = ''`.
- Tomt värde = knappen öppnar ett förifyllt mejl till info@medoma.se (fungerar direkt).
- För riktiga leads: skapa ett formulär på formspree.io (gratisnivå räcker), kopiera endpoint-URL:en
  (`https://formspree.io/f/XXXXXXX`) och klistra in som LEAD_ENDPOINT. Submissions mejlas till er.

## 5. Språk
Sidan finns i två versioner: `index.html` (engelska) och `sv.html` (svenska).
- Besökare med svensk webbläsare, eller på en .se-domän, skickas automatiskt till svenskan.
- EN · SV-växlaren uppe till höger låter besökaren byta; valet sparas i webbläsaren.
- Vid innehållsändringar: gör samma ändring i båda filerna.

## 6. Uppdateringar
Varje push till main deployas automatiskt. Ändra i `index.html`, pusha, klart efter ~1 minut.

## Kvar att göra före publik lansering
- Fyll i hakparenteserna i källnoten (n, period, verksamhet för +20 %) – syns i "How we calculate it".
- Verifiera att https://www.medoma.com/contact är rätt CTA-länk.
