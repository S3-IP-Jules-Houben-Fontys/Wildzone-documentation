# Wildzone documentation
<p align="center">
  <img src="https://user-images.githubusercontent.com/73841047/142646426-e43dc258-e831-43ce-ae1f-9ab1f70a7ea7.png">
</p>

<p align="center">
<img src="https://user-images.githubusercontent.com/73841047/144439724-11d1bef7-fd99-49d1-a7b5-11846b5c1bdc.gif">
</p>
**Alle documentatie omtrent het Fontys Eindhoven Software Engineering semester 3 Wildzone webshop project van Jules Houben.**

---

## Inleiding
In dit project wil ik een fictieve webshop gaan bouwen voor verschillende kleding artikelen. Het doel is om hiermee aan te tonen dat ik kan laten zien dat ik begrijp hoe een JavaScript front-end werkt, dat ik dit kan combineren met een OO gebaseerde back-end taal en dat de software gedistribueerd is zodat het een grote hoeveelheid aan gebruikers tevreden kan stellen. Om dit proces voor de gebruiker zo snel en efficiënt mogelijk te maken zal er gebruik worden gemaakt van asynchrone communicatie om te voorkomen dat een gebruiker lang moet wachten. In combinatie van een intuïtieve UX moet dit ervoor zorgen dat de gebruikservaring van de website zo optimaal mogelijk is. 
De data van de gebruiker zal opgeslagen worden in een relationele database. Aangezien dit gevoelige informatie is zal er gekeken moeten worden naar verschillende beveiligingsopties om de data van de gebruiker te kunnen beschermen. 

## Leeswijzer
Deze organisatie is opgedeeld in verschillende repositories. In elke repository zit slechts één service. In de ReadMe van iedere repository kun je zien hoe de microservice opgestart kan worden, hoe deze werkt en hoe deze getest wordt. Alle inhoudelijke documentatie betreffende keuzes van programmeertalen en frameworks kun je lezen in de huidige repository. In deze ReadMe kun je de algemene lijnen van het project zien. Klik onder het volgende kopje op de verschillende onderwerpen als je meer te weten wilt komen over dat onderwerp.

---

## Content van de documentatie repository
- [UX-onderzoek](https://github.com/S3-IP-Jules-Houben-Fontys/Wildzone-documentation/blob/main/front-end.md)
- [Beveiliging onderzoek]()

---

## Inhoudsopgave ReadMe Wildzone-documentation
1. [Gedistribueerde Software](#gedistribueerde-software)
2. [Conceptueel Model](#conceptueel-model)
3. [Project Overzicht](#project-overzicht)
4. [Gedistribueerde communicatie](#gedistribueerde-communicatie)
5. [Front-end Development](#front-end-development)
6. [Back-end Development](#back-end-development)
7. [Data Behoud](#data-behoud)
8. [Kwaliteits Garantie](#kwaliteits-garantie)
9. [Software Release Managament & het gebruik van Github](#github)

---

<h2 id="gedistribueerde-software"> 1. Gedistribueerde Software </h2>

### Waarom gedistribueerde software?

Gedistribueerde software is met name belangrijk voor grote bedrijven. Deze bedrijven krijgen per seconde duizenden verzoeken. Als de software allemaal op één server zou draaien, dan zou je ongelofelijke goede hardware moeten hebben. Alle verzoeken zouden namelijk door dezelfde processor verwerkt moeten worden. Van front-end, naar de back-end, naar de database, weer terug naar de back-end om vervolgens bij de user in de front-end te kunnen eindigen. Wanneer er zoveel verzoeken zijn, is het goed voor te stellen dat de processor dit niet allemaal tegelijk kan verwerken. 

Om dit probleem op te lossen moet er gebruik worden gemaakt van meerdere servers, met ieder hun eigen rekenkracht. Zo zou je een server kunnen nemen voor alle front-end verzoeken, een server voor alle back-end verzoeken en een server voor alle database verzoeken. Dit verhoogt het aantal gebruikers dat op één moment geholpen kunnen worden, zonder dat ze op elkaar moeten wachten.

Voor kleine softwareapplicaties zijn monolieten acceptabel, deze hoeven namelijk niet duizenden verzoeken per seconde te verwerken. Echter zijn monolithische applicaties niet makkelijk uit te breiden wanneer de applicatie heel populair wordt. Het hele systeem, van voor tot achter, moet namelijk op één server gerund kunnen worden. Als er dus ergens iets fout gaat in dit proces, dan werkt de applicatie niet meer.

In het geval van gedistribueerde applicaties zijn de verschillende servers onafhankelijk van elkaar. Een server kan dus kapotgaan, zonder dat de hele applicatie hierdoor niet meer werkt. Ook zijn gedistribueerde applicaties makkelijker uit te breiden. Mocht de front-end server aan zijn limiet zitten, dan kan er eenvoudig een tweede front-end server erbij genomen worden zonder dat dit een impact heeft op de applicatie.

Het is belangrijk om de verschillende onderdelen echt volledig los van elkaar te kunnen laten draaien. In alle gevallen hoeven de servers dus niet van elkaar te weten dat ze bestaan. Het enige wat ze moeten kunnen, is het ontvangen en het versturen van data in een vooraf gedefinieerde structuur.


<h2 id="conceptueel-model"> 2. Conceptueel Model </h2>

<p align="center">
 <img src="https://user-images.githubusercontent.com/73841047/142633369-2ab19943-3055-4b29-b087-eefd82fe2910.jpg">
</p>

Er zijn 4 belangrijke onderdelen in deze webshop, namelijk:
- Supplier (leverancier)
- Product
- Inventory (inventaris)
- Category (categorie)

Met dit conceptueel model kunnen we vervolgens een inschatting gaan maken hoe vaak een entiteit gebruikt zal gaan worden. Als een entiteit vaak gebruikt wordt, dan kan het verstandig zijn om deze entiteit zijn eigen service te geven. Stel de product entiteit wordt 100x gebruikt in 1 seconde en de leveranciers entiteit maar 1x per seconde. Het kan gebeuren dat de verzoeken 1-voor-1 worden afgewerkt. Wanneer er tijdens het opvragen van een leverancier iedere keer gewacht moet worden op de voorgaande 100 producten, dan kost dit veel tijd. Door veel vragende entiteiten hun eigen service te geven, dan kun je deze wachttijd onder andere verminderen. Zodra deze entiteiten hun eigen service hebben dan kan het bijvoorbeeld zo zijn dat de 100 producten op elkaar moeten wachten, maar dat ondertussen via de leveranciers service de leverancier alvast opgehaald kan worden.
Verder zorgt het maken van microservices ervoor dat de entiteiten niet van elkaar afhankelijk zijn. Stel er gaat iets fout bij de service van de leverancier, dan werkt de service voor producten wel nog gewoon, waardoor de gebruikers de applicatie kunnen blijven gebruiken. Welliswaar zonder informatie over leveranciers, maar de applicatie ligt niet compleet uit de lucht.


<h2 id="project-overzicht"> 3. Project Overzicht </h2>

Om duidelijkheid te creeren in dit project, wordt er gebruik gemaakt van de zogenaamde *C4-method*. De C4 methode is ontworpen om de software architectuur overzichtelijk in kaart te brengen voor zowel opdrachtgever als voor software engineers. De C4 methode bestaat uit 4 verschillende diagrammen, waarbij ieder diagram net iets dieper inzoomt op de software die ontwikkeld moet worden. De volgende onderdelen komen voor in de C4 methode:

- Context (level 1, geschikt voor iedereen; er is geen tot weinig technische kennis nodig om het diagram volledig te kunnen begrijpen)
- Containers (level 2, geschikt voor mensen met eenvoudige technische kennis; er worden technische ondedelen benoemd, maar moet begrijpelijk zijn voor mensen met eenvoudige technische kennis)
- Components (level 3, geschikt voor mensen met technische kennis; geeft een algemeen duidelijk beeld uit welke onderdelen/microservices het software systeem bestaat. Niet geschikt voor opdrachtgevers)
- Components (level 4, geschikt voor software egineers; geeft de werking van één enkele microservice weer tot in de details. Alleen geschikt voor software egineers)

---

### C1: Context

Zie onderstaande diagram voor de context van dit software systeem.

![Wildzone-C1 System Context diagram drawio (2)](https://user-images.githubusercontent.com/73841047/143442490-e2176763-8095-4cc2-8e0b-d8d9d8ba5ce7.png)

---

### C2: Containers

Als we iets verder inzoomen op het software systeem dat ontwikkeld moet worden, dan komen we uit bij de onderstaande diagram:

![Wildzone-C2 Container diagram drawio (1)](https://user-images.githubusercontent.com/73841047/143568140-c76727dd-a143-4314-a849-59b308bba449.png)

---

### C3: Components

![Wildzone-C3 Component diagram drawio](https://user-images.githubusercontent.com/73841047/143583232-469492a1-5c13-49ce-8662-ad572f6668a3.png)

---

<h2 id="gedistribueerde-software">Gedistribueerde communicatie</h2>

In dit project wordt er gebruik gemaakt van microservices. Dit houdt in dat alle services los van elkaar kunnen draaien, zonder dat ze van elkaars bestaan afweten. Echter moeten de verschillende services wel met elkaar kunnen communiceren. Want hoe kunnen ze anders ervoor zorgen dat er in het magazijn de melding komt dat product *X* is gekocht door klant Peter?

Er zijn een paar manieren om te communiceren met een microservice. De bekendste manier is JSON. JSON (JavaScrip Object Notation) is eenvoudig, snel, gratis en werkt met vrijwel elke back-end taal. Daarbij wordt het ondersteund door elke browser.

Een andere manier is XML. XML (Extensible Markup Language) was vroeger een veel gebruikte data overbrenger tussen systemen. Echter is XML bulky en langzaam in ontleden, wat ervoor zorgt dat de laadsnelheid flink omlaag gaat en de opslag omhoog. Verder maakt XML geen gebruik van tags, dus moet de code heel goed gedocumenteerd worden, aangezien de waardes niet altijd vanzelfsprekend zijn.

Voor dit project wordt JSON gebruikt omdat hier meer voordelen aan zitten als aan XML. Daarbij is JSON een EMCA standaard.

### Wat is REST?

REST staat voor **RE**presentational **S**tate **T**ransfer en is een architecturele stijl voor een [API](#api). REST is een nette en eenvoudige naam om te zeggen dat de applicatie de standaard HTTP acties accepteert. Denk hierbij aan Creat, Read, Update, Delete etc. Door middel van de URL kunnen de verschillende acties uitgevoerd worden.

<h3 id="api">Wat is een API?</h3>

API staat voor **A**pplication **P**rogramming **I**nterface en zorgt ervoor dat de opgevraagde data wordt opgehaald en afgeleverd. Je moet de API zien als een serveerder in een restaurant. Via het menu kun je zien wat je allemaal kunt vragen aan de serveerder. De keuken is de database in dit systeem; daar komt namelijk alle data, in dit geval het eten, vandaan. Je moet echter nog een manier hebben om je bestelling naar de keuken te krijgen en vervolgens je eten terug bij jou op tafel. Hiervoor dient de serveerder/api. Je geeft door welke data, in dit geval eten, je wilt hebben. De serveerder geeft het door aan de database/keuken en komt terug met de opgevraagde bestelling/data. 

Een API communiceert dus tussen twee services.

### Wat is een websocket?

Een websocket lijkt heel veel op een API. Het grote verschil is dat je een API iedere keer moet aanroepen als je deze wilt gebruiken. Bij een websocket is er een verbinding tussen twee services. Deze services kunnen elkaar berichten blijven sturen zonder dat er actief naar gevraagd moet worden. De verbinding tussen de twee services wordt gestart met een zogenaamde *handshake*, die aangeeft op welke locatie en poort ze met elkaar verbonden zijn. Deze handshake wordt pas verbroken zodra een van de twee services wegvalt.

Omdat de connect open blijft staan zit er vrijwel geen vertraging tussen het sturen van de berichten tussen de twee services. Dit is bijvoorbeeld handig als je een chatfunctie wilt toevoegen aan je applicatie. De websocket krijgt automatisch bericht wanneer de data is veranderd. In tegenstelling tot een API, waar je bij iedere update een nieuw verzoek moet sturen. Je zou om de zoveel seconden zo'n request kunnen uitvoeren, maar dat is niet heel efficiënt. In zo'n geval komt een websocket goed van pas.

### Wat is Postman?

Postman wordt gebruikt om de API's te testen en te documenteren. Je kunt namelijk heel eenvoudig HTTP acties aanmaken met Postman om te kijken of de API daadwerkelijk de gewenste output geeft. Zodra al deze acties zijn aangemaakt, dan kun je hier heel eenvoudig automatisch documentatie voor laten maken door Postman. Dit is vergelijkbaar met een andere tool genaamd Swagger. 

---

<h2 id="front-end-development">Front-end Development</h2>

### JavaScript Frameworks

#### Waarom een JavaScript framework?

Voor JavaScript zijn er inmiddels minstens 24 frameworks [(Huspi, 2019)](https://huspi.com/blog-open/what-javascript-framework-to-choose-in-2020-a-comparison/), met ieder als doel om programmeren in JavaScript beter te maken. Je kunt natuurlijk ook vanilla Javascript gebruiken; slechts het gebruik van de taal, zonder toevoegingen. De vraag is echter waarom je dit zou doen. Stel je wilt een kledingkast gaan bouwen. Je kunt ieder onderdeel helemaal zelf maken door een boom in het bos uit te zoeken, deze om te zagen, hiervan planken te maken, deze planken schuren, verven, gaten te boren, zelf pluggen maken, om vervolgens de kast in elkaar te kunnen zitten. Óf je kunt natuurlijk naar de IKEA gaan, waar de planken geverfd, met instructies en assemblage materiaal in één doos zitten die je vervolgens gemakkelijk in één middagje in elkaar kunt zetten. Een kast bij de IKEA kopen is dus vergelijkbaar met het gebruiken van een framework; standaard, saai en soms lastig werk is al voor je gedaan. Het enige wat je nu nog hoeft de doen is het zelf in elkaar zetten van de onderdelen naar wens.

Een framework kan je dus veel tijd besparen door je werk uit handen te nemen die goed geautomatiseerd kan worden.

Een andere reden om een framework te nemen in plaats van pure Javascript is dat programmeertalen de neiging om nogal snel onoverzichtelijk en slordig te worden [(Keefer, 2015)](https://artandlogic.com/2015/05/the-what-and-why-of-javascript-frameworks/).

_Waarom zijn er dan zoveel verschillende frameworks?_

Dit heeft te maken met dat ieder framework zijn limieten kent. De een wil zijn query naar een database compleet kunnen schrijven, terwijl de ander alle informatie wil krijgen als deze slechts de instantie van een object opvraagt. Ieder framework heeft daarom zijn eigen specialiteiten en functies.

Ik heb 3 potentiële JavaScript frameworks uitgezocht, namelijk:

- React
- Vue
- Angular

![Figuur 1 Trends in zoektermen naar de 3 populairste frameworks.](https://user-images.githubusercontent.com/73841047/142627946-c2943f0f-edcd-446e-b93e-30009644d60b.png)

Dit zijn volgens Google de 3 mest populaire frameworks. Ik wil graag dat een framework veel gebruikt wordt. Wanneer deze veel gebruikt wordt is er namelijk vaak goede documentatie aanwezig en is er een actieve community die eventuele vragen snel zouden kunnen beantwoorden.

#### React

**Pro&#39;s:**

- De code is goed leesbaar en makkelijk te debuggen, dit maakt het beginnen met dit framework gemakkelijker en intuïtiever
- Maakt gebruik van een virtuele DOM. Dit zorgt ervoor dat veranderingen van data razendsnel geladen kunnen worden op de pagina, zonder deze te moeten verversen.
- React native zorgt ervoor dat op mobiele apparaten de juiste, native, content gerendered wordt in plaats van web content. Dit zorgt ervoor dat de mobiele website beter geschikt is voor het besturingssysteem waarop het bekeken wordt.
- Er wordt gebruik gemaakt van JSX, dit is een markup taal vergelijkbaar met HTML. Aangezien JSX bijna identiek is aan HTML, moet dit zorgen dat applicaties snel ontwikkeld kunnen worden.
- Componenten kunnen hergebruikt worden, waardoor DRY makkelijk toegepast kan worden.
- Volgens [(Stackoverflow, 2021)](https://insights.stackoverflow.com/survey/2021) geeft het grootste deel van de respondenten aan React te verkiezen als vaakst gebruikte framework.

**Con&#39;s:**

- Developers zeggen dat de documentatie van React beter kan zijn. Het platform zou sneller nieuwe functies krijgen, dan dat de documentatie bijgewerkt zou kunnen worden [(Bonder, 2020)](https://www.talentopia.com/front-end/the-pros-and-cons-of-the-most-used-javascript-frameworks)
- Mocht het nodig zijn om een complexe applicatie te maken, dan zal er veelal gebruik gemaakt moeten worden van 3rd party packages.

**Twijfel**

- Volgens [(Reis, 2020)](https://www.imaginarycloud.com/blog/angular-vs-react/)heeft React een gemakkelijkere learning curve dan Angular.
- Volgens [(Bonder, 2020)](https://www.talentopia.com/front-end/the-pros-and-cons-of-the-most-used-javascript-frameworks) heeft React een steile learning curve.

#### Vue

**Pro&#39;s:**

- Maakt gebruik van een virtuele DOM. Dit zorgt ervoor dat veranderingen van data razendsnel geladen kunnen worden op de pagina, zonder deze te moeten verversen.
- Maakt het makkelijk om animaties toe te voegen
- Is simpel om te gebruiken en zou beginner-friendly zijn

**Con&#39;s:**

- Vue is nog erg nieuw, waardoor de community nog niet heel groot is, hierdoor mis je experts, plugins en support.
- Mobiele support is niet eenvoudig [(Grankin, 2020)](https://ddi-dev.com/blog/programming/the-good-and-the-bad-of-vue-js-framework-programming/)

**Twijfel:**

- Doordat Vue nog zo nieuw is en er zo weinig support is, is het niet aan te raden om hele grote projecten te maken. Voor kleine projecten zou dit niet veel moeten uitmaken

#### Angular

**Pro&#39;s:**

- Typescript lijkt veel op de standaard OOP-talen zoals C#, dit zou een deel van de learning curve moeten wegnemen.
- De documentatie van Angular is lang en uitgebreid.
- Je kunt gebruik maken van Angular/material, waardoor het design gebaseerd is op Google&#39;s Material Design om zo een snel en werkende UI elementen te kunnen maken.
- Applicaties zouden heel snel laden.

**Con&#39;s:**

- Angular heeft geen officiële support voor mobiele app development [(Reis, 2020)](https://www.imaginarycloud.com/blog/angular-vs-react/).
- Geeft je beperkte vrijheid in het organiseren van de code.

**Twijfel:**

- Angular is heel uitgebreid. Dit zorgt ervoor dat het hele specifieke onderdelen kan oplossen, maar de kans is groot dat deze ondersteuning niet nodig zal zijn voor dit project.

#### Conclusie

Ik heb besloten om te gaan met React, dit omdat deze gemakkelijk te debuggen zou zijn en dat het grootste deel van de professionele developers React verkiezen boven alle andere frameworks. Dit laat React op mij overkomen dat dit framework wordt vertrouwd en gebruikt door een grote groep developers. Doordat de community zo groot is en nog steeds aan het groeien is, is de con &quot;Developers zeggen dat de documentatie van React beter kan zijn. &quot; minder belangrijk aangezien de community dan altijd om hulp gevraagd kan worden. Verder is het belangrijk dat er goede mobiele support is, aangezien inmiddels 54,8% van het internetverkeer via mobiele apparaten plaats vindt [(Statista, 2021)](https://www.statista.com/statistics/277125/share-of-website-traffic-coming-from-mobile-devices/)

### UX voor software engineers: de basis

Voor een leek is UI en UX precies hetzelfde, want &quot;het heeft allebei met de voorkant van een applicatie te maken&quot;. Tot zekere hoogte klopt dit. Echter is er een groot wezenlijk verschil tussen de twee.

UI staat voor &#39; **U** ser **I** nterface&#39;, de interface is dus vooral wat de gebruiker ziet. Denk hierbij aan kleuren, afbeeldingen, lettertypen en iconen.


UX staat voor &#39; **U** ser e **X** perience&#39;, dit is wat gebruiker ervaart tijdens het gebruik van de app. De gebruiker &#39;ziet&#39; dit veelal niet. Denk hierbij aan het uitzoeken waar knoppen moeten komen, of het aantal kliks optimaliseren zodat de gebruiker sneller en eenvoudiger bij de gewenste pagina kan uitkomen

UI en UX zijn goed te vergelijken met een ijsberg; De top, de UI is zichtbaar voor de gebruiker, de rest van de ijsberg is voor de gebruiker niet te zien maar is wel degelijk aanwezig (Ditmeyer).

Als de ervaring met de applicatie niet goed wordt bevonden door de gebruiker, dan is het onwaarschijnlijk dat gebruiker de applicatie vaker zal gebruiken. Stel een deurklink zou je iedere keer een schok geven wanneer je de deur wilt openen. Het doel, de deur openen, kan nog altijd bereikt worden. Echter zal de gebruiker deze stap niet vaker willen herhalen, aangezien deze een negatieve ervaring heeft gehad met het gebruik van deze deurklink. UI kan slechts het uiterlijk van de deurklink veranderen. Of deze nu donkerpaars is of muntgroen dat maakt niet uit, de ervaring verandert namelijk niet. UX kan ervoor zorgen dat deze ervaring wel beter wordt, door bijvoorbeeld de deurklink niet meer onder stroom te zetten. In dit geval kan de gebruiker eenvoudig zijn doel bereiken, zonder hier negatieve ervaringen aan over te houden.

![Figuur 2 UI en UX zijn goed te vergelijken met een ijsberg (Ditmeyer)](https://user-images.githubusercontent.com/73841047/142628269-6023754b-e5d4-4266-9905-7b2ed9fda2fa.png)

#### Hoe ga ik UX aantonen in mijn project?

Voor een webshop is het belangrijk dat er producten verkocht worden via de website. Ik heb twee punten uitgekozen die voor mij het belangrijkste zijn:

- Snel producten kunnen toevoegen en naar de afrekenpagina kunnen.
- Laadsnelheid van de website.

#### Snel producten kunnen toevoegen en naar de afrekenpagina kunnen

De gebruikerservaring moet zo optimaal mogelijk zijn. Wanneer een potentiële klant iets wil kopen op een webshop, dan moet deze hierin zo min mogelijk gehinderd worden. In een fysieke winkel heb je tenslotte ook geen obstakels en knoppen waar je langs moet voordat je naar de kassa kunt gaan. Zodra een potentiële klant weet waarvoor hij op de website is, dan zou deze het product in maximaal 5[^1] kliks moeten kunnen kopen.

Als de gebruiker maar moet blijven klikken zonder deze het idee heeft dat de kliks zinvol zijn, dan zal de gebruiker dit als onprettig ervaren; de webshop is de tijd van de gebruiker aan het verdoen en tijd is geld. Gebruikers moeten tevreden zijn met de keuze dat ze in zee zijn gegaan met deze webshop. Als de gebruiker onzeker is over die keuze dan kan dit ervoor zorgen dat de aankoop niet doorgaat, waardoor de webshop geld misloopt.

[^1]: Met kliks worden alleen knoppen en linkjes bedoeld.

#### Laadsnelheid van de website

![Figuur 3 Overzicht van score per categorie van Google Lighthouse (Tune the web, 2021)](https://user-images.githubusercontent.com/73841047/142628557-f26e9b55-4780-408b-84c5-0d61bcb6fc9f.png)


De laadsnelheid is goed voor onder andere SEO en gebruiksvriendelijkheid. Om dit te testen wil ik Google&#39;s Lightouse gaan gebruiken. Dit is een eenvoudige tool om snel inzicht te krijgen hoe de website presteert. Ik wil minstens een performance score halen van 80. Dit zou betekenen dat de performance van de webshop in de top 10 procent van alle websites zou zitten.

Aangezien webshops veelal in een zeer competatieve markt zitten is het belangrijk om van de concurrenten te winnen. Het hoeft niet de mooiste website te zijn, zolang de performance (en in dit geval de laadsnelheid) maar goed is.

---

<h2 id="back-end-development">Back-end Development</h2>

Volgens [Laura Fitzgibbons](https://whatis.techtarget.com/definition/front-end#:~:text=The%20back%20end%20refers%20to,be%20accessed%20by%20a%20user.&text=The%20back%20end%20is%20also,navigated%20to%20by%20digital%20means.) is de defnitie van *software back-end* het volgende:

> *De back-end verwijst naar delen van een computertoepassing of de code van een programma die het mogelijk maken om te werken en die niet toegankelijk zijn voor een gebruiker. De meeste gegevens en bedieningssyntaxis worden opgeslagen en geopend in de back-end van een computersysteem. Meestal bestaat de code uit één of meer programmeertalen. De back-end wordt ook wel de datatoegangslaag van software of hardware genoemd en bevat alle functionaliteit die met digitale middelen moet worden benaderd en waarnaar moet worden genavigeerd.*

Of, simpel gezegd, code die uitgevoerd wordt door de computer zonder dat een gebruiker hierbij kan en dit direct kan aansturen. De back-end zit tussen de [front-end](#front-end-development) en de [database](#data-behoud) in. In de front-end wordt er data door de gebruiker opgevraagd, de back-end bekijkt dit verzoek en haalt de data op uit de database. De data van de database kan in de back-end worden bewerkt en omgezet als dit nodig is, om vervolgens teruggeven te worden aan de front-end zodat de gebruiker de opgevraagde gegevens ontvangt.

### Wat is een back-end framework en wat kan je ermee?

Frameworks zijn, zoals eerder genoemd in het hoofdstuk [Front-end Development](#front-end-development), kan een framework veel tijd besparen door je werk uit handen te nemen dat goed geautomatiseerd kan worden. Je hoeft dus niet meer de *boilerplate* code te schrijven. Dit is code die je voor ieder project opnieuw moet maken, maar vrijwel altijd *precies* hetzelfde is. De absolute basis om het zo te noemen om je project te starten.

Back-end frameworks zijn goed te vergelijken met front-end frameworks. Het grote verschil met een front-end framework is dat het niet gaat om de communicatie met de gebruiker, maar communicatie met de database. Een back-end framework zal dus vooral het verbinden en het verkrijgen van data van en met een database eenvoudiger maken.

Aangezien er API's / websockets gemaakt moeten worden, heb ik besloten niet één, maar twéé back-end frameworks te kiezen. Dit met reden om te kijken welke back-end taal en framework mij het beste bevalt. Hiervoor heb ik een framework gekozen dat gebaseerd is op JavaScript en een framework gebaseerd op Java (Hoewel de naam anders doet vermoeden, zijn JavaScript en Java niet dezelfde taal). In semester 2 heb ik gewerkt met een C# back-end dus heb ik deze taal en bijbehorende frameworks buiten mijn keuze gelaten.



---
<h2 id="data-behoud">Data Behoud</h2>
<h1>INVULLING VOLGT</H1>

---
<h2 id="kwaliteits-garantie">Kwaliteits Garantie</h2>
<h1>INVULLING VOLGT</H1>

---

<h2 id="github">Software Release Managament & het gebruik van Github</h2>

Om ervoor te zorgen dat er geen werk verloren gaat, zal Github gebruikt worden om alle projecten op te slaan, bugs te melden, automatisch te laten testen en bij geslaagde tests het project te Dockerizen en plaatsen op Docker hub. Software Release Management moet het saaie en repetitieve gedeelte van software development weghalen/verminderen. Zo kan het installeren van omgevingen en testen geautomatiseerd worden. Dit scheelt een hoop tijd; tijd die beter gestoken kan worden in het schrijven van code.

Tijdens dit proces worden de stappen 1 tot en met 7 doorlopen. Zie onderstaande afbeelding. 

<p align="center">
  <img width="350" id="srm" src="https://user-images.githubusercontent.com/73841047/143584767-f578966d-f21a-4a57-91fb-782bc29292c7.jpg">
</p>

---

### Software Branches

Om overzicht te houden welke code naar github gepusht worden, zal er gebruik worden gemaakt van zogenaamde *branches*. In semester 2 mocht alles op de *main* branch geplaatst worden, echter levert dit snel problemen op als je met meerdere developers moet samenwerken of wanneer een deel van de code toch niet werkt zoals gehoopt. Als namelijk alleen de main branch gebruikt wordt, dan kun je niet eenvoudig een paar commits terug gaan; je verliest alle code tot de commit waarnaar je terug wilt gaan. Verschillende branches kunnen dit voorkomen. Zie onderstaande afbeelding om te zien hoe de branch set-up eruit ziet in dit project.

![Wildzone-Software Branches drawio](https://user-images.githubusercontent.com/73841047/143588680-91d9ee14-e0ad-4790-bcad-021cdfcdaf89.png)

#### Main branch

Op de main branch staat de basis van het project. Zodra er een merge request gemaakt wordt op de main branch, dan zullen alle tests worden doorlopen en als deze tests vervolgens allemaal slagen dan zal het project omgezet worden naar een image en geüpload worden naar [deze Docker Hub repositories](https://hub.docker.com/u/jjuless). 

#### Development branch

Vanuit de main branch wordt de *development* branch aangemaakt. Op deze branch worden de nieuwste features en afgemaakte [userstories](https://dev.azure.com/461249/S3%20IP%20Jules%20Houben) geplaatst. Op de development branch zullen wel tests uitgevoerd worden, maar geen images gemaakt worden of andere publicaties.

#### Userstory branch

Vanuit de development branch wordt de *userstory* branch aangemaakt. De branch krijgt de naam van de userstory die gemaakt gaat worden. Zo is eenvoudig terug te zoeken in het [Azure board](https://dev.azure.com/461249/S3%20IP%20Jules%20Houben) om welke userstory het gaat en hoe ver het zit met de development hiervan.  Op de userstory branch zullen geen tests uitgevoerd worden en geen images gemaakt worden.

#### Bugfix / Release branch

Vanuit de main branch zal de *release* branch aangemaakt worden. Op deze branch worden geen nieuwe functies toegevoegd, maar kunnen wel bugfixes worden aangemaakt. Mocht het nu blijken dat er fouten in de release zaten, dan kunnen deze fouten op deze branch hersteld worden. Mochten het hele grote bugs zijn, groot genoeg voor een eigen userstory, dan zullen deze opgelost worden via de **development -> userstory** branch. Op bugfix / release zullen alleen testen uitgevoerd worden.

---

### CI/CD pipelines

Het doel van CI/CD pipelines is om tijdrovend werk te automatiseren door de computer. Dit zorgt ervoor dat er geen manuren verspild worden aan werk wat prima door een computer gedaan kan worden. Verder maakt een mens fouten, een computer gebeurt dat vrijwel nooit. Ook moeten CI/CD pipelines ervoor zorgen dat code vaker gepubliceerd wordt voor end-users. Vroeger werd er eens in de 5 maanden een update uitgebracht waar alle bugs werden verholpen en nieuwe features toegevoegd. Tegenwoordig is het de standaard om zo vaak mogelijk, het liefts meerdere malen per dag, zo'n update uit te voeren. Zo worden bugs sneller verholpen en kunnen nieuwe features vrijwel direct getest worden, om zo de kwaliteit van de software naar een hoger niveau te brengen.

Een vrij groot deel van de software release management kan geautomatiseerd worden. Als we kijken naar de software cycle, dan zien we dat de [stappen 3 tot en met 6](#srm) geautomatiseerd kunnen worden. Stappen die kostbare tijd in beslag nemen, tijd die beter gestoken kan worden in het ontwikkelen van nog meer en nog betere software.
Momenteel kunnen dus de volgende delen geautomatiseerd worden:
- Software Build
- Review
- Test
- Deployment

#### **CI** (**C**ontinuous **I**ntegration)

Zorgt ervoor dat de kwaliteit van de code aan vastgestelde eisen moet voldoen, anders wordt de code afgekeurd. Deze eisen kunnen zeer verschillend zijn. Een eis kan bijvoorbeeld zijn dat de code een end-2-end test moet doorlopen, voordat de code bij de rest van het project gevoegd kan worden. Een andere eis kan zijn dat de code in dezelfde stijl geschreven moet worden, zo moeten bijvoorbeeld variabelen aan bepaalde eisen voldoen of mogen comments in de code alleen tekst bevatten en geen uitgezette code bevatten. Zodra de nieuwe code gepusht wordt naar de development of main branch, dan zal de code dus eerst succesvol door deze eisen/tests moeten lopen voordat deze geaccepteerd worden.

#### **CD** (**C**ontinuous **D**elivery)

Zorgt ervoor dat de developer geen moeite meer hoef te doen voor het publiceren van de software; dit wordt automatisch gedaan door de CD pipeline. Als alle tests succesvol zijn doorlopen dan zal de software automatisch op klaarstaan om geplaatst te worden op een server. Hierdoor worden de stappen [3 tot en met 6](#srm) geautomatiseerd en hoeft de developer niets meer handmatig te publiceren. 

Vaak worden de termen Continuous Delivery en Continious Deployment door elkaar gehaald, echter hebben ze niet exact dezelfde termen. Bij Continuous Delivery moet een developer of systeem beheerder nog handmatig de code deployen in de productie omgeving. Bij Continious Deployment wordt de laatste stap van deze pipeline ook nog geautomatiseerd; er is geen developer of systeem beheerder meer nodig om de code op de server te krijgen. Zie de afbeelding hier beneden voor een visuele uitleg.

<p align="center">
  <img src="https://user-images.githubusercontent.com/73841047/143922528-a25fbc75-3c02-4afc-8d81-6619d516aa53.png">
</p>


#### Het verschil tussen CI & CD

Onderstaande afbeelding geeft een goed en duidelijk beeld over een complete CI/CD pipeline eruit ziet. Het belangrijkste verschil is dta CI ervoor zorgt dat de code in de repository terecht kan komen nadat het alle testen succesvol heeft doorlopen. 

CD neemt vervolgens deze code uit de repository, kan hier verschillende testen op doen en de software vervolgens productie klaar te maken. In het geval van Continuous Deployment, dan wordt de code ook nog eens direct geplaatst in de productie-omgeving.

<br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/73841047/143909565-0276f1c8-2641-4f51-9500-639e1be32c15.png">
</p>
<br>


#### CI/CD pipelines in dit project

<h1>INVULLING VOLGT</H1>

---

### Containerized Software

In dit project wordt Docker gebruikt. Docker zorgt ervoor dat het draaien van code op een server heel gemakkelijk gemaakt wordt. Vroeger moest je eerst alle software en besturingssystemen installeren op je eigen computer, server of virtuele server. Dit zorgt voor veel nadelen want:

- Je moet iedere keer de omgeving opnieuw instellen, voor zowel het testen als de live omgeving. Laat staan wanneer je applicatie zo populair is dat de server het niet aan kan en er dus meerdere servers geïnstalleerd moeten worden om de vraag aan te kunnen. Voor iedere server moet het installatie process exact opnieuw worden doorlopen.
- Als je veel moet installeren en instellen dan wordt de kans op fouten groter. Als de server namelijk niet precies is ingesteld zoals gehoopt, dan kan het zijn dat de applicatie niet (goed) draait. 

Met containerized software kun je een zogenaamde *image* maken van je applicatie. Je slaat als het ware het bouwplan op van de applicatie. Zo'n bouwplan kun je eenvoudig onbeperkt hergebruiken. Van dit bouwplan worden de instructies uitgevoerd, om zo de applicatie op te bouwen. Je kunt dit bouwplan extra instructies meegeven zodat je zeker weet dat de applicatie later draait op de gewenste manier.

<p align="center">
  <img src="https://user-images.githubusercontent.com/73841047/144228763-267c84fa-9769-4004-b7a1-efac9280d52a.png">
</p>

Het voordeel van de image/het bouwplan is dat je maar één keer hoeft te bepalen waaruit de image bestaat en welke omgevingsvariabelen deze nodig heeft. Je kunt dus heel eenvoudig de image vaker uitvoeren. Zodra je de image laat builden dan wordt er een container aangemaakt. In deze container draait de applicatie. Een container heeft geen besturingssysteem; het maakt gebruik van de kernel van het hostsysteem. Je hoeft dus niet voor elke container een OS te installeren. Dit scheelt een hele hoop installeer werk, kans op fouten en opslag.

Aangezien de container gebruik maakt van de kernel van het OS van het hostsysteem, maakt het niet uit op welk OS de container draait. Dit maakt de compatibiliteit een stuk groter.

Omdat elke applicatie in zijn eigen container draait, leent het containerizen van software zich goed voor microservices. Deze microservices moeten tenslotte allemaal los van elkaar kunnen draaien, daarom kun je elke service eenvoudig in een eigen container stoppen. Wanneer je je software systeem wilt uitbreiden dan voeg je eenvoudig een microservice toe in een nieuwe container. Deze service staat los van alle andere containers, dus mocht er iets mis zijn met de gemaakte code in de container, dan heeft dit niet direct invloed op het presteren van de andere microservices/containers.

Tot slot kun je alle containers heel eenvoudig en snel opstarten met docker-compose. Dit zorgt ervoor dat alle containers aangezet worden en met de juiste omgevingsvariabelen opgestart worden. 

---

### Configuration by Code

(Bijna) Iedere software moet van tevoren ingesteld worden met voorwaarden om te voldoen aan de eisen. Stel ik wil verbinding maken met een database, dan moet ik aangeven waar deze database gehost wordt, wat de naam is van de database, wat het wachtwoord is etc. Als dit allemaal hardcoded is en er komt een verandering, dan moet ik gaan zoeken waar ik deze gegevens allemaal heb ingevuld. Als oplossing voor dit probleem zijn environment variables bedacht. Deze environment variables worden opgeslagen in een bestand genaamd .ENV. Dit bestand wordt meestal niet volledig meegestuurd naar een repository, hier kunnen namelijk wachtwoorden inzitten. Deze wachtwoorden zouden dan te lezen zijn voor iedereen met toegang tot de repository.

Vaak wordt er dan een sample.env meegestuurd. Hierin staan wel welke variabelen er gebruikt worden in de applicatie, maar niet welke waardes deze variabelen hebben.

Het voordeel van de configuratie opslaan in de repository is dat je kunt bijhouden wanneer er wat is aangepast door wie. Verder heb je alle code dan op één plek staan. 

