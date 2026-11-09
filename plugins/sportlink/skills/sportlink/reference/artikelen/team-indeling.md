# team-indeling

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Valkuilen en bondsregels](#valkuilen-en-bondsregels)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft de spelers en staf van een team met hun rol.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `teamcode` | integer | **ja** |  | [teams](teams.md) (`teamcode`) | Teamcode |
| `lokaleteamcode` | integer | **ja** |  | [teams](teams.md) (`lokaleteamcode`) | Teamcode lokaal |
| `teampersoonrol` | string | nee | `ALLES` | [keuzelijst-teampersoonrollen](keuzelijst-teampersoonrollen.md) (`waarde`) | Filter rol |
| `toonlidfoto` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Toon foto van lid |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `relatiecode` | string | Lidcode |
| `naam` | string | Naam |
| `voornaam` | string | Voornaam |
| `achternaam` | string | Achternaam |
| `tussenvoegsel` | string | Tussenvoegsel |
| `geslacht` | string | Geslacht |
| `rol` | string | Rol |
| `functie` | string | Functie |
| `einddatum` | string | Einddatum |
| `email` | email | E-mail |
| `email2` | email | Secundaire e-mail |
| `telefoon` | string | Telefoonnummer |
| `telefoon2` | string | Secundaire telefoonnummer |
| `mobiel` | string | Mobiel |
| `foto` | binary | Foto |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/team-indeling?client_id=$SPORTLINK_CLIENT_ID&teamcode=<teamcode>&lokaleteamcode=<lokaleteamcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "relatiecode": null,
    "naam": "Voornaam Achternaam",
    "voornaam": "Voornaam Achternaam",
    "achternaam": "Voornaam Achternaam",
    "tussenvoegsel": "van",
    "geslacht": null,
    "rol": "Spelend teamlid",
    "functie": "",
    "einddatum": null,
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
    "voornaam": "Voornaam Achternaam",
    "achternaam": "Voornaam Achternaam",
    "tussenvoegsel": "van",
    "geslacht": null,
    "rol": "Technische staf",
    "functie": "Assistent coach",
    "einddatum": null,
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
    "voornaam": "Voornaam Achternaam",
    "achternaam": "Voornaam Achternaam",
    "tussenvoegsel": "van",
    "geslacht": null,
    "rol": "Spelend teamlid",
    "functie": "",
    "einddatum": null,
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

- **KNVB:** geen e-mailadressen of telefoonnummers.
- `toonlidfoto` standaard `NEE`.
- Bevat persoonsgegevens; wat zichtbaar is, hangt af van het privacyniveau van elk lid.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [keuzelijst-teampersoonrollen](keuzelijst-teampersoonrollen.md), [teams](teams.md)
- **Levert invoer voor:** geen
