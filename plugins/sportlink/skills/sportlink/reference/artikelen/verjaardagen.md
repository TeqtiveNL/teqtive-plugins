# verjaardagen

## Wat het teruggeeft

Geeft de leden die binnenkort jarig zijn.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `aantaldagen` | integer | nee | `21` |  | Aantal dagen |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `verjaardag` | string | Verjaardag |
| `volledigenaam` | string | Naam |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/verjaardagen?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "verjaardag": "10 Nov",
    "volledigenaam": "Voornaam Achternaam"
  },
  {
    "verjaardag": "12 Nov",
    "volledigenaam": "Voornaam Achternaam"
  },
  {
    "verjaardag": "14 Nov",
    "volledigenaam": "Voornaam Achternaam"
  }
]
```

## Valkuilen en bondsregels

- `aantaldagen` maximaal 21.
- Bevat persoonsgegevens; leden met privacyniveau "Afgeschermd" verschijnen niet.

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
