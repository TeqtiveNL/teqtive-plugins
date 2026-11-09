# trainingdetails

## Wat het teruggeeft

Geeft de data, locatie en kleedkamer van een training.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `trainingid` | integer | **ja** |  | [trainingenlijst](trainingenlijst.md) (`trainingid`) | Training code |
| `aantaldagen` | integer | nee | `30` |  | Maximum aantal dagen vooruit |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `begindatum` | datetime | Begindatum |
| `einddatum` | datetime | Einddatum |
| `locatie` | string | Locatie |
| `kleedkamer` | string | Kleedkamer |
| `opmerkingen` | string | Opmerkingen |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/trainingdetails?client_id=$SPORTLINK_CLIENT_ID&trainingid=<trainingid>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "begindatum": "<Begindatum>",
    "einddatum": "<Einddatum>",
    "locatie": "<Locatie>",
    "kleedkamer": "<Kleedkamer>",
    "opmerkingen": "<Opmerkingen>"
  }
]
```

## Valkuilen en bondsregels

- `aantaldagen` maximaal 30.

## Gerelateerd

- **Invoer uit:** [trainingenlijst](trainingenlijst.md)
- **Levert invoer voor:** geen
