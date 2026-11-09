# uitslagen

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Valkuilen en bondsregels](#valkuilen-en-bondsregels)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft de gespeelde wedstrijden van de club met de uitslag.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdtype` | string | nee |  | [keuzelijst-wedstrijdtypes](keuzelijst-wedstrijdtypes.md) (`waarde`) | Wedstrijdtype |
| `teamcode` | integer | nee |  | [teams](teams.md) (`teamcode`) | Teamcode |
| `lokaleteamcode` | integer | nee |  | [teams](teams.md) (`lokaleteamcode`) | Teamcode lokaal |
| `aantalregels` | integer | nee | `100` |  | Aantal regels |
| `weekoffset` | integer | nee | `-1` |  | Weeknummer vanaf nu |
| `aantaldagen` | integer | nee | `7` |  | Aantal dagen |
| `gebruiklokaleteamgegevens` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Gebruik lokale teamnamen |
| `sorteervolgorde` | string | nee | `datum` | [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md) (`sorteervolgorde`) | Sorteervolgorde |
| `eigenwedstrijden` | string | nee | `ja` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Eigenwedstrijden |
| `thuis` | string | nee | `JA` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Thuis |
| `uit` | string | nee | `JA` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Uit |
| `spelsoort` | string | nee | `ALLES` | [keuzelijst-spelsoorten](keuzelijst-spelsoorten.md) (`waarde`) | Spelsoort |
| `leeftijdscategorie` | string | nee | `ALLES` | [keuzelijst-leeftijdscategorieen](keuzelijst-leeftijdscategorieen.md) (`waarde`) | Leeftijdscategorie |
| `competitiesoort` | string | nee | `ALLES` | [keuzelijst-competitiesoorten](keuzelijst-competitiesoorten.md) (`waarde`) | Competitiesoort |
| `dagsoort` | string | nee | `ALLES` | [keuzelijst-dagsoorten](keuzelijst-dagsoorten.md) (`waarde`) | Dagsoort |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `wedstrijddatum` | datetime | Datum |
| `wedstrijdcode` | integer | Wedstrijdcode |
| `wedstrijdnummer` | integer | Wedstrijdnummer |
| `datum` | string | Datum |
| `wedstrijd` | string | Wedstrijd |
| `datumopgemaakt` | string | Datum opgemaakt |
| `accommodatie` |  | Accommodatie |
| `aanvangstijd` | clocktime | Aanvangstijd |
| `thuisteam` | string | Thuisteam |
| `thuisteamid` | string | Thuisteamid |
| `thuisteamlogo` | string | Thuisteam logo |
| `thuisteamclubrelatiecode` | string | Thuisteam-clubrelatiecode |
| `uitteamclubrelatiecode` | string | Uitteam-clubrelatiecode |
| `uitteam` | string | Uitteam |
| `uitteamid` | string | Uitteamid |
| `uitteamlogo` | string | Uitteam logo |
| `uitslag` | string | Uitslag |
| `uitslag-regulier` | string | Uitslag regulier |
| `uitslag-nv` | string | Uitslag na verlenging |
| `uitslag-s` | string | Uitslag strafschoppen |
| `competitienaam` | string | Competitienaam |
| `competitiesoort` | string | Competitiesoort |
| `eigenteam` | boolean | Eigenteam |
| `sportomschrijving` | string | Sportomschrijving |
| `verenigingswedstrijd` | string | Verenigingswedstrijd |
| `status` | string | status |
| `meer` | link | Meer |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/uitslagen?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "wedstrijddatum": "2026-11-04T19:00:00+0100",
    "wedstrijdcode": 1814556,
    "wedstrijdnummer": 12345,
    "datum": "2026-11-04 00:00:00.00",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "datumopgemaakt": "4 nov.",
    "accommodatie": "Sportpark Voorbeeld",
    "aanvangstijd": "19:00",
    "thuisteam": "Voorbeeldclub 1",
    "thuisteamid": "4247",
    "thuisteamlogo": "https://example.org/afbeelding.png",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "uitteam": "Voorbeeldclub 1",
    "uitteamid": "4212",
    "uitteamlogo": "https://example.org/afbeelding.png",
    "uitslag": "5 - 15",
    "uitslag-regulier": "5 - 15",
    "uitslag-nv": null,
    "uitslag-s": null,
    "competitienaam": "Dames Midweek",
    "competitiesoort": "regulier",
    "eigenteam": "true",
    "sportomschrijving": "Zaal",
    "verenigingswedstrijd": "Voorbeeldclub",
    "status": "Uitgespeeld",
    "meer": "wedstrijd-informatie?wedstrijdcode=1814556"
  },
  {
    "wedstrijddatum": "2026-11-04T21:00:00+0100",
    "wedstrijdcode": 1771724,
    "wedstrijdnummer": 12345,
    "datum": "2026-11-04 00:00:00.00",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "datumopgemaakt": "4 nov.",
    "accommodatie": "Sportpark Voorbeeld",
    "aanvangstijd": "21:00",
    "thuisteam": "Voorbeeldclub 1",
    "thuisteamid": "7493",
    "thuisteamlogo": "https://example.org/afbeelding.png",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "uitteam": "Voorbeeldclub 1",
    "uitteamid": "4245",
    "uitteamlogo": "https://example.org/afbeelding.png",
    "uitslag": "18 - 14",
    "uitslag-regulier": "18 - 14",
    "uitslag-nv": null,
    "uitslag-s": null,
    "competitienaam": "Dames Midweek",
    "competitiesoort": "regulier",
    "eigenteam": "true",
    "sportomschrijving": "Zaal",
    "verenigingswedstrijd": "Voorbeeldclub",
    "status": "Uitgespeeld",
    "meer": "wedstrijd-informatie?wedstrijdcode=1771724"
  },
  {
    "wedstrijddatum": "2026-11-07T13:55:00+0100",
    "wedstrijdcode": 1772448,
    "wedstrijdnummer": 12345,
    "datum": "2026-11-07 00:00:00.00",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "datumopgemaakt": "7 nov.",
    "accommodatie": "Sportpark Voorbeeld",
    "aanvangstijd": "13:55",
    "thuisteam": "Voorbeeldclub 1",
    "thuisteamid": "13519",
    "thuisteamlogo": "https://example.org/afbeelding.png",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "uitteam": "Voorbeeldclub 1",
    "uitteamid": "2780",
    "uitteamlogo": "https://example.org/afbeelding.png",
    "uitslag": "12 - 16",
    "uitslag-regulier": "12 - 16",
    "uitslag-nv": null,
    "uitslag-s": null,
    "competitienaam": "D-Jeugd",
    "competitiesoort": "regulier",
    "eigenteam": "true",
    "sportomschrijving": "Zaal",
    "verenigingswedstrijd": "Voorbeeldclub",
    "status": "Uitgespeeld",
    "meer": "wedstrijd-informatie?wedstrijdcode=1772448"
  }
]
```

## Valkuilen en bondsregels

- **KNVB:** voor competities tot en met Onder-9 geeft dit artikel geen standen of uitslagen. Een lege response bij een JO9-team is dus correct. Zie [bonden.md](../bonden.md#knvb).
- `aantaldagen` standaard 7, maximaal 365. `weekoffset` van -52 tot en met 0, standaard -1 (vorige week).
- Uitslagvarianten: regulier, na verlenging (`-nv`) en na strafschoppen (`-s`).
- `eigenteam` komt terug als tekst (`"true"` of `"false"`), niet als boolean, ook al noemt de catalogus het type `boolean`. Vergelijk dus met `=== "true"`.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [keuzelijst-competitiesoorten](keuzelijst-competitiesoorten.md), [keuzelijst-dagsoorten](keuzelijst-dagsoorten.md), [keuzelijst-leeftijdscategorieen](keuzelijst-leeftijdscategorieen.md), [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md), [keuzelijst-spelsoorten](keuzelijst-spelsoorten.md), [keuzelijst-wedstrijdtypes](keuzelijst-wedstrijdtypes.md), [teams](teams.md)
- **Levert invoer voor:** geen
