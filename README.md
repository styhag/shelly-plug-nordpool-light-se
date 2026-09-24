# Shelly Plus Plug S – elprisfärg för Sverige

Få färg på lampan i en **Shelly Plus Plug S** efter aktuellt elpris i Sverige. Välj elområde **SE1, SE2, SE3 eller SE4** och ställ in egna färger och prisgränser. **SE2** är förvalt. Skriptet styr bara RGB-lampan, **inte strömmen i uttaget**.

## Tack och erkännande

Detta är en svensk anpassning av **Jussi Isotalos** originalprojekt [shelly-plug-nordpool-light](https://github.com/jisotalo/shelly-plug-nordpool-light). Han skapade grundskriptet, LED-logiken, inställningssidan och byggverktygen. Den svenska versionen ändrar prisinhämtning, elområden och förvald moms. Originalets upphovsrättsnotis och **GNU Affero General Public License v3.0 (AGPL-3.0)** finns kvar i källfilerna och `LICENSE.txt`. Tack, Jussi!

## Installera

1. Använd Shelly Plus Plug S med firmware **1.0.7 eller senare**. Ställ in tidszon **Europe/Stockholm** och korrekt tid.
2. Öppna Shelly-enhetens IP-adress i webbläsaren. Under **Scripts**, skapa ett nytt skript.
3. Kopiera hela innehållet i [`dist/shelly-plug-nordpool-light.js`](dist/shelly-plug-nordpool-light.js) till kodfältet och välj **Save** och **Start**. Slå på automatisk start. Använd inte originalets Library-URL: den hämtar originalversionen.
4. Öppna `http://ENHETENS-IP/script/SKRIPT-ID` i det lokala nätverket. Välj elområde och justera färggränser.
5. Om originalskriptet redan körs på samma enhet, stoppa det först så att inte två skript ändrar samma lampa.

Priserna visas i **öre/kWh**. Förvalet är **25 % moms**, som läggs till positiva spotpriser. Negativa spotpriser lämnas negativa, som i originalet. Elnätsavgift, energiskatt och elhandlarpåslag ingår inte. En separat svensk konfigurationsnyckel (`shelly-plug-sverige-light`) används, så originalets sparade inställningar skrivs inte över.

Priserna kommer från [Elpriset just nu](https://www.elprisetjustnu.se/elpris-api) genom [se.elpris.eu](https://se.elpris.eu/), ett kompakt API för små enheter. Skriptet väljer dagens aktuella kvart med tidsstämplar som hanterar övergången mellan sommar- och vintertid. Om aktuellt pris saknas används felregelns färg.

## Utveckling och status

`npm ci && npm run build` bygger filen i `dist/`. Denna version är byggd och syntaxkontrollerad men **inte testad på fysisk Shelly**. Kontrollera visat pris mot dagens pris för ditt elområde innan du förlitar dig på färgen. Kontrollera tid, tidszon, internet, DNS och HTTPS om inget pris visas. Den externa pristjänstens tillgänglighet och format kan ändras.

Licens: [AGPL-3.0](LICENSE.txt).
