# Wildzone documentation
<p align="center">
  <img src="https://user-images.githubusercontent.com/73841047/142646426-e43dc258-e831-43ce-ae1f-9ab1f70a7ea7.png">
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

<h2 id="front-end-development">Front-end Development</h2>
<h1>INVULLING VOLGT</H1>

---
<h2 id="back-end-development">Back-end Development</h2>
<h1>INVULLING VOLGT</H1>

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

