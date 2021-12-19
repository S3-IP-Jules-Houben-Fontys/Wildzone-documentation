
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

<a href="#onderzoeksvraag">Onderzoeksvraag</a><br>
<a href="#1-authenticatie">1. Welke authenticatie service kan ik het beste gebruiken voor een webshop & adminpanel?</a><br>
<a href="#2-communicatie">2. Hoe zorg ik ervoor dat de onderlinge communicatie tussen microservices veilig is?</a><br>
<a href="#3-risico">3. Welke beveiligingsrisico's komen er vaak voor bij web applicaties?</a><br>
<a href="#4-testen">4. Hoe kan ik testen of mijn website veilig is?</a><br>
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

Maar welk social media account wordt het vaakst gebruikt om in te loggen op een website? Het antwoord op die vraag is volgens [Pacilio (2019)](https://www.indiehackers.com/post/social-login-do-users-prefer-google-twitter-or-facebook-here-is-what-we-ve-learned-on-cruip-com-9e98cc9bbc) met 70.99% van 33.999 gevraagde gebruikers de inlog met het Google account. Zie onderstaande afbeelding voor meer informatie:

<div align="center">
    <img src="https://user-images.githubusercontent.com/73841047/146638086-8c824038-d101-45d5-a854-b04e2a916fac.png">
</div>

Auth0 is een library die je aan je project kunt toevoegen. Auth0 zorgt ervoor dat je zelf geen authenticatie meer hoeft op te zetten. Dit heeft meerdere voordelen:
- Je hoeft je geen zorgen te maken over de veiligheid. Auth0 slaat de gebruikersgegevens op, op hun eigen beveiligde servers. Wachtwoorden worden niet opgeslagen als plain tekst, maar gehashed met bcrypt en er wordt een salt toegevoegd. [(Auth0, 2021)](https://auth0.com/pricing)
- Auth0 kan in 15 minuten geintegreerd worden in een React.js app. [(Arias, 2021)](https://auth0.com/docs/quickstart/spa/react)
- Ondersteunt het inloggen met social media accounts en tweestaps verificatie.
- Kan ook Express.js en Spring Boot API's beveiligen. [(Patrick, 2021)](https://auth0.com/docs/quickstart/backend/nodejs) / [(Anderson, 2021)](https://auth0.com/docs/quickstart/backend/java-spring-security5)

Auth0 is in mijn ogen de beste keuze voor dit project om te gebruiken als authenticatie service.

<hr>

<h2 align="center" id="2-communicatie">2. Hoe zorg ik ervoor dat de onderlinge communicatie tussen microservices veilig is?</h2>

Zoals in hoofdstuk 1 al kort aangehaald: Auth0 kan ook Express.js en Spring Boot API's beveiligen. API's zijn normaal gesproken voor iedereen toegangkelijk. Dit wil zeggen dat wanneer je weet op welke URL je een HTTP(S) request kan doen met de juiste prameters, dan kun je informatie ontvangen en versturen. Ook wanneer dit oorsponkelijk niet het idee was, bijvoorbeeld wanneer de microservices alleen onderling zouden moeten communiceren. Om ervoor te zorgen dat er niets van buitenaf de API's kan laten werken, moeten deze API's beveiligd worden. Een oplossing hiervoor is het beveiligen van de endpoints. API-endpoints zijn de specifieke digitale locaties waar verzoeken om informatie door één of meerdere programma's worden verzonden om de daar aanwezige digitale bron op te halen [(TechTarget, 2021)](https://searchapparchitecture.techtarget.com/definition/API-endpoint).

Zo'n endpoint kan dus worden afgeschermd door middel van een vereiste token. Als de gebruiker of de andere service geen of niet de juiste token heeft, dan weigert de API dit verzoek uit te voeren.

Volgens de website [REST API Tutorial](https://restfulapi.net/security-essentials/) is het verstandig om altijd HTTPS te gebruiken. De data wordt dan versleuteld en verstuurd. Bij de ontvanger wordt deze data weer ontsleuteld. Mocht iemand deze data daar tussenin zien te onderscheppen, dan is deze data niet bruikbaar omdat het versleuteld is en niet zomaar ontsleuteld kan worden. Voor dit project is het echter te tijdrovend om te gebruiken, aangezien er alleen gebruik gemaakt wordt van localhost. Als dit project daadwerkelijk gepubliceerd zou worden, dan moet er 100% zeker naar een SSL certificaat gekeken worden om HTTPS te kunnen gebruiken.

Verder in het artikel zegt de website [REST API Tutorial](https://restfulapi.net/security-essentials/) dat je nooit gevoelige informatie in een URL moet zetten. URL's kunnen heel eenvoudig gelogd worden door middel van bijvoorbeeld een tool zoals wireshark. Met deze tool zou je alle HTTP en HTTPS URLs kunnen zien. Als er dus gevoelige informatie staat in de URL, dan zou iemand anders dit dus kunnen onderscheppen en lezen.

<hr>

<h2 align="center" id="3-risico">3. Welke beveiligingsrisico's komen er vaak voor bij web applicaties?</h2>

[OWASP (2021)](https://owasp.org/www-project-top-ten/) heeft een top 10 web applicatie beveiligings risico's opgesteld. Aan de hand van deze top 10 zouden developers 'eenvoudige' beveiligings risico's moeten kunnen voorkomen. De volgende 10 risico's zouden het vaakst voorkomen in 2021:

1. [**Broken Access Control**](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)<br>
    Wanneer gebruikers of services acties kunnen uitvoeren waarvoor ze oorspronkelijk geen toestemming voor hebben gekregen. Dit probleem wordt vooral veroorzaakt wanneer de gebruiker gegevens kan manipuleren. Dit kan bijvoorbeeld in de URL gebreuren:<br>
        `voorbeeld.nl/pagina?isAdmin=false`<br>
    Als de gebruiker deze URL zou aanpassen en er verder geen checks worden uitgevoerd in de back-end om te kijken of deze gebruiker ook als admin staat geregistreerd in de database, dan zou de gebruiker admin rechten kunnen verkrijgen door middel van een simpele aanpassing in de URL:<br>
        `voorbeeld.nl/pagina?isAdmin=true`<br>
    Een oplossing zou dus kunnen zijn door gevoelige informatie zoals `isAdmin=false` niet in de URL te plaatsen, maar om dit op te vragen uit de database. Een aanvaller kan (meestal) de database niet (direct) aanpassen, dus een dubbele check met de database is altijd een goed idee. Overigens is het niet slim om gevoelige informatie zoals `isAdmin=false` überhaupt mee te sturen naar de interface, dit geeft namelijk inzicht in hoe de applicatie zou werken, wat een aanvaller vervolgens weer extra opties geeft om zwakke punten te vinden.

2. [**Cryptographic Failures**](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/)<br>
    Wanneer gevoelige en/of persoonlijke informatie niet (goed) is versleuteld en beschikbaar is voor aanvallers. In Europa zijn er zogenaamde 'General Data Protection Regulations' ook wel GDPR genoemd. Deze regels geven aan welke data versleuteld moet zijn als deze opgeslagen wordt. In de inleiding werd het artikel "Claim in de maak na datalek coronatesten: 'Er is een onaanvaardbaar risico genomen'" [(NOS Nieuws, 2021)](https://nos.nl/artikel/2408387-claim-in-de-maak-na-datalek-coronatesten-er-is-een-onaanvaardbaar-risico-genomen) genoemd. Medewerkers konden de medische gegevens van familieleden en BN'ers opzoeken, wat dus inhoudt dat persoonlijke gegevens zonder reden opgevraagd konden worden én niet versleuteld bekeken konden worden. Zeker in het geval dat protocollen zoals HTTP, SMTP of FTP (wat allemaal onbeveiligde protocollen zijn) moet de data versleuteld zijn, anders kan een aanvaller alle gegevens onderscheppen en eenvoudig lezen omdat het platte tekst is.

3. [**Injection**](https://owasp.org/Top10/A03_2021-Injection/)<br>
    Wanneer een aanvaller zijn/haar eigen script/code/waardes kan gebruiken om data blijvend te veranderen of te verkrijgen. Dit is te voorkomen door ervoor te zorgen dat eventuele code onschadelijk wordt gemaakt. In het geval van SQL kan de input worden gebruikt als prameter, dit voorkomt dat er ongewenste dingen gebeuren bij het toevoegen van data. Maar ook het ophalen van data moet gecontroleerd worden. Afhankelijk van hoe de software in elkaar zit kan de code ook nog uitgevoerd worden wanneer het opgehaald wordt uit de database. In beide gevallen moet de data dus onschadelijk gemaakt zijn.

4. [**Insecure Design**](https://owasp.org/Top10/A04_2021-Insecure_Design/)<br>
    Deze is lastig te omschrijven in één regel, maar het komt neer op het volgende: De software moet van tevoren goed doordacht zijn op eventuele zwaktepunten in het systeem. Er moet vooral gekeken worden na hoe het systeem misbruikt kan worden door de rand op te zoeken. Zo wordt het voorbeeld 'scalpers' [genoemd door OWASP](https://owasp.org/Top10/A04_2021-Insecure_Design/#:~:text=Scenario%20%233%3A%20A,rejected%20such%20transactions.). Dit zijn bots die een klant kunnen nadoen en op die manier een hele voorraad kunnen opkopen in grote getalen, zodat echte klanten deze niet meer kunnen kopen. Je kunt je uiteraard alleen beveiligen tegen bestaande risico's. Scalpers zijn bijvoorbeeld relatief nieuw en sinds de corona pandemie populair. Scalpen is in 2021 nog niet illegaal, maar zorgt wel voor onvrede bij menselijke klanten die hun product niet kunnen kopen bij een webshop omdat een scalper hen is voorgeweest met een scalpingbot. 

5. [**Security Misconfiguration**](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/)<br>
    Wanneer de applicatie in productie is gegaan, maar de development accounts of standaard inloggegevens nog steeds aanwezig zijn. Ook het niet omzetten van de applicatie naar productie kan zorgen voor problemen; debug berichten komen aan bij de aanvaller, die dit vervolgens kan gebruiken om zwakheden in het systeem te vinden. Ook het niet (tijdig) updaten van de software (libraries) valt hieronder. 

6. [**Vulnerable and Outdated Components**](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/)
    Wanneer software niet (tijdig) geüpdate wordt naar een nieuwe gepatchte versie. Als er in versie 7.3.1 een zwaktepunt zit die bekend is bij de aanvaller, dan kan deze relatief eenvoudig een aanval inzetten. Als in versie 7.3.2 er een patch is voor dit zwaktepunt dan kan dit zwaktepunt eenvoudig verholpen worden door de software te updaten. Het up-to-date houden van software kan dus aanvallen voorkomen.

7. [**Identification and Authentication**](https://owasp.org/Top10/A07_2021-Identification_and_Authentication_Failures/)
    Komt veel overeen met _1. Broken Access Control_, maar nu gaat vooral om permissies en accounts. Zo is een standaard account zoals `user: admin` en `password: admin` een veel gebruikt development account, maar dus ook een zwaktepunt die gevonden en gebruikt kan worden door een aanvaller. 'Brute forcing' is een techniek die gebruikt kan worden om zo veel mogelijk gebruikersnamen en wachtwoorden in te vullen in de hoop dat minstens één combinatie toegang geeft tot het systeem. Het bijhouden van inlogpogingen en het beperken van inloggen bij verdachte pogingen helpt bij dit probleem. Een twee-factor identificatie kan ervoor zorgen dat wanneer een aanvaller op een of andere manier toch aan de inloggevens is gekomen van een gebruiker, nog niet kan inloggen omdat hij/zij deze unieke code niet heeft. 

8. [**Software and Data Integrity Failures**](https://owasp.org/Top10/A08_2021-Software_and_Data_Integrity_Failures/)
    Wanneer de applicatie klaar is om (automatisch) gecheckt te worden dan zou een aanvaller via een geïnstalleerde library of onveilige CI/CD pipeline code bewerken of inzien. Dit kan voorkomen worden door een ervaren developer te laten kijken naar de te publiceren code. Uiteraard moeten environment variabelen niet zichtbaar zijn in de CI/CD pipelines, want dan zou de aanvaller deze eenvoudig kunnen overnemen en gebruiken.

9. [**Security Logging and Monitoring Failures**](https://owasp.org/Top10/A09_2021-Security_Logging_and_Monitoring_Failures/)
    Het missen van het opslaan van alle gebeurtenissen. Wanneer er (verdachte) gebeurtenissen plaatsvinden op de website, dan is het verstandig om deze op te slaan en regelmatig (automatisch) te laten controleren. Als er veel verdachte pogingen zijn dan is er een kans dat het systeem onder vuur ligt en er binnenkort misschien een zwakke plek gevonden wordt. Het is verstandig om de plekken van verdachte input te controleren en eventueel het account / ip-adres / apparaat te verbannen van de applicatie.

10. [**Server Side Request Forgery**](https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/)
    Een aanvaller kan inzicht krijgen in de infrastructuur van de server en de applicatie. Hierdoor kunnen 'verborgen' URL's gevonden worden die niet geschikt zijn voor het publiek. Ook services met open poorten kunnen bekeken en aangepast worden.

<hr>


<h2 align="center" id="4-testen">4. Hoe kan ik testen of mijn website veilig is?</h2>
<hr>

<h2 align="center" id="conclusie">Conclusie</h2>

<hr>

<h2 align="center" id="bron">Bronnenlijst</h2>