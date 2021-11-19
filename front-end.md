# Front-end Development

## JavaScript Frameworks

### Waarom een JavaScript framework?

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

### React

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

### Vue

**Pro&#39;s:**

- Maakt gebruik van een virtuele DOM. Dit zorgt ervoor dat veranderingen van data razendsnel geladen kunnen worden op de pagina, zonder deze te moeten verversen.
- Maakt het makkelijk om animaties toe te voegen
- Is simpel om te gebruiken en zou beginner-friendly zijn

**Con&#39;s:**

- Vue is nog erg nieuw, waardoor de community nog niet heel groot is, hierdoor mis je experts, plugins en support.
- Mobiele support is niet eenvoudig [(Grankin, 2020)](https://ddi-dev.com/blog/programming/the-good-and-the-bad-of-vue-js-framework-programming/)

**Twijfel:**

- Doordat Vue nog zo nieuw is en er zo weinig support is, is het niet aan te raden om hele grote projecten te maken. Voor kleine projecten zou dit niet veel moeten uitmaken

### Angular

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

### Conclusie

Ik heb besloten om te gaan met React, dit omdat deze gemakkelijk te debuggen zou zijn en dat het grootste deel van de professionele developers React verkiezen boven alle andere frameworks. Dit laat React op mij overkomen dat dit framework wordt vertrouwd en gebruikt door een grote groep developers. Doordat de community zo groot is en nog steeds aan het groeien is, is de con &quot;Developers zeggen dat de documentatie van React beter kan zijn. &quot; minder belangrijk aangezien de community dan altijd om hulp gevraagd kan worden. Verder is het belangrijk dat er goede mobiele support is, aangezien inmiddels 54,8% van het internetverkeer via mobiele apparaten plaats vindt [(Statista, 2021)](https://www.statista.com/statistics/277125/share-of-website-traffic-coming-from-mobile-devices/)

## UX voor software engineers: de basis

Voor een leek is UI en UX precies hetzelfde, want &quot;het heeft allebei met de voorkant van een applicatie te maken&quot;. Tot zekere hoogte klopt dit. Echter is er een groot wezenlijk verschil tussen de twee.

UI staat voor &#39; **U** ser **I** nterface&#39;, de interface is dus vooral wat de gebruiker ziet. Denk hierbij aan kleuren, afbeeldingen, lettertypen en iconen.


UX staat voor &#39; **U** ser e **X** perience&#39;, dit is wat gebruiker ervaart tijdens het gebruik van de app. De gebruiker &#39;ziet&#39; dit veelal niet. Denk hierbij aan het uitzoeken waar knoppen moeten komen, of het aantal kliks optimaliseren zodat de gebruiker sneller en eenvoudiger bij de gewenste pagina kan uitkomen

UI en UX zijn goed te vergelijken met een ijsberg; De top, de UI is zichtbaar voor de gebruiker, de rest van de ijsberg is voor de gebruiker niet te zien maar is wel degelijk aanwezig (Ditmeyer).

Als de ervaring met de applicatie niet goed wordt bevonden door de gebruiker, dan is het onwaarschijnlijk dat gebruiker de applicatie vaker zal gebruiken. Stel een deurklink zou je iedere keer een schok geven wanneer je de deur wilt openen. Het doel, de deur openen, kan nog altijd bereikt worden. Echter zal de gebruiker deze stap niet vaker willen herhalen, aangezien deze een negatieve ervaring heeft gehad met het gebruik van deze deurklink. UI kan slechts het uiterlijk van de deurklink veranderen. Of deze nu donkerpaars is of muntgroen dat maakt niet uit, de ervaring verandert namelijk niet. UX kan ervoor zorgen dat deze ervaring wel beter wordt, door bijvoorbeeld de deurklink niet meer onder stroom te zetten. In dit geval kan de gebruiker eenvoudig zijn doel bereiken, zonder hier negatieve ervaringen aan over te houden.

![Figuur 2 UI en UX zijn goed te vergelijken met een ijsberg (Ditmeyer)](https://user-images.githubusercontent.com/73841047/142628269-6023754b-e5d4-4266-9905-7b2ed9fda2fa.png)

### Hoe ga ik UX aantonen in mijn project?

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
