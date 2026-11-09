---
name: sportlink
description: Kennis van de Sportlink Club.Dataservice API (Sportlink API, club data) voor ontwikkelaars die een clubsite of app bouwen. Verbinden met client_id, alle artikelen (endpoints) met parameters, uitvoervelden en voorbeeldresponses, foutcodes, de navigatie van teams via poules naar wedstrijden, bondsregels, en codevoorbeelden in JS/TS en PHP/WordPress. Gebruik bij vragen over programma, uitslagen, standen (fixtures, results, standings), teams, trainingen, clubgegevens of keuzelijsten uit Sportlink.
---

# Sportlink Club.Dataservice

> Onofficieel: deze skill is niet gelieerd aan, gesponsord door of goedgekeurd door Sportlink.

Club.Dataservice is de REST-API waarmee een sportclub haar eigen gegevens uit Sportlink Club opvraagt: programma, uitslagen, standen, teams, trainingen, bestuur en meer. Elk endpoint heet in Sportlink een **artikel**: `GET https://data.sportlink.com/<artikel>?client_id=…`. Dit document gebruikt die term ook.

## Hoe je deze skill gebruikt

Standaard antwoord je uit de kennis in deze skill (**catalogusmodus**). Daarvoor is geen ClientID nodig. Vraagt de ontwikkelaar om echte data van zijn club (**live-modus**), geef dan het commando uit [verbinden.md](reference/verbinden.md#live-patroon). De ontwikkelaar draait dat zelf in zijn eigen terminal. Jouw shell heeft de ClientID van de club niet.

**Bij elke vraag:**
1. Kies het artikel uit de artikeltabel hieronder en lees het artikelbestand.
2. Heeft het artikel een code nodig (teamcode, poulecode, wedstrijdcode)? Volg dan [navigatie.md](reference/navigatie.md) om te zien welk artikel die code levert.
3. Kijk in [bonden.md](reference/bonden.md) of er een bondsregel geldt. Daarmee verklaar je ook lege of ontbrekende data.
4. Geef code met de patronen uit [code-js.md](reference/code-js.md) of [code-php.md](reference/code-php.md), of taalonafhankelijk als HTTP-call met een voorbeeldresponse. In code zijn functie-, variabele- en typenamen Engels (`fetchUpcomingMatches`); alleen API-velden blijven Nederlands.

## ClientID: half-geheim

- In commando's staat altijd `$SPORTLINK_CLIENT_ID`. De ontwikkelaar vult de waarde zelf in via `read -s`.
- In code wordt de ClientID gelezen uit een omgevingsvariabele of uit de serverconfig.
- Een response wordt **recursief** gemaskeerd voordat hij getoond wordt, want `info` stuurt de ClientID genest mee terug.
- Een ClientID die de ontwikkelaar toch in de chat plakt, gebruik je niet verder in je antwoord. Raad hem aan het patroon met `read -s` te gebruiken.

Persoonsgegevens laat je alleen zien zoals de API ze teruggeeft; het privacyniveau van elk lid in Sportlink bepaalt wat zichtbaar is. Bewaar ze nergens.

## Vaste reference-bestanden

| Bestand | Lees als |
|---|---|
| [verbinden.md](reference/verbinden.md) | je een call opbouwt, live-modus nodig hebt of uitlegt waar de ClientID te vinden is |
| [foutcodes.md](reference/foutcodes.md) | een response een `error` bevat, of leeg is terwijl dat niet verwacht werd |
| [navigatie.md](reference/navigatie.md) | een artikel een code nodig heeft die uit een ander artikel komt |
| [bonden.md](reference/bonden.md) | de sport of bond ertoe doet, voor bondsregels, standen of keuzelijsten |
| [woordenlijst.md](reference/woordenlijst.md) | een Sportlink-begrip uitleg nodig heeft |
| [code-js.md](reference/code-js.md) | je JavaScript- of TypeScript-code schrijft |
| [code-php.md](reference/code-php.md) | je PHP- of WordPress-code schrijft |

## Artikelen

Ontbreekt een artikel hier, of wijkt het af van wat de API doet? Dan is de openbare catalogus `https://data.sportlink.com/list` leidend. Die is zonder ClientID op te vragen.

| Artikel | Groep | Wat |
|---|---|---|
| [info](reference/artikelen/info.md) | meta | Geeft de ClientID en de bond van de club terug; gebruik het om te testen of een key werkt en om de sport te bepalen. |
| [afgelastingen](reference/artikelen/afgelastingen.md) | competitie | Geeft de afgelaste wedstrijden van de club in een tijdvenster. |
| [periodestand](reference/artikelen/periodestand.md) | competitie | Geeft de stand van een periode binnen een poule (deelcompetitie met een eigen kampioen). |
| [poule-indeling](reference/artikelen/poule-indeling.md) | competitie | Geeft de teams in een poule met hun speelnummer, speeldag en starttijd. |
| [poule-programma](reference/artikelen/poule-programma.md) | competitie | Geeft het programma van een hele poule, ook van wedstrijden zonder eigen team. |
| [poulelijst](reference/artikelen/poulelijst.md) | competitie | Geeft alle poules van de club met poulecode, publieke poulecode en team. |
| [poulestand](reference/artikelen/poulestand.md) | competitie | Geeft de ranglijst van een poule: positie, gespeeld, gewonnen, gelijk, verloren, doelpunten, verliespunten en punten. |
| [pouleuitslagen](reference/artikelen/pouleuitslagen.md) | competitie | Geeft de uitslagen van een hele poule. |
| [programma](reference/artikelen/programma.md) | competitie | Geeft de geplande wedstrijden van de club, filterbaar op team, thuis/uit, sport en periode. |
| [uitslagen](reference/artikelen/uitslagen.md) | competitie | Geeft de gespeelde wedstrijden van de club met de uitslag. |
| [wedstrijd-accommodatie](reference/artikelen/wedstrijd-accommodatie.md) | competitie | Geeft de accommodatie van een wedstrijd: naam, adres, plaats, telefoon en route. |
| [wedstrijd-historische-resultaten](reference/artikelen/wedstrijd-historische-resultaten.md) | competitie | Geeft eerdere onderlinge duels van de twee teams, per seizoen. |
| [wedstrijd-informatie](reference/artikelen/wedstrijd-informatie.md) | competitie | Geeft alle details van één wedstrijd: nummer, veld, tijden, rijders, officials en score. |
| [wedstrijd-kleedkamers](reference/artikelen/wedstrijd-kleedkamers.md) | competitie | Geeft de kleedkamers voor thuisteam, uitteam en scheidsrechter bij een wedstrijd. |
| [wedstrijd-officials](reference/artikelen/wedstrijd-officials.md) | competitie | Geeft de aangestelde officials van een wedstrijd. |
| [wedstrijd-statistieken](reference/artikelen/wedstrijd-statistieken.md) | competitie | Geeft statistieken van beide teams, zoals het percentage gewonnen wedstrijden thuis en uit. |
| [team-gegevens](reference/artikelen/team-gegevens.md) | teams | Geeft de gegevens van één team, zoals naam, competitie en looptijd. |
| [team-sponsors](reference/artikelen/team-sponsors.md) | teams | Geeft de sponsors van een team met naam, website en logo. |
| [team-trainingenlijst](reference/artikelen/team-trainingenlijst.md) | teams | Geeft de trainingen van één team. |
| [teampoulelijst](reference/artikelen/teampoulelijst.md) | teams | Geeft alle poules waarin één team speelt. |
| [teams](reference/artikelen/teams.md) | teams | Geeft alle teams van de club met teamcode, poulecode, competitie, klasse en indeling. |
| [trainingdetails](reference/artikelen/trainingdetails.md) | teams | Geeft de data, locatie en kleedkamer van een training. |
| [trainingenlijst](reference/artikelen/trainingenlijst.md) | teams | Geeft alle trainingen van de club met trainers. |
| [bestuur](reference/artikelen/bestuur.md) | vereniging | Geeft de bestuursleden van de club met hun functie en contactgegevens. |
| [clubgegevens](reference/artikelen/clubgegevens.md) | vereniging | Geeft de gegevens van de club: naam, code, adressen, contact en clubkleuren. |
| [clublogo](reference/artikelen/clublogo.md) | vereniging | Geeft het logo van de club. |
| [commissie-details](reference/artikelen/commissie-details.md) | vereniging | Geeft de gegevens van één commissie. |
| [commissies](reference/artikelen/commissies.md) | vereniging | Geeft alle commissies van de club. |
| [kleuren-clubdata](reference/artikelen/kleuren-clubdata.md) | vereniging | Geeft de websitekleuren die de club in Sportlink heeft ingesteld. |
| [kleuren-clubtv](reference/artikelen/kleuren-clubtv.md) | vereniging | Geeft de kleuren voor de club-tv-weergave. |
| [verenigingsactiviteiten](reference/artikelen/verenigingsactiviteiten.md) | vereniging | Geeft de agenda van de club: toernooien, vergaderingen, clubevenementen en jubilea. |
| [vrijwilligerstaken](reference/artikelen/vrijwilligerstaken.md) | vereniging | Geeft de vrijwilligerstaken van de club. |
| [commissie-leden](reference/artikelen/commissie-leden.md) | personen | Geeft de leden van een commissie met hun rol en contactgegevens. |
| [scheidsrechtersaanstellingen](reference/artikelen/scheidsrechtersaanstellingen.md) | personen | Geeft welke scheidsrechters bij welke wedstrijden zijn aangesteld, ook clubscheidsrechters. |
| [team-indeling](reference/artikelen/team-indeling.md) | personen | Geeft de spelers en staf van een team met hun rol. |
| [verjaardagen](reference/artikelen/verjaardagen.md) | personen | Geeft de leden die binnenkort jarig zijn. |
| [vrijwilligers](reference/artikelen/vrijwilligers.md) | personen | Geeft wie een vrijwilligerstaak doet en wanneer. |
| [wedstrijd-deelnemers](reference/artikelen/wedstrijd-deelnemers.md) | personen | Geeft de deelnemers van een wedstrijd zoals vastgelegd in het digitale wedstrijdformulier. |
| [wedstrijd-thuisteam](reference/artikelen/wedstrijd-thuisteam.md) | personen | Geeft spelers en staf van het thuisteam bij een wedstrijd. |
| [wedstrijd-uitteam](reference/artikelen/wedstrijd-uitteam.md) | personen | Geeft spelers en staf van het uitteam bij een wedstrijd. |
| [keuzelijst-boolean](reference/artikelen/keuzelijst-boolean.md) | keuzelijsten | Geeft de geldige ja/nee-waarden voor parameters zoals `gebruiklokaleteamgegevens`. |
| [keuzelijst-competitieperiode](reference/artikelen/keuzelijst-competitieperiode.md) | keuzelijsten | Geeft de competitieperiodes, zoals de najaars- en voorjaarsreeks. |
| [keuzelijst-competitiesoorten](reference/artikelen/keuzelijst-competitiesoorten.md) | keuzelijsten | Geeft de soorten competitie, zoals regulier of beker. |
| [keuzelijst-dagsoorten](reference/artikelen/keuzelijst-dagsoorten.md) | keuzelijsten | Geeft de speeldagen voor het filter `dagsoort`. |
| [keuzelijst-factuurstatussen](reference/artikelen/keuzelijst-factuurstatussen.md) | keuzelijsten | Geeft de statussen van facturen; alleen relevant voor de artikelen met ledenlogin, die buiten deze skill vallen. |
| [keuzelijst-geslacht](reference/artikelen/keuzelijst-geslacht.md) | keuzelijsten | Geeft de waarden voor het filter `geslacht`. |
| [keuzelijst-leeftijdscategorieen](reference/artikelen/keuzelijst-leeftijdscategorieen.md) | keuzelijsten | Geeft de leeftijdscategorieën van de bond, zoals JO11 bij de KNVB. |
| [keuzelijst-periodenummers](reference/artikelen/keuzelijst-periodenummers.md) | keuzelijsten | Geeft de periodes van een poule en welke de huidige is. |
| [keuzelijst-sorteervolgordes](reference/artikelen/keuzelijst-sorteervolgordes.md) | keuzelijsten | Geeft de mogelijke sorteervolgordes voor programma en uitslagen. |
| [keuzelijst-spelsoorten](reference/artikelen/keuzelijst-spelsoorten.md) | keuzelijsten | Geeft de spelsoorten, zoals veld en zaal. |
| [keuzelijst-teampersoonrollen](reference/artikelen/keuzelijst-teampersoonrollen.md) | keuzelijsten | Geeft de rollen in een team, zoals speler en trainer. |
| [keuzelijst-teamsoorten](reference/artikelen/keuzelijst-teamsoorten.md) | keuzelijsten | Geeft de teamsoorten, zoals bondsteam of lokaal team. |
| [keuzelijst-verenigingsactiviteit-kalendersoorten](reference/artikelen/keuzelijst-verenigingsactiviteit-kalendersoorten.md) | keuzelijsten | Geeft de soorten activiteiten in de clubagenda. |
| [keuzelijst-wedstrijdtypes](reference/artikelen/keuzelijst-wedstrijdtypes.md) | keuzelijsten | Geeft de wedstrijdtypes, zoals competitie, beker en oefen. |
