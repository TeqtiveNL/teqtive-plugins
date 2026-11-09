# keuzelijst-periodenummers

## Wat het teruggeeft

Geeft de periodes van een poule en welke de huidige is.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `poulecode` | integer | **ja** |  | [poulelijst](poulelijst.md) (`poulecode`) | Poulecode |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `waarde` | integer | Periodenummer |
| `omschrijving` | string | Omschrijving |
| `huidig` | string | Huidige periodenummer |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/keuzelijst-periodenummers?client_id=$SPORTLINK_CLIENT_ID&poulecode=<poulecode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "waarde": 0,
    "omschrijving": "<Omschrijving>",
    "huidig": "<Huidige periodenummer>"
  }
]
```

## Valkuilen en bondsregels

- De waarden verschillen per bond: haal ze op voor de club en cache ze. Zie [bonden.md](../bonden.md#standen-en-keuzelijsten).

## Gerelateerd

- **Invoer uit:** [poulelijst](poulelijst.md)
- **Levert invoer voor:** geen
