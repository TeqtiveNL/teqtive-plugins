# teampoulelijst

## Wat het teruggeeft

Geeft alle poules waarin één team speelt.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `teamcode` | integer | **ja** |  | [teams](teams.md) (`teamcode`) | Teamcode |
| `lokaleteamcode` | integer | **ja** |  | [teams](teams.md) (`lokaleteamcode`) | Teamcode lokaal |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `poulecode` | integer | Poulecode |
| `teamcode` | integer | Teamcode |
| `teamnaam` | string | Teamnaam |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/teampoulelijst?client_id=$SPORTLINK_CLIENT_ID&teamcode=<teamcode>&lokaleteamcode=<lokaleteamcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "poulecode": 42337,
    "teamcode": 1390,
    "teamnaam": "Voorbeeldclub 1"
  }
]
```

## Valkuilen en bondsregels

- De poules veranderen bij een herindeling, zoals tussen de najaars- en voorjaarsreeks.

## Gerelateerd

- **Invoer uit:** [teams](teams.md)
- **Levert invoer voor:** geen
