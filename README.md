# Tønder-logbog – web-app

En selvstændig web-app til at føre logbog over kørsel og ophold i Tønder og beregne befordrings- og rejsefradrag. Den kører i enhver browser uden konto, server eller Claude.

## Filer
- `index.html` – hele appen (opdatér denne fil for nye funktioner)
- `manifest.webmanifest`, `sw.js`, `icon-*.png` – gør, at den kan lægges på hjemmeskærmen og virker uden net

## Sådan virker data
- Alt gemmes automatisk på den enkelte telefon i det øjeblik, man taster. Der er ingen gem-knap.
- Hver person har sin egen logbog på sin egen telefon, også selvom alle bruger samme webadresse. Intet sendes nogen steder hen.
- Lagt på hjemmeskærmen (iPhone: Safari → Del → Føj til hjemmeskærm) beholder iOS data. Åbnet som almindelig fane i Safari kan iOS slette data efter 7 dage uden brug, så brug hjemmeskærmen.
- Tryk **Gem backup** jævnligt og vælg "Gem i Filer" → Google Drive → TØNDER/FRADRAGSBEREGNER. Appen minder om det efter 14 dage. **Indlæs backup** flytter logbogen til en ny telefon.

## Hosting (vælg én – begge er gratis)
Filerne skal ligge på en https-adresse. En HTML-fil i Google Drive kan ikke åbnes som app på telefonen.

**GitHub Pages (anbefalet, nem at opdatere)**
1. Opret en konto på github.com og et nyt repository, fx `toender-logbog` (public).
2. "Add file" → "Upload files" → træk alle filerne i denne mappe ind → "Commit changes".
3. Settings → Pages → Source: "Deploy from a branch", Branch: `main`, mappe `/ (root)` → Save.
4. Efter et minut ligger appen på `https://<brugernavn>.github.io/toender-logbog/`.
5. Ny version: upload den nye `index.html` på samme måde. Telefonerne henter den automatisk næste gang, de har net.

**Netlify Drop (hurtigst)**
Gå til app.netlify.com/drop og træk mappen ind. Opdatering: træk mappen ind igen på samme site.

## Jacob, Mary og andre
De kan bare bruge samme adresse – deres data ligger på deres egen telefon, og I ser ikke hinandens. Vil de hellere have deres egen kopi, lægger de filerne på deres egen GitHub Pages på samme måde.

## Når du opdaterer appen
- Hæv `APP_VERSION` øverst i scriptet i `index.html`.
- Bevar formatet på de gemte data (nøglen `toender-logbog` i localStorage). Nye felter skal have en standardværdi i funktionen `migrate()`, så gamle logbøger stadig kan åbnes.
