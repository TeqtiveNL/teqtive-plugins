# commissies

## Wat het teruggeeft

Geeft alle commissies van de club.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen** (unieke sleutel: `commissiecode`).

| Veld | Type | Label |
|---|---|---|
| `commissiecode` | string | Commissiecode |
| `commissienaam` | string | Commissienaam |
| `omschrijving` | string | Omschrijving |
| `foto` | binary | Foto |
| `opmerkingen` | string | Opmerkingen |
| `telefoon` | string | Telefoon |
| `mobiel` | string | Mobiel |
| `email` | string | E-mail |
| `details` | link | Details |
| `leden` | link | Leden |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/commissies?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "commissiecode": "422",
    "commissienaam": "Activiteiten",
    "omschrijving": "Activiteiten ",
    "foto": null,
    "opmerkingen": null,
    "telefoon": null,
    "mobiel": null,
    "email": null,
    "details": "commissie-details?commissiecode=422",
    "leden": "commissie-leden?commissiecode=422"
  },
  {
    "commissiecode": "423",
    "commissienaam": "Feest",
    "omschrijving": "Feest",
    "foto": null,
    "opmerkingen": null,
    "telefoon": null,
    "mobiel": null,
    "email": null,
    "details": "commissie-details?commissiecode=423",
    "leden": "commissie-leden?commissiecode=423"
  },
  {
    "commissiecode": "380",
    "commissienaam": "JTC",
    "omschrijving": "Jeugd Technische Commissie",
    "foto": null,
    "opmerkingen": null,
    "telefoon": null,
    "mobiel": null,
    "email": null,
    "details": "commissie-details?commissiecode=380",
    "leden": "commissie-leden?commissiecode=380"
  }
]
```

## Valkuilen en bondsregels

- De `commissiecode` gebruik je in [commissie-details](commissie-details.md) en [commissie-leden](commissie-leden.md).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** [commissie-details](commissie-details.md), [commissie-leden](commissie-leden.md)
