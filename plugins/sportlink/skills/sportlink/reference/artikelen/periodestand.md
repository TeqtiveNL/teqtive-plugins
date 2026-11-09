# periodestand

## Wat het teruggeeft

Geeft de stand van een periode binnen een poule (deelcompetitie met een eigen kampioen).

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `poulecode` | integer | **ja** |  | [poulelijst](poulelijst.md) (`poulecode`) | Poulecode |
| `periodenummer` | integer | nee | `-1` |  | Periodenummercode |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen** (`eigenteam` markeert het eigen team).

| Veld | Type | Label |
|---|---|---|
| `positie` | integer | Positie |
| `teamcode` | integer | Teamcode |
| `poulecode` | integer | Poulecode |
| `clubcode` | string | Clubcode |
| `clubnaam` | string | Clubnaam |
| `teamnaam` | string | Teamnaam |
| `aantalwedstrijden` | integer | Aantal wedstrijden |
| `totaalpunten` | integer | Totaal punten |
| `doelpuntenvoor` | integer | Doelpunten voor |
| `tegendoelpunten` | integer | Doelpunten tegen |
| `gewonnen` | integer | Gewonnen |
| `gelijkspel` | integer | Gelijkspel |
| `verloren` | integer | Verloren |
| `doelsaldo` | integer | Doelsaldo |
| `verliespunten` | integer | Punten in mindering |
| `eigenteam` | boolean | eigenteam |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/periodestand?client_id=$SPORTLINK_CLIENT_ID&poulecode=<poulecode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "positie": 0,
    "teamcode": 0,
    "poulecode": 0,
    "clubcode": "<Clubcode>",
    "clubnaam": "<Clubnaam>",
    "teamnaam": "<Teamnaam>",
    "aantalwedstrijden": 0,
    "totaalpunten": 0,
    "doelpuntenvoor": 0,
    "tegendoelpunten": 0,
    "gewonnen": 0,
    "gelijkspel": 0,
    "verloren": 0,
    "doelsaldo": 0,
    "verliespunten": 0,
    "eigenteam": false
  }
]
```

## Valkuilen en bondsregels

- **KNVB:** voor competities tot en met Onder-9 geeft dit artikel geen standen of uitslagen. Een lege response bij een JO9-team is dus correct. Zie [bonden.md](../bonden.md#knvb).
- `periodenummer=-1` (standaard) geeft de huidige periode. Geldige nummers komen uit [keuzelijst-periodenummers](keuzelijst-periodenummers.md).

## Gerelateerd

- **Invoer uit:** [poulelijst](poulelijst.md)
- **Levert invoer voor:** geen
