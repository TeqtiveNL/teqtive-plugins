# wedstrijd-deelnemers

## Wat het teruggeeft

Geeft de deelnemers van een wedstrijd zoals vastgelegd in het digitale wedstrijdformulier.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdcode` | integer | **ja** |  | [programma](programma.md) (`wedstrijdcode`) | Wedstrijdcode |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `relatiecode` | string | Relatiecode |
| `volledigenaam` | string | Naam |
| `rol` | string | Rol |
| `einddatum` | date | Einddatum |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/wedstrijd-deelnemers?client_id=$SPORTLINK_CLIENT_ID&wedstrijdcode=<wedstrijdcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "relatiecode": "ABC1234",
    "volledigenaam": "Voornaam Achternaam",
    "rol": "Spelend teamlid",
    "einddatum": null
  },
  {
    "relatiecode": null,
    "volledigenaam": "Voornaam Achternaam",
    "rol": "Spelend teamlid",
    "einddatum": null
  },
  {
    "relatiecode": "ABC1234",
    "volledigenaam": "Voornaam Achternaam",
    "rol": "Spelend teamlid",
    "einddatum": null
  }
]
```

## Valkuilen en bondsregels

- Bevat persoonsgegevens.

## Gerelateerd

- **Invoer uit:** [programma](programma.md)
- **Levert invoer voor:** geen
