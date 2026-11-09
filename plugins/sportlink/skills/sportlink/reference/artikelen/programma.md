# programma

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Valkuilen en bondsregels](#valkuilen-en-bondsregels)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft de geplande wedstrijden van de club, filterbaar op team, thuis/uit, sport en periode.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `lokaleteamcode` | integer | nee |  | [teams](teams.md) (`lokaleteamcode`) | Teamcode lokaal |
| `teamcode` | integer | nee |  | [teams](teams.md) (`teamcode`) | Teamcode |
| `sorteervolgorde` | string | nee | `datum` | [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md) (`sorteervolgorde`) | Sorteervolgorde |
| `gebruiklokaleteamgegevens` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Gebruik lokale teamnamen |
| `aantalregels` | integer | nee | `100` |  | Maximum aantal regels |
| `aantaldagen` | integer | nee | `30` |  | Maximum aantal dagen vooruit |
| `weekoffset` | integer | nee | `0` |  | Weeknummer vanaf nu |
| `eigenwedstrijden` | string | nee | `JA` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Eigenwedstrijden |
| `thuis` | string | nee | `JA` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Thuis |
| `uit` | string | nee | `JA` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Uit |
| `spelsoort` | string | nee | `ALLES` | [keuzelijst-spelsoorten](keuzelijst-spelsoorten.md) (`waarde`) | Spelsoort |
| `competitiesoort` | string | nee | `ALLES` | [keuzelijst-competitiesoorten](keuzelijst-competitiesoorten.md) (`waarde`) | Competitiesoort |
| `dagsoort` | string | nee | `ALLES` | [keuzelijst-dagsoorten](keuzelijst-dagsoorten.md) (`waarde`) | Dagsoort |
| `leeftijdscategorie` | string | nee | `ALLES` | [keuzelijst-leeftijdscategorieen](keuzelijst-leeftijdscategorieen.md) (`waarde`) | Leeftijdscategorie |
| `wedstrijdtype` | string | nee |  | [keuzelijst-wedstrijdtypes](keuzelijst-wedstrijdtypes.md) (`waarde`) | Wedstrijdtype |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen** (unieke sleutel: `wedstrijdcode`).

| Veld | Type | Label |
|---|---|---|
| `wedstrijddatum` | datetime | Datum |
| `wedstrijdcode` | integer | Wedstrijdcode |
| `wedstrijdnummer` | integer | Wedstrijdnummer |
| `teamnaam` | string | Team |
| `thuisteamclubrelatiecode` | string | Thuisteam-clubrelatiecode |
| `uitteamclubrelatiecode` | string | Uitteam-clubrelatiecode |
| `thuisteamid` | integer | Thuisteamid |
| `thuisteam` | string | Thuisteam |
| `thuisteamlogo` | string | Thuisteam logo |
| `uitteamid` | integer | Uitteamid |
| `uitteam` | string | Uitteam |
| `uitteamlogo` | string | Uitteam logo |
| `teamvolgorde` | integer | Teamvolgorde |
| `competitiesoort` | string | Competitiesoort |
| `competitie` | string | Competitie |
| `klasse` | string | Klasse |
| `poule` | string | Poule |
| `klassepoule` | string | Klassepoule |
| `kaledatum` | string | Kaledatum |
| `datum` | string | Datum |
| `vertrektijd` | clocktime | Vertrektijd |
| `verzameltijd` | clocktime | Verzameltijd |
| `aanvangstijd` | clocktime | Aanvangstijd |
| `wedstrijd` | string | Wedstrijd |
| `status` | string | Status |
| `scheidsrechters` | string | Scheidsrechters |
| `scheidsrechter` | string | Scheidsrechter |
| `accommodatie` | string | Accommodatie |
| `veld` | string | Veld |
| `locatie` | string | Locatie |
| `plaats` | string | Plaats |
| `rijders` | string | Rijders |
| `kleedkamerthuisteam` | string | Kleedkamerthuisteam |
| `kleedkameruitteam` | string | Kleedkameruitteam |
| `kleedkamerscheidsrechter` | string | Kleedkamerscheidsrechter |
| `meer` | link | Meer |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/programma?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "wedstrijddatum": "2026-11-10T21:00:00+0100",
    "wedstrijdcode": 1772348,
    "wedstrijdnummer": 12345,
    "teamnaam": "Voorbeeldclub 1",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "thuisteamid": 4245,
    "thuisteam": "Voorbeeldclub 1",
    "thuisteamlogo": "https://example.org/afbeelding.png",
    "uitteamid": 4230,
    "uitteam": "Voorbeeldclub 1",
    "uitteamlogo": "https://example.org/afbeelding.png",
    "teamvolgorde": 2001,
    "competitiesoort": "regulier",
    "competitie": "Dames Midweek",
    "klasse": "Poule",
    "poule": "NW C DMW-02 Z (35+)",
    "klassepoule": "Poule NW C DMW-02 Z (35+)",
    "kaledatum": "2026-11-10 00:00:00.00",
    "datum": "10 nov.",
    "vertrektijd": "",
    "verzameltijd": "20:00",
    "aanvangstijd": "21:00",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "status": "Te spelen",
    "scheidsrechters": "Voornaam Achternaam",
    "scheidsrechter": "Voornaam Achternaam",
    "accommodatie": "Sportpark Voorbeeld",
    "veld": "zaal 1",
    "locatie": "Sportpark Voorbeeld",
    "plaats": "Voorbeeldstad",
    "rijders": null,
    "kleedkamerthuisteam": "",
    "kleedkameruitteam": "",
    "kleedkamerscheidsrechter": "",
    "meer": "wedstrijd-informatie?wedstrijdcode=1772348"
  },
  {
    "wedstrijddatum": "2026-11-14T16:45:00+0100",
    "wedstrijdcode": 1772630,
    "wedstrijdnummer": 12345,
    "teamnaam": "Voorbeeldclub 1",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "thuisteamid": 21760,
    "thuisteam": "Voorbeeldclub 1",
    "thuisteamlogo": "https://example.org/afbeelding.png",
    "uitteamid": 21772,
    "uitteam": "Voorbeeldclub 1",
    "uitteamlogo": "https://example.org/afbeelding.png",
    "teamvolgorde": 2001,
    "competitiesoort": "regulier",
    "competitie": "F-Jeugd",
    "klasse": "Poule",
    "poule": "NW NH GF-01 Z (competitie)",
    "klassepoule": "Poule NW NH GF-01 Z (competitie)",
    "kaledatum": "2026-11-14 00:00:00.00",
    "datum": "14 nov.",
    "vertrektijd": "15:50",
    "verzameltijd": "",
    "aanvangstijd": "16:45",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "status": "Te spelen",
    "scheidsrechters": "",
    "scheidsrechter": "",
    "accommodatie": "Sportpark Voorbeeld",
    "veld": "veld 1 A",
    "locatie": "Sportpark Voorbeeld",
    "plaats": "Voorbeeldstad",
    "rijders": "",
    "kleedkamerthuisteam": "",
    "kleedkameruitteam": "",
    "kleedkamerscheidsrechter": "",
    "meer": "wedstrijd-informatie?wedstrijdcode=1772630"
  },
  {
    "wedstrijddatum": "2026-11-14T17:55:00+0100",
    "wedstrijdcode": 1772671,
    "wedstrijdnummer": 12345,
    "teamnaam": "Voorbeeldclub 1",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "thuisteamid": 15928,
    "thuisteam": "Voorbeeldclub 1",
    "thuisteamlogo": "https://example.org/afbeelding.png",
    "uitteamid": 2783,
    "uitteam": "Voorbeeldclub 1",
    "uitteamlogo": "https://example.org/afbeelding.png",
    "teamvolgorde": 701,
    "competitiesoort": "regulier",
    "competitie": "Dames C-Jeugd",
    "klasse": "Poule",
    "poule": "NW B DC-01 Z",
    "klassepoule": "Poule NW B DC-01 Z",
    "kaledatum": "2026-11-14 00:00:00.00",
    "datum": "14 nov.",
    "vertrektijd": "",
    "verzameltijd": "",
    "aanvangstijd": "17:55",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "status": "Te spelen",
    "scheidsrechters": "Voornaam Achternaam",
    "scheidsrechter": "Voornaam Achternaam",
    "accommodatie": "Sportpark Voorbeeld",
    "veld": "zaal 1",
    "locatie": "Sportpark Voorbeeld",
    "plaats": "Voorbeeldstad",
    "rijders": "",
    "kleedkamerthuisteam": "",
    "kleedkameruitteam": "",
    "kleedkamerscheidsrechter": "",
    "meer": "wedstrijd-informatie?wedstrijdcode=1772671"
  }
]
```

## Valkuilen en bondsregels

- `aantaldagen` standaard 30, maximaal 42 voor de hele club of 250 met een `teamcode`. `aantalregels` standaard 100, maximaal 500.
- `teamcode` en `lokaleteamcode` gaan samen mee.
- `dagsoort` werkt alleen samen met `spelsoort`.
- `wedstrijdcode` is de sleutel voor de `wedstrijd-*`-artikelen; `wedstrijdnummer` is het publieke nummer.
- In de zomer kan het programma leeg zijn omdat de indeling nog loopt.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [keuzelijst-competitiesoorten](keuzelijst-competitiesoorten.md), [keuzelijst-dagsoorten](keuzelijst-dagsoorten.md), [keuzelijst-leeftijdscategorieen](keuzelijst-leeftijdscategorieen.md), [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md), [keuzelijst-spelsoorten](keuzelijst-spelsoorten.md), [keuzelijst-wedstrijdtypes](keuzelijst-wedstrijdtypes.md), [teams](teams.md)
- **Levert invoer voor:** [wedstrijd-accommodatie](wedstrijd-accommodatie.md), [wedstrijd-deelnemers](wedstrijd-deelnemers.md), [wedstrijd-historische-resultaten](wedstrijd-historische-resultaten.md), [wedstrijd-informatie](wedstrijd-informatie.md), [wedstrijd-kleedkamers](wedstrijd-kleedkamers.md), [wedstrijd-officials](wedstrijd-officials.md), [wedstrijd-statistieken](wedstrijd-statistieken.md), [wedstrijd-thuisteam](wedstrijd-thuisteam.md), [wedstrijd-uitteam](wedstrijd-uitteam.md)
