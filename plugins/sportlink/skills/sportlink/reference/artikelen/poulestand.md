# poulestand

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Valkuilen en bondsregels](#valkuilen-en-bondsregels)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft de ranglijst van een poule: positie, gespeeld, gewonnen, gelijk, verloren, doelpunten, verliespunten en punten.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `poulecode` | integer | **ja** |  | [poulelijst](poulelijst.md) (`poulecode`) | Poule code |
| `gebruiklokaleteamgegevens` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Gebruik lokale teamnamen |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen** (`eigenteam` markeert het eigen team).

| Veld | Type | Label |
|---|---|---|
| `positie` | integer | Positie |
| `teamnaam` | string | Team |
| `clubrelatiecode` | string | Clubrelatiecode |
| `clublogo` | string | Club logo |
| `gespeeldewedstrijden` | integer | Gespeelde wedstrijden |
| `gewonnen` | integer | Gewonnen |
| `gelijk` | integer | Gelijk |
| `verloren` | integer | Verloren |
| `doelpuntenvoor` | integer | Doelpunten voor |
| `doelpuntentegen` | integer | Doelpunten tegen |
| `doelsaldo` | integer | Doelsaldo |
| `verliespunten` | integer | Punten in mindering |
| `punten` | integer | Punten |
| `eigenteam` | boolean | Eigenteam |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/poulestand?client_id=$SPORTLINK_CLIENT_ID&poulecode=<poulecode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "positie": 1,
    "teamnaam": "Voorbeeldclub 1",
    "clubrelatiecode": "XYZ9999",
    "clublogo": "https://example.org/afbeelding.png",
    "gespeeldewedstrijden": 4,
    "gewonnen": 4,
    "gelijk": 0,
    "verloren": 0,
    "doelpuntenvoor": 126,
    "doelpuntentegen": 74,
    "doelsaldo": 52,
    "verliespunten": 0,
    "punten": 8,
    "eigenteam": "false"
  },
  {
    "positie": 2,
    "teamnaam": "Voorbeeldclub 1",
    "clubrelatiecode": "XYZ9999",
    "clublogo": "https://example.org/afbeelding.png",
    "gespeeldewedstrijden": 4,
    "gewonnen": 3,
    "gelijk": 0,
    "verloren": 1,
    "doelpuntenvoor": 73,
    "doelpuntentegen": 60,
    "doelsaldo": 13,
    "verliespunten": 0,
    "punten": 6,
    "eigenteam": "true"
  },
  {
    "positie": 3,
    "teamnaam": "Voorbeeldclub 1",
    "clubrelatiecode": "XYZ9999",
    "clublogo": "https://example.org/afbeelding.png",
    "gespeeldewedstrijden": 4,
    "gewonnen": 2,
    "gelijk": 0,
    "verloren": 2,
    "doelpuntenvoor": 85,
    "doelpuntentegen": 62,
    "doelsaldo": 23,
    "verliespunten": 0,
    "punten": 4,
    "eigenteam": "false"
  }
]
```

## Valkuilen en bondsregels

- **KNVB:** voor competities tot en met Onder-9 geeft dit artikel geen standen of uitslagen. Een lege response bij een JO9-team is dus correct. Zie [bonden.md](../bonden.md#knvb).
- Neem de stand altijd over; bereken punten nooit zelf, want de telling verschilt per bond.
- De kolommen zijn op voetbal geschoeid (`doelpuntenvoor`, `gelijk`). Bij andere sporten is hun betekenis niet gedocumenteerd.
- `eigenteam` markeert het team van de club.
- `eigenteam` komt terug als tekst (`"true"` of `"false"`), niet als boolean, ook al noemt de catalogus het type `boolean`. Vergelijk dus met `=== "true"`.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [poulelijst](poulelijst.md)
- **Levert invoer voor:** geen
