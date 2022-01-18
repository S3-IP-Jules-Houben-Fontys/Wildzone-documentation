

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
<a href="#conclusie">conclusie</a><br>
<a href="#discussie">Discussie</a>

<hr>

<h2 align="center" id="onderzoeksvraag">Onderzoeksvraag</h2>

In dit onderzoek ga ik uitzoeken hoe je het beste je (delen) van je software applicatie kunt delegeren, mijn onderzoeksvraag luidt daarom als volgt:

**Kun je voor maximaal €50,- een werkende microservice laten ontwikkelen, die gebouwd wordt aan de hand van een OpenAPI 3.0 specificatie via Fiverr?**


Om de hoofdvraag te kunnen beantwoorden, deel ik deze op in deelvragen:

<ol>
    <li>Wat heb ik precies nodig?</li>
    <li>Wat moet ik allemaal klaarzetten en ontwerpen, zodat de externe developer direct kan beginnen?</li>
    <li>Welke (gemiddelde) prijzen worden er gevraagd voor welke werkzaamheden op Fiverr?</li>
    <li>Voor welke developer kies ik?</li>
    <li>Heeft de developer voldaan aan al mijn opgestelde eisen?</li>
</ol>

<hr>

<h2 align="center" id="1">1. Wat verwacht ik dat de externe developer moet gaan opleveren?</h2>

Ik verwacht dat de developer aan de hand van mijn OpenAPI 3.0 specificatie de microservice kan gaan bouwen. Hieronder valt een API waarop HTTP acties uitgevoerd kunnen worden en dat de API gebruik maakt van een database. Voor de API zoek ik bij voorkeur een Express.JS developer met kennis van de Sequelize ORM aangezien ik hier zelf redelijk bekend mee ben. Mochten er fouten of bugs optreden dan kan ik dit, tot zekere hoogte, zelf nog oplossen mocht dit nodig zijn. Voor de database heb ik geen grote voorkeur, maar zou ik het fijn vinden als het MySQL óf MongoDB is. Met andere databases heb ik geen ervaring en wordt het opsporen en oplossen van fouten in die databases voor mij een stuk lastiger omdat ik mij daar dan eerst in moet gaan verdiepen.

Verder verwacht ik dat er testen in de API zitten, zodat ik snel kan zien of de API werkt. Deze testen moeten automatisch uitgevoerd kunnen worden met een Github action. De developer moet de basisprincipes van git begrijpen en naar mijn repository kunnen pushen. Verder wil ik de microservice in een docker container laten draaien, het zou fijn zijn als de developer dit zelf kan maken, maar is geen harde eis.

<hr>

<h2 align="center" id="2">2. Wat moet ik allemaal klaarzetten en ontwerpen, zodat de externe developer direct kan beginnen?</h2>

Aangezien ik ervanuit ga dat de developer ervaring heeft met de OpenAPI 3.0 specificatie, zal ik deze ter beschikking stellen aan de developer. De developer kan dan direct aan de slag, aangezien er niets meer ontworpen hoeft te worden. Ik vermoed dat het geen zin heeft om userstories te maken, aangezien alles duidelijk wordt uitgelegd in de OpenAPI specificatie; als deze volledig is gemaakt dan zouden alle eventuele userstories ook voltooid moeten zijn. Ik kan hoogstens mijn eigen userstory, *US-05: Als klant van Wildzone wil ik producten kunnen toevoegen aan een mandje, zodat ik niet elk product apart moet afrekenen.* eraanhangen maar daar heeft de developer niet veel aan naar mijn mening.

Er moet een repository komen waar de code naartoe gepusht kan worden. Ik wil niet dat de code direct terecht komt op main, dus deze branch zal ik afschermen. De branch 'development' wordt wel beschikbaar voor de developer. Iedere keer wanneer er op de *development*-branch gepusht wordt, zullen de tests gedraaid worden. Wanneer de *development*-branch gemerged wordt met de *main*-branch door mij, dan zal de tests nogmaals gedraaid worden en als alle tests slagen dan wordt de applicatie omgezet naar een image en geupload naar mijn docker hub repository. Er zal dus ook een docker hub repository klaar moeten staan. 

<hr>

<h2 align="center" id="3">3. Welke (gemiddelde) prijzen worden er gevraagd voor welke werkzaamheden op Fiverr?</h2>

Ik heb een aantal zoektermen gebruikt op Fiverr, met verschillende resultaten. Wat mij in eerste instantie opvalt is dat er vooral veel full-stack services worden aangeboden. Dit heb ik echter niet nodig, aangezien ik zelf de front-end van de applicatie regel. Ik heb slechts een API met database nodig. Mijn zoekopdrachten waren:

<ul>
    <li>express.js api</li>
    <li>Sequelize </li>
    <li>Sequelize api </li>
    <li>Node.js api </li>
</ul>

De volgende resultaten kwamen naarboven:


| Naam | Link | reviews | prijs | Opleiding | vertrouwen |
|------|------|---------|-------|--------|------------|
|   farhankhan488   |   https://www.fiverr.com/farhankhan488   |     5/5 :star: (4 reviews)    |    **€13,81** <br> voor *I will develop CRUD for 4 tables of your MySQL database.*    | B.Sc. - Computer Science Software Engineering *Karakoram International University, Pakistan, Graduated 2020* |   5/5, is enthousiast en neemt de tijd om de documentatie door te lezen. Wil eerst gemaakte API's laten zien voordat er afspraken over prijs gemaakt worden.      |
|  mabdullahsial    |   https://www.fiverr.com/mabdullahsial   |    4.9/5 :star: (84 reviews)     |  **€23,02** <br> voor *Contact for exact price! - Simple Frontend and Integrate premade 2 3 apis*     | B.Sc. - Mechanical Engineering *UETLahore, Pakistan, Graduated 2018* |   2/5, heeft goede reviews maar twijfel aan de echtheid van alle reviews. Opleiding heeft niets met back-end development te maken en certificaten lijken vooral front-end gericht.       |
|   codingwebninja   |   https://www.fiverr.com/codingwebninja   |     5/5 :star: (10 reviews)    |    **€18,41** <br> voor *Complete API end points of your application with database and authentication and deployment*   | Associate - Web Development *Virtual University of Pakistan, Pakistan, Graduated 2020*  |   3/5, geeft aan een 'self-taught' developer te zijn. De vraag is dan wat voor kwaliteit je terug krijgt. Hij is geslaagd aan een virtuele universiteit, maar de website voor deze universiteit ziet er niet al te best uit. Het diploma geeft tot zekere hoogte vertrouwen.    |
|  adeel_nasir    |  https://www.fiverr.com/adeel_nasir    |    5/5 :star: (12 reviews)    |   **€18,41** <br> voor *basic small api backend application*   |  Bechlor Of Computer Science *Islamia University bahawalpur, Pakistan, Graduated 2020*     |   4/5, komt betrouwbaar en vriendelijk over. Reviews lijken betrouwbaar.  |
| anasikram | https://www.fiverr.com/anasikram |  5/5 :star: (33 reviews) | **€23,02** <br> voor *Node js api with CRUD operations and connection with database.*  | Software Engineer *COMSATS University, Pakistan, Pakistan, Graduated 2020* | 3.5/5, 3 reviews door dezelfde persoon, bijna alle reviews zijn van 3 maanden geleden. |
| mudasirqazi_ | https://www.fiverr.com/mudasirqazi_ | 5/5 :star: (318 reviews) | **€9,21** <br> voor *Custom Development* | B.Sc. - Software Engineering *University of engineering & technology, Pakistan, Graduated 2014* en M.Sc. - Computer Science *National University of Computer and Emerging Sciences, Pakistan, Graduated 2018* | 5/5, heeft indrukwekkende opleidingen gevolgd en heeft veel goede en uitgebreide reviews.
| sarab_ali | https://www.fiverr.com/sarab_ali | 5/5 :star: (25 reviews) | **€9,21** <br> voor *All In One* | B.Sc. - Computer Science *University of Gujrat, Pakistan, Graduated 2020* | 4.5/5, reviews zijn uitgebreid en positief. |

Wat mij hier direct opvalt is dat alle resultaten uit Pakistan komen, of in elk geval een Pakistaanse opleiding hebben gevolgd. Verder valt ook op dat de reviews zeer uiteen lopen. Als ik zoek op alleen Nederlandse express.js developers, dan krijg ik slechts 2 resultaten met een startprijs van boven de €100,- of zelfs €2.000,-. Deze vallen dus buiten de grenzen van dit onderzoek en zijn dus niet meegenomen in bovenstaande tabel.

Ik heb alle kandidaten het volgende bericht gestuurd:

"*Are you familiar with the OpenAPI 3.0 specification? I have the specification ready for you, so little to no designing will be involved. All you need to do is develop the API, create migrations for a MySQL database and create tests for each endpoint. The API needs to be built in Express with the Sequelize ORM. The code needs to be pushed to my public repository on Github (https://github.com/S3-IP-Jules-Houben-Fontys/Wildzone-api-basket), where an action automatically runs your integration tests (endpoint tests) to check if everything is working. Everything is set-up and ready including the documentation, so you only need to develop this API. I've attached the OpenAPI specification file to this message.*"

Zoals aangegeven heb ik de <a href="https://github.com/S3-IP-Jules-Houben-Fontys/Wildzone-api-basket/blob/main/OpenAPI.yml">OpenAPI specificatie voor de basket</a> toegevoegd aan het bericht, zodat ze deze konden bekijken.

<ul>
<li> Codingwebninja en mudasIrqazi_ gaven aan het te druk te hebben met andere projecten en hebben mijn verzoek vriendelijk afgewezen.</li>

<li> AnnasIkram vroeg direct om het budget, ik heb aangegeven dat ik ongeveer €25,- wilde uitgeven. AnasIkram heeft niet meer gereageerd op mijn budget.</li>

<li> MabdullahsIal zegt de opdracht aan te kunnen en vraag om de repository en code details. Dit heb ik beide bij het eerste bericht gezet, dus MabdullahIal heeft mijn bericht niet (goed) gelezen. Nadat ik MabldullahIal de gevraagde informatie heb gegeven, heb ik geen reactie meer ontvangen.</li>

<li> Adeel_nasir gaf aan mij niet te kunnen helpen hiermee. Ik reageerde met 'okay, no problem' waarna adeel_nasir mij vriendelijk bedankte.</li>

<li> Sarab_ali reageert vriendelijk dat hij niet bekend is met de OpenAPI specificatie en de opdracht dus niet kan aannemen. Hij bedankt mij vriendelijk.</li>

<li> Farhankhan488 bedankt mij omdat ik hem overweeg en geeft aan enthousiast te zijn en zijn skills en kwaliteit van werk beschikbaar stelt.

</ul>

<hr>

<h2 align="center" id="4">4. Voor welke developer kies ik?</h2>

Mijn keuze gaat voor farhankhan488. Hij heeft een passende opleiding, eerlijke reviews (welliswaar weinig reviews) en komt oprecht over. Ook reageert hij enthousiast op mijn eerste bericht.'

Farhankkan geeft aan geen goed internet te hebben, dus vraagt mij om de opdracht uit te leggen. Na een korte uitleg verwijs ik hem door naar de OpenAPI specificatie, aangezien hier alles in staat wat er moet gebeuren. Ik vraag hem zes keer welke prijs hij vraagt voor dit project en twee keer of hij het project aan kan, geen enkele keer heb ik antwoord gekregen op mijn vragen.

Farhankhan vraagt vervolgens of ik het project kan opzetten op zij "leptop" via Teamviewer. Ik vraag hem of hij bekend is met Git(hub), waarop hij met ja antwoordt.

Voor de zevende keer vraag ik om zijn prijs, waarop hij vraagt wat mijn budget is. Ik weet dat het gebruikelijk is in Azië om af te dingen op de prijs, dus begin ik voorzichtig met een budget van €30,-. Zoals aangegeven in de hoofdvraag ben ik bereid te gaan tot €50,-. Farhankhan geeft aan dat €30,- te weinig is waarop ik de vervolgvraag stel "hoeveel meer dan?". Farhankhan geeft geen duidelijk antwoord maar geeft aan meer dan €100,-.

Dit verbaasde mij omdat ik maar één api wil en één table in de database. Dus reageerde ik het volgende: 

"*It is only one table and one api, your advertisement said you can do 4 tables with crud and make the API for €13,79, so with €30,- I'm already paying more than twice as much as you advertised you would do. I'm willing to do €40,- but that's the max for the budget.*"

Waarop Farhankhan reageert: "*If its one table and one api i will do that for you free brother*", echter stuurt hij direct achter dit bericht dat hij niet weet waar hij moet beginnen. Hierop reageerde ik:

"*No I will pay you for your work ofcourse! This is the documentation: https://documenter.getpostman.com/view/17792690/UVXjLc2y for the API, your job is to create this API so the documentation suits the API. You need to clone the repository to your device. Then you need to create the project in the cloned repository on your device. After that install the dependencies (cors, express, mysql2 and sequelize) and install the devDependencies (cross-env, dotenv, jest, nodemon, sequelize-cli and supertest). After that you can create the migrations (documentation about the sequelize migrations can be found here: https://sequelize.org/master/manual/migrations.html) for the basket and the product. When that's done you can create the controller and routes and setup the server.js. When you are finished with that you can create endpoint tests and finally push the project to my Github repository (https://github.com/S3-IP-Jules-Houben-Fontys/Wildzone-api-basket). I hope this gives you an idea where to start and how to develop this API.*"

Farhankhan begreep dit. Ik was benieuwd hoe snel hij het zou afkrijgen dus vroeg ik hem wanneer hij verwachtte klaar te zijn. Om 13:20 geeft hij aan het klaar te hebben om 18:00 (beide in Nederlandse tijd). Na 2 uur merk ik uit zijn reacties dat hij geen idee heeft hoe de OpenAPI specificatie én API documentatie werken, terwijl ik dit heb aangegeven in mijn eerste bericht en ik vaker naar de OpenAPI specificatie en API documentatie heb verwezen.

Ik had de deadline gesteld voor 18-01-2022 voor 18:00.

<hr>

<h2 align="center" id="5">5. Heeft de developer voldaan aan al mijn opgestelde eisen?</h2>


:white_large_square: **De developer kan aan de hand van de OpenAPI 3.0 specificatie de microservice bouwen.**<br>
Farhankhan lijkt de OpenAPI specificatie niet te begrijpen/kennen. Hij heeft het niet direct toegegeven, maar heeft wel gevraagd om andere documentatie (hoewel hij deze ook niet begreep).

:white_large_square: **Er kunnen HTTP acties uitgevoerd worden op de API**<br>
Dit is niet mogelijk aangezien de applicatie niet kan opstarten. Aangezien ik niet aan de geschreven code van Farhankhan wil komen, kan ik niet met zekerheid zeggen of het alleen ligt aan instellingen, of dat er meer mis is met de applicatie. In het eerste oogopslag mis ik dingen zoals migrations en tests, dus verwacht ik ook niet dat de applicatie wel gaat werken als ik de instellingen ga aanpassen.

:white_large_square: **De API maakt verbinding met een database**<br>
Als ik kijk in de config.json file, dan staan hier alle waardes hardcoded en niet overeenkomend met de database in de docker-compose.yaml die ik klaar heb gezet om gebruikt te worden. De API kan dus sowieso geen verbinding maken met een database als de service wel zou kunnen opstarten.

:white_check_mark: **Bij voorkeur wordt de API gebouwd in Express.JS met Sequelize als ORM** <br>
Farhankhan gaf aan met "Sequelize for MySQL" en Express.js gewerkt te hebben en was bereid om dit ook voor dit project te doen. Dit voldoet dus aan mijn eis.

:white_large_square: **De API werkt met MySQL of MongoDB** <br>
De applicatie werkt überhaupt niet, dus ook deze eis is niet gehaald.

:white_large_square: **De API bevat tests** <br>
De API bevat geen tests en er zijn geen dependencies gevonden die met testen te maken hebben.

:white_check_mark: **De developer moet de basisprincipes van git begrijpen en naar de repository kunnen pushen** <br>
Er zijn twee commits gedaan, de commits hebben nette namen gekregen en zijn niet al te groot.

Als laatste eis had ik dat de developer de API zou kunnen dockerizen, dit was niet meer nodig omdat ik zelf deze workflow en dockerfile al had toegevoegd.

<hr>

<h2 align="center" id="conclusie">Conclusie</h2>

De hoofdvraag was:<Br>

**Kun je voor maximaal €50,- een werkende microservice laten ontwikkelen, die gebouwd wordt aan de hand van een OpenAPI 3.0 specificatie via Fiverr?**

Van de vooraf opgestelde eisen zijn er maar 2 van de 7 eisen behaald. Verder heb ik geen werkende applicatie ontvangen. Dus nee je kunt niet voor maximaal €50,- een werkende microservice laten ontwikkelen, die gebouwd wordt aan de hand van een OpenAPI 3.0 specificatie via Fiverr.

<hr>

<h2 align="center" id="discussie">Discussie</h2>

In dit onderzoek heb ik alleen naar de website Fiverr gekeken voor werk. Mogelijk zijn er nog andere websites waar betere developers op te vinden zijn die het tegen een goedkopere prijs kunnen doen. Dit zou eventueel onderzocht kunnen worden in toekomstig onderzoek.

Ik heb zonder voorkennis voor een maximaal budget gekozen van €50,- eventueel extra inlezen had tot andere resultaten kunnen leiden.

Ik heb alleen kandidaten gekozen die al een review hadden ontvangen, dit vond ik voor dit onderzoek belangrijk omdat ik voor mijn eigen bedrijf ook niet zomaar een developer zonder reviews zou kiezen.

