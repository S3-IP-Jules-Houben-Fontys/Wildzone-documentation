

<h1 align="center">Fiverr research</h1>
<h2 align="center">Software ontwikkeling door externe Software developers</h2>
<br>

<div align="center">
    <img src="https://user-images.githubusercontent.com/73841047/148233162-a0e8ef37-29a2-4178-821f-4d3938678384.jpg">
</div>

<div align="center">

| Gemaakt door:           | Docent en school:     |
|-------------------------|-----------------------|
| Jules Houben \| i461249 | Leon van Bokhorst     |
| 5 Januari 2022          | Fontys Hogeschool ICT |
| Versie 1                | Software Engineering  |

</div>

<hr>

<h2 align="center">Inleiding</h2>

Als Software Developer ben je liever lui dan moe, want waarom zou je het moeilijk doen als het ook makkelijk en snel kan? In dit onderzoek wil ik gaan uitzoeken of je voor maximaal €50,- een werkende API kunt krijgen naar wens, ontworpen door mij met OpenAPI 3.0 en gerealiseerd door een externe (onbekende) software developer via Fiverr. Kan dat wel voor €50,- en hoe kan ik inschatten of de developer de opdracht wel succesvol kan ontwikkelen? Dat kun je lezen in dit onderzoek.

<h2 align="center">Inhoudsopgave</h2>

<a href="#onderzoeksvraag">Onderzoeksvraag</a><br>
<a href="#1">1. Wat verwacht ik dat de externe developer moet gaan opleveren?</a><br>
<a href="#2">2. Wat moet ik allemaal klaarzetten en ontwerpen, zodat de externe developer direct kan beginnen?</a><br>
<a href="#3">3. Welke (gemiddelde) prijzen worden er gevraagd voor welke werkzaamheden op Fiverr?</a><br>
<a href="#4">4. Voor welke developer kies ik?</a><br>
<a href="#5">5. Heeft de developer voldaan aan al mijn opgestelde eisen?</a><br>
<a href="#discussie">Discussie</a><br>
<a href="#bron">Bronnenlijst</a>

<hr>

<h2 align="center" id="onderzoeksvraag">Onderzoeksvraag</h2>

In dit onderzoek ga ik uitzoeken hoe je het beste je (delen) van je software applicatie kunt delegeren, mijn onderzoeksvraag luidt daarom als volgt:

**Kun je voor €50,- een microservice laten ontwikkelen, die gebouwd wordt aan de hand van een OpenAPI 3.0 specificatie?**


Om de hoofdvraag te kunnen beantwoorden, deel ik deze op in deelvragen:

<ul>
    <li>Wat heb ik precies nodig?</li>
    <li>Wat moet ik allemaal klaarzetten en ontwerpen, zodat de externe developer direct kan beginnen?</li>
    <li>Welke (gemiddelde) prijzen worden er gevraagd voor welke werkzaamheden op Fiverr?</li>
    <li>Voor welke developer kies ik?</li>
    <li>Heeft de developer voldaan aan al mijn opgestelde eisen?</li>
</ul>

<hr>

<h2 align="center" id="1">1. Wat verwacht ik dat de externe developer moet gaan opleveren?</h2>

Ik verwacht dat de developer aan de hand van mijn OpenAPI 3.0 specificatie de microservice kan gaan bouwen. Hieronder valt een API waarop HTTP acties uitgevoerd kunnen worden en dat de API gebruik maakt van een database. Voor de API zoek ik bij voorkeur een Express.JS developer aangezien ik hier zelf redelijk bekend mee ben. Mochten er fouten of bugs optreden dan kan ik dit, tot zekere hoogte, zelf nog oplossen mocht dit nodig zijn. Voor de database heb ik geen grote voorkeur, maar zou ik het fijn vinden als het MySQL óf MongoDB is. Met andere databases heb ik geen ervaring en wordt het opsporen en oplossen van fouten in die databases voor mij een stuk lastiger omdat ik mij daar dan eerst in moet gaan verdiepen.

Verder verwacht ik dat er testen in de API zitten, zodat ik snel kan zien of de API werkt. Deze testen moeten automatisch uitgevoerd kunnen worden met een Github action. De developer moet de basisprincipes van git begrijpen en naar mijn repository kunnen pushen. Verder wil ik de microservice in een docker container laten draaien, het zou fijn zijn als de developer dit zelf kan maken, maar is geen harde eis.

<hr>

<h2 align="center" id="2">2. Wat moet ik allemaal klaarzetten en ontwerpen, zodat de externe developer direct kan beginnen?</h2>

Aangezien ik ervanuit ga dat de developer ervaring heeft met de OpenAPI 3.0 specificatie, zal ik deze ter beschikking stellen aan de developer. De developer kan dan direct aan de slag, aangezien er niets meer ontworpen hoeft te worden. Ik vermoed dat het geen zin heeft om userstories te maken, aangezien alles duidelijk wordt uitgelegd in de OpenAPI specificatie; als deze volledig is gemaakt dan zouden alle eventuele userstories ook voltooid moeten zijn. Ik kan hoogstens mijn eigen userstory, *US-05: Als klant van Wildzone wil ik producten kunnen toevoegen aan een mandje, zodat ik niet elk product apart moet afrekenen.* eraanhangen maar daar heeft de developer niet veel aan naar mijn mening.

Er moet een repository komen waar de code naartoe gepusht kan worden. Ik wil niet dat de code direct terecht komt op main, dus deze branch zal ik afschermen. De branch 'development' wordt wel beschikbaar voor de developer. Iedere keer wanneer er op de *development*-branch gepusht wordt, zullen de tests gedraaid worden. Wanneer de *development*-branch gemerged wordt met de *main*-branch door mij, dan zal de tests nogmaals gedraaid worden en als alle tests slagen dan wordt de applicatie omgezet naar een image en geupload naar mijn docker hub repository. Er zal dus ook een docker hub repository klaar moeten staan. 

<hr>

<h2 align="center" id="3">3. Welke (gemiddelde) prijzen worden er gevraagd voor welke werkzaamheden op Fiverr?</h2>

Ik heb een aantal zoektermen gebruikt op Fiverr, met verschillende resultaten. Wat mij in eerste instantie opvalt is dat er vooral veel full-stack services worden aangeboden. Dit heb ik echter niet nodig, aangezien ik zelf de front-end van de applicatie regel. Ik heb slechts een API met database nodig. Mijn zoekopdrachten waren:

**express.js api**

https://www.fiverr.com/farhankhan488/develop-rest-api-using-node-express-and-mysql?context_referrer=search_gigs&source=top-bar&ref_ctx_id=eb1e96b84d8d5145f59aef2e8bef3ba1&pckg_id=1&pos=2&context_type=auto&funnel=eb1e96b84d8d5145f59aef2e8bef3ba1

Are you familiar with the OpenAPI 3.0 specification? I have the specification ready for you so little to no designing will be involved, all you need to do is develop the API, database and create tests for each endpoint. The code needs to be pushed to my public repository on Github, where an action automatically runs your tests to check if everything is working. It would be nice if you are familiar with Docker too, but it's not a problem if you are not.


<hr>

<h2 align="center" id="4">4. Voor welke developer kies ik?</h2>

<hr>

<h2 align="center" id="5">5. Heeft de developer voldaan aan al mijn opgestelde eisen?</h2>

<hr>



<h2 align="center" id="discussie">Discussie</h2>

In dit onderzoek heb ik alleen naar de website Fiverr gekeken voor werk. Mogelijk zijn er nog andere websites waar betere developers op te vinden zijn die het tegen een goedkopere prijs kunnen doen. Dit zou eventueel onderzocht kunnen worden in toekomstig onderzoek.

Ik heb zonder voorkennis voor een maximaal budget gekozen van €50,- eventueel extra inlezen had tot andere resultaten kunnen leiden.

<hr>

<h2 align="center" id="bron">Bronnenlijst</h2>
