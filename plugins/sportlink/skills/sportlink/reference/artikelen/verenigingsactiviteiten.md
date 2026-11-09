# verenigingsactiviteiten

## Wat het teruggeeft

Geeft de agenda van de club: toernooien, vergaderingen, clubevenementen en jubilea.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `aantaldagen` | integer | nee | `7` |  | Maximum aantal dagen vooruit |
| `kalendersoort` | string | nee |  |  | Filter op kalender soort |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `kalendernaam` | string | Kalendernaam |
| `kalendersoort` | string | Kalendersoort |
| `activiteit` | string | Activiteit |
| `datumvan` | datetime | Datum van |
| `datumtm` | datetime | Datum t/m |
| `heledag` | boolean | Hele dag |
| `beheerders` | string | Beheerders |
| `opmerkingen` | string | Opmerkingen |
| `plaats` | string | Locatie |
| `url` | string | URL |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/verenigingsactiviteiten?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "kalendernaam": "<Kalendernaam>",
    "kalendersoort": "<Kalendersoort>",
    "activiteit": "<Activiteit>",
    "datumvan": "<Datum van>",
    "datumtm": "<Datum t/m>",
    "heledag": false,
    "beheerders": "<Beheerders>",
    "opmerkingen": "<Opmerkingen>",
    "plaats": "<Locatie>",
    "url": "<URL>"
  }
]
```

## Valkuilen en bondsregels

- `aantaldagen` standaard 7. Filter op `kalendersoort` met waarden uit [keuzelijst-verenigingsactiviteit-kalendersoorten](keuzelijst-verenigingsactiviteit-kalendersoorten.md).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
