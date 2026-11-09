# teams

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Valkuilen en bondsregels](#valkuilen-en-bondsregels)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft alle teams van de club met teamcode, poulecode, competitie, klasse en indeling.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `competitieperiode` | string | nee |  | [keuzelijst-competitieperiode](keuzelijst-competitieperiode.md) (`waarde`) | Competitieperiode |
| `teamsoort` | string | nee | `ALLES` | [keuzelijst-teamsoorten](keuzelijst-teamsoorten.md) (`waarde`) | Teamsoort |
| `geslacht` | string | nee | `ALLES` | [keuzelijst-geslacht](keuzelijst-geslacht.md) (`waarde`) | Geslacht |
| `spelsoort` | string | nee | `ALLES` | [keuzelijst-spelsoorten](keuzelijst-spelsoorten.md) (`waarde`) | Spelsoort |
| `competitiesoort` | string | nee | `ALLES` | [keuzelijst-competitiesoorten](keuzelijst-competitiesoorten.md) (`waarde`) | Competitiesoort |
| `leeftijdscategorie` | string | nee | `ALLES` | [keuzelijst-leeftijdscategorieen](keuzelijst-leeftijdscategorieen.md) (`waarde`) | Leeftijdscategorie |
| `gebruiklokaleteamgegevens` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Gebruik lokale teamnamen |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen** (unieke sleutel: `poulecode`).

| Veld | Type | Label |
|---|---|---|
| `teamcode` | integer | Teamcode |
| `lokaleteamcode` | integer | Lokaleteamcode |
| `poulecode` | integer | Poulecode |
| `teamnaam` | string | Teamnaam |
| `competitienaam` | string | Competitienaam |
| `klasse` | string | Klasse |
| `poule` | string | Poule |
| `klassepoule` | string | Klassepoule |
| `spelsoort` | string | Spelsoort |
| `competitiesoort` | string | Competitiesoort |
| `geslacht` | string | Geslacht |
| `teamsoort` | string | Teamsoort |
| `leeftijdscategorie` | string | Leeftijdscategorie |
| `kalespelsoort` | string | Spelsoort |
| `speeldag` | string | Speeldag |
| `speeldagteam` | string | Speeldagteam |
| `more` | link | Meer |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/teams?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "teamcode": 1390,
    "lokaleteamcode": -1,
    "poulecode": 42337,
    "teamnaam": "Voorbeeldclub 1",
    "competitienaam": "Dames Senioren",
    "klasse": "1e Klasse",
    "poule": "NW DS-1A NV",
    "klassepoule": "1e Klasse NW DS-1A NV",
    "spelsoort": "Veld",
    "competitiesoort": "regulier",
    "geslacht": "vrouw",
    "teamsoort": "bond",
    "leeftijdscategorie": "Senioren (D)",
    "kalespelsoort": "VE",
    "speeldag": "",
    "speeldagteam": "zondag speeldag",
    "more": "team-indeling?teamcode=1390&lokaleteamcode=-1"
  },
  {
    "teamcode": 2775,
    "lokaleteamcode": -1,
    "poulecode": 42298,
    "teamnaam": "Voorbeeldclub 1",
    "competitienaam": "Dames Senioren",
    "klasse": "1e Klasse",
    "poule": "NW DS-1A Z",
    "klassepoule": "1e Klasse NW DS-1A Z",
    "spelsoort": "Zaal",
    "competitiesoort": "regulier",
    "geslacht": "vrouw",
    "teamsoort": "bond",
    "leeftijdscategorie": "Senioren (D)",
    "kalespelsoort": "ZA",
    "speeldag": "",
    "speeldagteam": "zondag speeldag",
    "more": "team-indeling?teamcode=2775&lokaleteamcode=-1"
  },
  {
    "teamcode": 1391,
    "lokaleteamcode": -1,
    "poulecode": 44364,
    "teamnaam": "Voorbeeldclub 1",
    "competitienaam": "Dames Senioren najaar",
    "klasse": "Poule",
    "poule": "NW B DS-02 V",
    "klassepoule": "Poule NW B DS-02 V",
    "spelsoort": "Veld",
    "competitiesoort": "regulier",
    "geslacht": "vrouw",
    "teamsoort": "bond",
    "leeftijdscategorie": "Senioren (D)",
    "kalespelsoort": "VE",
    "speeldag": "",
    "speeldagteam": "zondag speeldag",
    "more": "team-indeling?teamcode=1391&lokaleteamcode=-1"
  }
]
```

## Valkuilen en bondsregels

- Een team kan in meer competities spelen, zoals competitie en beker. Filter dan op `competitiesoort`.
- De waarden van de filters komen uit de `keuzelijst-*`-artikelen en verschillen per bond.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [keuzelijst-competitieperiode](keuzelijst-competitieperiode.md), [keuzelijst-competitiesoorten](keuzelijst-competitiesoorten.md), [keuzelijst-geslacht](keuzelijst-geslacht.md), [keuzelijst-leeftijdscategorieen](keuzelijst-leeftijdscategorieen.md), [keuzelijst-spelsoorten](keuzelijst-spelsoorten.md), [keuzelijst-teamsoorten](keuzelijst-teamsoorten.md)
- **Levert invoer voor:** [programma](programma.md), [team-gegevens](team-gegevens.md), [team-indeling](team-indeling.md), [team-sponsors](team-sponsors.md), [team-trainingenlijst](team-trainingenlijst.md), [teampoulelijst](teampoulelijst.md), [uitslagen](uitslagen.md)
