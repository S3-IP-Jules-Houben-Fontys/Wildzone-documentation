
<h1 align="center">Security research</h1>
<h2 align="center">Veilige webontwikkeling</h2>
<br>

<div align="center">
    <img src="https://user-images.githubusercontent.com/73841047/146545085-097ff3b8-14cc-4bdc-a700-ed3adbd04616.png">
</div>

<hr>

<h2 align="center">Inleiding</h2>

"Claim in de maak na datalek coronatesten: 'Er is een onaanvaardbaar risico genomen'" aldus [NOS Nieuws (2021)](https://nos.nl/artikel/2408387-claim-in-de-maak-na-datalek-coronatesten-er-is-een-onaanvaardbaar-risico-genomen). Een zin die je als software developer nooit wil horen, want dat houdt namelijk in dat je een deel van je software niet goed hebt beveiligd en getest. [NOS Nieuws (2021)](https://nos.nl/artikel/2408387-claim-in-de-maak-na-datalek-coronatesten-er-is-een-onaanvaardbaar-risico-genomen) vervolgt: De data van 6,5 miljoen Nederlanders waren in te zien voor alle 26.000 medewerkers.

Hoe kan het zo zijn, dat een nationaal systeem bedoelt voor het opslaan van medische gegevens van miljoenen mensen zomaar beschikbaar is voor 26.000 (!) medewerkers? Had dit gemakkelijk voorkomen kunnen worden door bijvoorbeeld niet alle medewerkers alle gegevens te kunnen laten opvragen? Uit hetzelfde artikel van [NOS Nieuws (2021)](https://nos.nl/artikel/2408387-claim-in-de-maak-na-datalek-coronatesten-er-is-een-onaanvaardbaar-risico-genomen) komt: De persoonsgegevens hadden beter versleuteld moeten worden en het had medewerkers onmogelijk gemaakt moeten worden grote hoeveelheden data makkelijk te downloaden.

Als de oplossing zo simpel is, had de oplossing dan niet voordat de software in gebruik genomen werd geïmplementeerd moeten zijn? Hoe zorg je er eigenlijk voor dat je dit soort krantenkoppen kunt voorkomen met het goed beveiligen en testen van je gemaakte software? Dat kun je lezen in dit onderzoek.

<hr>

<h2 align="center">Leeswijzer</h2>

<hr>

<h2 align="center">Inhoudsopgave</h2>

<a href="#onderzoeksvraag">Onderzoeksvraag</a>
<a href="#1-authenticatie">1. Welke authenticatie service kan ik het beste gebruiken voor een webshop & adminpanel?</a><br>
<a href="#2-testen">2. Hoe kan ik testen of mijn website veilig is?</a><br>
<a href="3-communicatie">3. Hoe zorg ik ervoor dat de onderlinge communicatie tussen microservices veilig is?</a><br>
<a href="4-risico">4. Welke beveiligingsrisico's komen er vaak voor bij web applicaties?</a><br>
<a href="#bron">Bronnenlijst</a>

<hr>

<h2 align="center" id="onderzoeksvraag">Onderzoeksvraag</h2>

In dit onderzoek staat internet veiligheid voorop en met name de communicatie tussen twee services en het authenticatie process in een webshop. Daarom luidt de onderzoeksvraag als volgt:

**Hoe zorg ik ervoor dat mijn webshop, die gebruik maakt van microservices, zo veilig mogelijk is?**

<h3>Deelvragen</h3>

Om de hoofdvraag te kunnen beantwoorden, deel ik deze op in deelvragen:

<ul>
    <li>Welke authenticatie service kan ik het beste gebruiken voor een webshop & adminpanel?</li>
    <li>Hoe kan ik testen of mijn website veilig is?</li>
    <li>Hoe zorg ik ervoor dat de onderlinge communicatie tussen microservices veilig is?</li>
    <li>Welke beveiligingsrisico's komen er vaak voor bij web applicaties?</li>
</ul>

<hr>

<h2 align="center" id="1-authenticatie">1. Welke authenticatie service kan ik het beste gebruiken voor een webshop & adminpanel?</h2>

[Openbase (2021)](https://openbase.com/categories/js/best-react-authentication-libraries) heeft de volgende lijst aanbevolen:

1. **Auth0 (Auth0)** <br>
    Heeft een gebruikers score van 5.0 / 5. Heeft 460 Github sterren en 317 duizend wekelijkse downloads. Auth0 is voor het laatst 2 maanden geleden geüpdate.

2. **MSAL-React (Azure)** <br>
    Is gemaakt door Microsoft, heeft 2 duizend Github sterren en 67 duizend wekelijkse downloads. MSAL-React is voor het laatst 18 dagen geleden geüpdate.

3. **Auth-js (Asgardeo)** <br>
    Heeft 20 Github sterren, 766 wekelijkse downloads en is voor het laatst 19 dagen geleden geüpdate.

4. **Schematics (Oktadev)**<br>
    Heeft 55 Github sterren, 2 duizend wekelijkse downloads en is voor het laatst 9 dagen geleden geüpdate.

5. **Supertokens-auth-react** <br>
    Heet 55 github sterren, 305 wekelijkse downloads en is voor het laatst 1 maand geleden geüpdate.

6. **Redux-auth-wrapper** <br>
    Heeft 2 duizend Github sterren, 24 duizend wekelijkse downloads en is voor het laatst 9 maand geleden geüpdate.

Voor authenticatie vind ik het belangrijk om een up-to-date systeem te gebruiken. Mijn redenatie hiervoor is dat er constant 'hacks' bedacht worden. De authenticatie moet deze hacks zo veel mogelijk voor blijven en/of updates releasen zodat die zwaktepunten kunnen worden gedicht. Als zo'n authenticatie service dus maanden geen update meer heeft gekregen, dan kun je je afvragen of het systeem wel nog zo veilig is. 

Verder vind ik het belangrijk dat de authenticatie service vaak gebruikt wordt door andere gebruikers. Als een systeem vaak gebruikt wordt, dan kun je ervanuit gaan dat deze ook door bedrijven en professionals gebruikt worden. De kans dat een project met meer dan 2 duizend wekelijkse downloads nog steeds een hobby project is, lijkt mij vrij klein. 

De nummer 1, Auth0, lijkt hierdoor de beste kandidaat met relatief veel meer wekelijkse downloads dan de andere authenticatie services. Ook is Auth0 redelelijk recent geüpdate, namelijk 2 maanden geleden. Vergeleken met Redux-auth-wrapper die 24 duizend keer per week gedownload wordt, maar 9 maanden geleden voor het laatst geüpdate is geworden vallen die 2 maanden reuze mee.

### (Social) Login proces

Volgens [Auth0 (Social Login, 2021)](https://auth0.com/learn/social-login/) geeft 86 procent van de gebruikers aan last te hebben van het moeten maken van nieuwe accounts op websites. Auth0 vervolgt: Sommige van deze gebruikers verlaten de site liever dan zich te registreren, wat betekent dat het verstrekken van sociale login aan de apps het aantal registraties op de site zal verhogen. Het is dus belangrijk om voorkeur te geven om de mogelijkheid aan te bieden om in te loggen met social media. De authenticatie software moet dus de mogelijkheid hebben om sociale login toe te voegen.

Maar welk social media account wordt het vaakst gebruikt om in te loggen op een website? Het antwoord op die vraag is volgens [Pacilio (2019)](https://www.indiehackers.com/post/social-login-do-users-prefer-google-twitter-or-facebook-here-is-what-we-ve-learned-on-cruip-com-9e98cc9bbc) met 70.99% van 33.999 gevraagde gebruikers de inlog met het Google account.

Auth0 is een library die je aan je project kunt toevoegen. Auth0 zorgt ervoor dat je zelf geen authenticatie meer hoeft op te zetten. Dit heeft meerdere voordelen:
- Je hoeft je geen zorgen te maken over de veiligheid. Auth0 slaat de gebruikersgegevens op, op hun eigen beveiligde servers. Wachtwoorden worden niet opgeslagen als plain tekst, maar gehashed met bcrypt en er wordt een salt toegevoegd. [(Auth0, 2021)](https://auth0.com/pricing)
- Auth0 kan in 15 minuten geintegreerd worden in een React.js app. [(Arias, 2021)](https://auth0.com/docs/quickstart/spa/react)
- Ondersteunt het inloggen met social media accounts en tweestaps verificatie.
- Kan ook Express.js en Spring Boot API's beveiligen. [(Patrick, 2021)](https://auth0.com/docs/quickstart/backend/nodejs) / [(Anderson, 2021)](https://auth0.com/docs/quickstart/backend/java-spring-security5)



<div align="center">
    <img src="https://user-images.githubusercontent.com/73841047/146638086-8c824038-d101-45d5-a854-b04e2a916fac.png">
</div>

<hr>

<h2 align="center" id="2-testen">2. Hoe kan ik testen of mijn website veilig is?</h2>

<hr>

<h2 align="center" id="3-communicatie">3. Hoe zorg ik ervoor dat de onderlinge communicatie tussen microservices veilig is?</h2>

<hr>

<h2 align="center" id="4-risico">4. Welke beveiligingsrisico's komen er vaak voor bij web applicaties?</h2>

<hr>

<h2 align="center" id="conclusie">Conclusie</h2>

<hr>

<h2 align="center" id="bron">Bronnenlijst</h2>