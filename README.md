# Wildzone-documentation
Alle documentatie omtrent het Fontys Eindhoven Software Engineering semester 3 Wildzone webshop project van Jules Houben.

## Conceptueel model
![Wildzone-Conceptueel model](https://user-images.githubusercontent.com/73841047/142633369-2ab19943-3055-4b29-b087-eefd82fe2910.jpg)

Er zijn 4 belangrijke onderdelen in deze webshop, namelijk:
- Supplier (leverancier)
- Product
- Inventory (inventaris)
- Category (categorie)

Met dit conceptueel model kunnen we vervolgens een inschatting gaan maken hoe vaak een entiteit gebruikt zal gaan worden. Als een entiteit vaak gebruikt wordt, dan kan het verstandig zijn om deze entiteit zijn eigen service te geven. Stel de product entiteit wordt 100x gebruikt in 1 seconde en de leveranciers entiteit maar 1x per seconde. Het kan gebeuren dat de verzoeken 1-voor-1 worden afgewerkt. Wanneer er tijdens het opvragen van een leverancier iedere keer gewacht moet worden op de voorgaande 100 producten, dan kost dit veel tijd. Door veel vragende entiteiten hun eigen service te geven, dan kun je deze wachttijd onder andere verminderen. Zodra deze entiteiten hun eigen service hebben dan kan het bijvoorbeeld zo zijn dat de 100 producten op elkaar moeten wachten, maar dat ondertussen via de leveranciers service de leverancier alvast opgehaald kan worden.
Verder zorgt het maken van microservices ervoor dat de entiteiten niet van elkaar afhankelijk zijn. Stel er gaat iets fout bij de service van de leverancier, dan werkt de service voor producten wel nog gewoon, waardoor de gebruikers de applicatie kunnen blijven gebruiken. Welliswaar zonder informatie over leveranciers, maar de applicatie ligt niet compleet uit de lucht.

## Service overzicht
