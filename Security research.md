
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