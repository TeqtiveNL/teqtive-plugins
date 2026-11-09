# wedstrijd-historische-resultaten

## Wat het teruggeeft

Geeft eerdere onderlinge duels van de twee teams, per seizoen.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdcode` | integer | **ja** |  | [programma](programma.md) (`wedstrijdcode`) | Wedstrijdcode |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `seizoen` | string | Seizoen |
| `wedstrijd` | string | Wedstrijd |
| `datum` | string | Datum |
| `wedstrijddatum` | string | Wedstrijddatum |
| `wedstrijddatetime` | datetime | Wedstrijddatum |
| `uitslag` | string | Uitslag |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/wedstrijd-historische-resultaten?client_id=$SPORTLINK_CLIENT_ID&wedstrijdcode=<wedstrijdcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "seizoen": "2017 - 2018 Competitie Seizoen",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "datum": "15 nov. 2017",
    "wedstrijddatum": "2017-11-15 00:00:00.00",
    "wedstrijddatetime": "2017-11-15T20:00:00+0100",
    "uitslag": "15 - 15"
  },
  {
    "seizoen": "2017 - 2018 Competitie Seizoen",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "datum": "5 feb. 2018",
    "wedstrijddatum": "2018-02-05 00:00:00.00",
    "wedstrijddatetime": "2018-02-05T19:00:00+0100",
    "uitslag": "15 - 19"
  },
  {
    "seizoen": "2018 - 2019 Competitie Seizoen",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "datum": "29 okt. 2018",
    "wedstrijddatum": "2018-10-29 00:00:00.00",
    "wedstrijddatetime": "2018-10-29T19:00:00+0100",
    "uitslag": "12 - 19"
  }
]
```

## Valkuilen en bondsregels

- **KNVB:** voor competities tot en met Onder-9 geeft dit artikel geen standen of uitslagen. Een lege response bij een JO9-team is dus correct. Zie [bonden.md](../bonden.md#knvb).

## Gerelateerd

- **Invoer uit:** [programma](programma.md)
- **Levert invoer voor:** geen
