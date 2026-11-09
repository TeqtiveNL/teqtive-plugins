# poulelijst

## Wat het teruggeeft

Geeft alle poules van de club met poulecode, publieke poulecode en team.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `poulecode` | integer | Poulecode |
| `publiekepoulecode` | string | PubliekePoulecode |
| `teamcode` | integer | Teamcode |
| `teamnaam` | string | Teamnaam |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/poulelijst?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "poulecode": 42337,
    "publiekepoulecode": "P0000000000",
    "teamcode": 1390,
    "teamnaam": "Voorbeeldclub 1"
  },
  {
    "poulecode": 42298,
    "publiekepoulecode": "P0000000000",
    "teamcode": 2775,
    "teamnaam": "Voorbeeldclub 1"
  },
  {
    "poulecode": 43360,
    "publiekepoulecode": "P0000000000",
    "teamcode": 2776,
    "teamnaam": "Voorbeeldclub 1"
  }
]
```

## Valkuilen en bondsregels

- `poulecode` is de interne sleutel voor andere artikelen; `publiekepoulecode` is alleen voor weergave.

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** [keuzelijst-periodenummers](keuzelijst-periodenummers.md), [periodestand](periodestand.md), [poule-indeling](poule-indeling.md), [poule-programma](poule-programma.md), [poulestand](poulestand.md), [pouleuitslagen](pouleuitslagen.md)
