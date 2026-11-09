# team-sponsors

## Wat het teruggeeft

Geeft de sponsors van een team met naam, website en logo.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `teamcode` | integer | **ja** |  | [teams](teams.md) (`teamcode`) | Teamcode |
| `lokaleteamcode` | integer | **ja** |  | [teams](teams.md) (`lokaleteamcode`) | Teamcode lokaal |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `naam` | string | Naam |
| `website` | string | Website |
| `opmerkingen` | string | Opmerkingen |
| `begindatum` | string | Begindatum |
| `begindatetime` | datetime | Begindatum |
| `logo` | binary | Logo |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/team-sponsors?client_id=$SPORTLINK_CLIENT_ID&teamcode=<teamcode>&lokaleteamcode=<lokaleteamcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "naam": "<Naam>",
    "website": "<Website>",
    "opmerkingen": "<Opmerkingen>",
    "begindatum": "<Begindatum>",
    "begindatetime": "<Begindatum>",
    "logo": "<Logo>"
  }
]
```

## Gerelateerd

- **Invoer uit:** [teams](teams.md)
- **Levert invoer voor:** geen
