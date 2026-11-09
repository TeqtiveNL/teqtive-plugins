# trainingenlijst

## Wat het teruggeeft

Geeft alle trainingen van de club met trainers.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `trainingid` | integer | Trainingcode |
| `trainingnaam` | string | Trainingnaam |
| `trainernaam1` | string | Trainernaam1 |
| `trainernaam2` | string | Trainernaam2 |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/trainingenlijst?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "trainingid": 32502,
    "trainingnaam": "Dinsdag Veld Dames 1 & Heren 1",
    "trainernaam1": "Voornaam Achternaam",
    "trainernaam2": null
  },
  {
    "trainingid": 32523,
    "trainingnaam": "ZAAL HB1",
    "trainernaam1": "Voornaam Achternaam",
    "trainernaam2": "Voornaam Achternaam"
  },
  {
    "trainingid": 32526,
    "trainingnaam": "ZAAL Do. D1 & E1",
    "trainernaam1": "Voornaam Achternaam",
    "trainernaam2": "Voornaam Achternaam"
  }
]
```

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** [trainingdetails](trainingdetails.md)
