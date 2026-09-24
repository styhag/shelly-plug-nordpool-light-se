# Shelly Plus Plug S – elprisfärg för Sverige

En svensk anpassning av Jussi Isotalos `shelly-plug-nordpool-light` (AGPL-3.0). Källkod och originallicens ingår. Priserna kommer från Elpriset just nu via den kompakta proxyn se.elpris.eu. Skriptet ändrar **bara RGB-lampan** och styr aldrig strömmen i uttaget.

## Installera

1. Använd **Shelly Plus Plug S** med firmware 1.0.7 eller senare. Anslut den till Wi-Fi och ställ in enhetens tidszon till **Europe/Stockholm** samt korrekt tid.
2. Öppna Shelly-enhetens IP-adress i webbläsaren och välj **Scripts**. Skapa ett nytt skript, till exempel `elpris-sverige-lampa`.
3. Öppna filen `shelly-plug-nordpool-light.js` i mappen `dist`, kopiera **hela** innehållet till skriptets kodfält och välj **Save**. Använd inte originalprojektets Library-URL eftersom den installerar originalversionen.
4. Välj **Start** och slå på automatisk start. Om du redan kör originalversionen för lampan: stoppa den först, annars ändrar båda skripten samma LED.
5. Öppna `http://ENHETENS-IP/script/SKRIPT-ID` i samma nätverk. Skript-ID syns under Scripts; om detta är första skriptet är det oftast `1`.
6. Välj elområde och anpassa färg- och prisgränser. **SE2 är förvalt** (Funäsdalen). Priserna anges i öre/kWh. 25 % moms är förvalt och läggs till för positiva spotpriser, liksom i originalet. Nättariff, energiskatt och elhandlarpåslag ingår inte.

Skriptet hämtar aktuell kvartsprislista från `https://se.elpris.eu`, kontrollerar tidsintervallet med absoluta tidsstämplar även när sommartid ändras och försöker hämta ett nytt pris varje kvart. Om priset inte kan läsas används felregelns färg. Den svenska konfigurationen sparas under egen nyckel `shelly-plug-sverige-light`.

## Kontroll

Öppna webbsidan för skriptet och jämför visat pris med dagens pris för ditt elområde. Om pris saknas: kontrollera enhetens tid, tidszon, internet, DNS och HTTPS-åtkomst. Enheten måste kunna nå `se.elpris.eu`. Funktionen har byggts och syntaxkontrollerats, men inte provats på fysisk Shelly. API:et är en extern tjänst; tillgänglighet och format kan ändras.

Original: https://github.com/jisotalo/shelly-plug-nordpool-light
Datakälla: https://www.elprisetjustnu.se/elpris-api
Proxy: https://se.elpris.eu/
