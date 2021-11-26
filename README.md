# Wildzone documentation
<p align="center">
  <img src="https://user-images.githubusercontent.com/73841047/142646426-e43dc258-e831-43ce-ae1f-9ab1f70a7ea7.png">
</p>

**Alle documentatie omtrent het Fontys Eindhoven Software Engineering semester 3 Wildzone webshop project van Jules Houben.**

## Inleiding
In dit project wil ik een fictieve webshop gaan bouwen voor verschillende kleding artikelen. Het doel is om hiermee aan te tonen dat ik kan laten zien dat ik begrijp hoe een JavaScript front-end werkt, dat ik dit kan combineren met een OO gebaseerde back-end taal en dat de software gedistribueerd is zodat het een grote hoeveelheid aan gebruikers tevreden kan stellen. Om dit proces voor de gebruiker zo snel en efficiënt mogelijk te maken zal er gebruik worden gemaakt van asynchrone communicatie om te voorkomen dat een gebruiker lang moet wachten. In combinatie van een intuïtieve UX moet dit ervoor zorgen dat de gebruikservaring van de website zo optimaal mogelijk is. 
De data van de gebruiker zal opgeslagen worden in een relationele database. Aangezien dit gevoelige informatie is zal er gekeken moeten worden naar verschillende beveiligingsopties om de data van de gebruiker te kunnen beschermen. 

## Leeswijzer
Deze organisatie is opgedeeld in verschillende repositories. In elke repository zit slechts één service. In de ReadMe van iedere repository kun je zien hoe de microservice opgestart kan worden, hoe deze werkt en hoe deze getest wordt. Alle inhoudelijke documentatie betreffende keuzes van programmeertalen en frameworks kun je lezen in de huidige repository. In deze ReadMe kun je de algemene lijnen van het project zien. Klik onder het volgende kopje op de verschillende onderwerpen als je meer te weten wilt komen over dat onderwerp.

## Content van de documentatie repository
- [Front-end](https://github.com/S3-IP-Jules-Houben-Fontys/Wildzone-documentation/blob/main/front-end.md)
- Back-end

## Inhoudsopgave ReadMe Wildzone-documentation
1. [Gedistribueerde Software](#gedistribueerde-software)
2. [Conceptueel Model](#conceptueel-model)
3. [Microservices Overzicht](#microservice-overzicht)

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


<h2 id="microservice-overzicht"> 3. Project Overzicht </h2>

Om duidelijkheid te creeren in dit project, wordt er gebruik gemaakt van de zogenaamde *C4-method*. De C4 methode is ontworpen om de software architectuur overzichtelijk in kaart te brengen voor zowel opdrachtgever als voor software engineers. De C4 methode bestaat uit 4 verschillende diagrammen, waarbij ieder diagram net iets dieper inzoomt op de software die ontwikkeld moet worden. De volgende onderdelen komen voor in de C4 methode:

- Context (level 1, geschikt voor iedereen; er is geen tot weinig technische kennis nodig om het diagram volledig te kunnen begrijpen)
- Containers (level 2, geschikt voor mensen met eenvoudige technische kennis; er worden technische ondedelen benoemd, maar moet begrijpelijk zijn voor mensen met eenvoudige technische kennis)
- Components (level 3, geschikt voor mensen met technische kennis; geeft een algemeen duidelijk beeld uit welke onderdelen/microservices het software systeem bestaat. Niet geschikt voor opdrachtgevers)
- Components (level 4, geschikt voor software egineers; geeft de werking van één enkele microservice weer tot in de details. Alleen geschikt voor software egineers)

---

### Context

Zie onderstaande diagram voor de context van dit software systeem.

![Wildzone-C1 System Context diagram drawio (2)](https://user-images.githubusercontent.com/73841047/143442490-e2176763-8095-4cc2-8e0b-d8d9d8ba5ce7.png)

---

### Containers

Als we iets verder inzoomen op het software systeem dat ontwikkeld moet worden, dan komen we uit bij de onderstaande diagram:

![Wildzone-C2 Container diagram drawio (1)](https://user-images.githubusercontent.com/73841047/143568140-c76727dd-a143-4314-a849-59b308bba449.png)

---

### Components
