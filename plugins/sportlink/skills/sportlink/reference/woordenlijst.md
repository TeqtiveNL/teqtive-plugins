# Woordenlijst

## Begrippen

**Artikel**
Een opvraagbare dataset van Sportlink Club.Dataservice, bijvoorbeeld `programma` of `poulestand`. Technisch is een artikel een REST-endpoint. In de skill en de spec gebruiken we altijd "artikel".
_Niet:_ endpoint, feed (behalve als uitleg)

**Catalogus**
De openbare lijst van alle artikelen met hun invoer en uitvoer, op te vragen zonder ClientID.

**ClientID**
De sleutel die een club krijgt als ze Club.Dataservice afneemt. Hij geeft toegang tot de artikelen van die ene club.
_Niet:_ club-key, API-key, token

**Bond**
De sportbond waaronder een club valt, zoals de KNVB of de KNKV. De bond bepaalt welke competitiedata er in Sportlink beschikbaar is.

**Ledenlogin-artikel**
Een artikel dat naast de ClientID ook een login van een individueel lid vraagt. Deze artikelen vallen buiten de scope.

**Ontwikkelaar**
De doelgebruiker van de skill: iemand die een clubsite of app bouwt op Sportlink-data.

**Teamcode / poulecode / wedstrijdcode**
De sleutels waarmee artikelen naar elkaar verwijzen: een team leidt naar zijn poules, en een poule leidt naar stand, programma en uitslagen. Een wedstrijdcode is iets anders dan het wedstrijdnummer dat op papier staat.

**Bondsregel**
Een regel van een bond die bepaalt wat een artikel teruggeeft. Voorbeeld: de KNVB publiceert geen standen voor competities tot en met Onder-9.

**Catalogusmodus / live-modus**
De twee manieren waarop de skill werkt. In catalogusmodus put de skill alleen uit zijn eigen kennis over de artikelen; daarvoor is geen ClientID nodig. In live-modus haalt Claude op verzoek van de ontwikkelaar echte data op met diens ClientID.
_Niet:_ "stand" (dat woord betekent in dit domein altijd een competitiestand)

**Keuzelijst**
Een artikel met de geldige waarden voor een invoerveld, zoals leeftijdscategorieën of spelsoorten. De waarden verschillen per bond.
