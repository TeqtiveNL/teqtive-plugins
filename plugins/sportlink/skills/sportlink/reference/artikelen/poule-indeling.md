# poule-indeling

## Wat het teruggeeft

Geeft de teams in een poule met hun speelnummer, speeldag en starttijd.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `poulecode` | integer | **ja** |  | [poulelijst](poulelijst.md) (`poulecode`) | Poule code |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `teamnaam` | string | Teamnaam |
| `clubrelatiecode` | string | Clubrelatiecode |
| `speelnummer` | int | Speelnummer |
| `speeldag` | string | Speeldag |
| `starttijd` | clocktime | Starttijd |
| `eigenteam` | boolean | Eigenteam |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/poule-indeling?client_id=$SPORTLINK_CLIENT_ID&poulecode=<poulecode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "teamnaam": "Voorbeeldclub 1",
    "clubrelatiecode": "XYZ9999",
    "speelnummer": "1",
    "speeldag": "zondag",
    "starttijd": null,
    "eigenteam": "false"
  },
  {
    "teamnaam": "Voorbeeldclub 1",
    "clubrelatiecode": "XYZ9999",
    "speelnummer": "2",
    "speeldag": "zondag",
    "starttijd": null,
    "eigenteam": "false"
  },
  {
    "teamnaam": "Voorbeeldclub 1",
    "clubrelatiecode": "XYZ9999",
    "speelnummer": "3",
    "speeldag": "zondag",
    "starttijd": null,
    "eigenteam": "true"
  }
]
```

## Valkuilen en bondsregels

- Gebruik `poulecode`, niet `publiekepoulecode`.
- `eigenteam` komt terug als tekst (`"true"` of `"false"`), niet als boolean, ook al noemt de catalogus het type `boolean`. Vergelijk dus met `=== "true"`.

## Gerelateerd

- **Invoer uit:** [poulelijst](poulelijst.md)
- **Levert invoer voor:** geen
