# wedstrijd-thuisteam

## Wat het teruggeeft

Geeft spelers en staf van het thuisteam bij een wedstrijd.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdcode` | integer | **ja** |  | [programma](programma.md) (`wedstrijdcode`) | Wedstrijdcode |
| `toonlidfoto` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Toon foto van lid |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `relatiecode` | string | Lidcode |
| `naam` | string | Naam |
| `rol` | string | Rol |
| `einddatum` | string | Einddatum |
| `functie` | string | Functie |
| `email` | email | E-mail |
| `email2` | email | Secundaire e-mail |
| `telefoon` | string | Telefoonnummer |
| `telefoon2` | string | Secundaire telefoonnummer |
| `mobiel` | string | Mobiel |
| `foto` | binary | Foto |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/wedstrijd-thuisteam?client_id=$SPORTLINK_CLIENT_ID&wedstrijdcode=<wedstrijdcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "relatiecode": null,
    "naam": "Voornaam Achternaam",
    "rol": "Spelend teamlid",
    "einddatum": null,
    "functie": "",
    "email": null,
    "email2": null,
    "telefoon": null,
    "telefoon2": null,
    "mobiel": null,
    "foto": null
  },
  {
    "relatiecode": null,
    "naam": "Voornaam Achternaam",
    "rol": "Spelend teamlid",
    "einddatum": null,
    "functie": "",
    "email": null,
    "email2": null,
    "telefoon": null,
    "telefoon2": null,
    "mobiel": null,
    "foto": null
  },
  {
    "relatiecode": "ABC1234",
    "naam": "Voornaam Achternaam",
    "rol": "Spelend teamlid",
    "einddatum": null,
    "functie": "",
    "email": null,
    "email2": null,
    "telefoon": null,
    "telefoon2": null,
    "mobiel": null,
    "foto": null
  }
]
```

## Valkuilen en bondsregels

- Bevat persoonsgegevens. `toonlidfoto` standaard `NEE`.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [programma](programma.md)
- **Levert invoer voor:** geen
