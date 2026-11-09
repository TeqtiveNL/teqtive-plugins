# team-trainingenlijst

## Wat het teruggeeft

Geeft de trainingen van één team.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `teamcode` | integer | **ja** |  | [teams](teams.md) (`teamcode`) | Teamcode |
| `lokaleteamcode` | integer | **ja** |  | [teams](teams.md) (`lokaleteamcode`) | Teamcode lokaal |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `trainingid` | integer | TrainingId |
| `naam` | string | Naam |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/team-trainingenlijst?client_id=$SPORTLINK_CLIENT_ID&teamcode=<teamcode>&lokaleteamcode=<lokaleteamcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "trainingid": 0,
    "naam": "<Naam>"
  }
]
```

## Valkuilen en bondsregels

- De `trainingid` gebruik je in [trainingdetails](trainingdetails.md).

## Gerelateerd

- **Invoer uit:** [teams](teams.md)
- **Levert invoer voor:** geen
