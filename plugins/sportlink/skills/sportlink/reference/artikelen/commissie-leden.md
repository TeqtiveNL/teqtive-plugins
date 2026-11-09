# commissie-leden

## Wat het teruggeeft

Geeft de leden van een commissie met hun rol en contactgegevens.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `commissiecode` | integer | **ja** |  | [commissies](commissies.md) (`commissiecode`) | Commissie code |
| `toonlidfoto` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Toon foto van lid |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `lid` | string | Naam |
| `rolid` | string | RolId |
| `rol` | string | Rol |
| `email` | email | E-mail |
| `email2` | email | Secundaire e-mail |
| `telefoon` | string | Telefoonnummer |
| `telefoon2` | string | Secundaire telefoonnummer |
| `mobiel` | string | Mobiel |
| `startdatum` | string | Startdatum |
| `startdatetime` | datetime | Startdatum |
| `einddatum` | string | Einddatum |
| `einddatetime` | datetime | Einddatum |
| `informatie` | string | Informatie |
| `adres` | string | Adres |
| `plaats` | string | Plaats |
| `foto` | binary | Foto |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/commissie-leden?client_id=$SPORTLINK_CLIENT_ID&commissiecode=<commissiecode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "lid": "Voornaam Achternaam",
    "rolid": "21",
    "rol": "algemeen commisielid",
    "email": null,
    "email2": null,
    "telefoon": null,
    "telefoon2": null,
    "mobiel": null,
    "startdatum": "01-01-2020",
    "startdatetime": "2020-01-01T00:00:00+0100",
    "einddatum": "",
    "einddatetime": null,
    "informatie": "",
    "adres": null,
    "plaats": null,
    "foto": null
  },
  {
    "lid": "Voornaam Achternaam",
    "rolid": "21",
    "rol": null,
    "email": null,
    "email2": null,
    "telefoon": null,
    "telefoon2": null,
    "mobiel": null,
    "startdatum": null,
    "startdatetime": null,
    "einddatum": null,
    "einddatetime": null,
    "informatie": null,
    "adres": null,
    "plaats": null,
    "foto": null
  }
]
```

## Valkuilen en bondsregels

- Bevat persoonsgegevens. `toonlidfoto` standaard `NEE`.

## Gerelateerd

- **Invoer uit:** [commissies](commissies.md), [keuzelijst-boolean](keuzelijst-boolean.md)
- **Levert invoer voor:** geen
