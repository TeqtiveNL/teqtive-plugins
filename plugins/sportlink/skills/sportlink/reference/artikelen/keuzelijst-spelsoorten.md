# keuzelijst-spelsoorten

## Wat het teruggeeft

Geeft de spelsoorten, zoals veld en zaal.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `waarde` | string | waarde |
| `omschrijving` | string | omschrijving |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/keuzelijst-spelsoorten?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "waarde": "alles",
    "omschrijving": "Alles"
  },
  {
    "waarde": "ve",
    "omschrijving": "Veld"
  },
  {
    "waarde": "za",
    "omschrijving": "Zaal"
  }
]
```

## Valkuilen en bondsregels

- De waarden verschillen per bond: haal ze op voor de club en cache ze. Zie [bonden.md](../bonden.md#standen-en-keuzelijsten).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** [programma](programma.md), [teams](teams.md), [uitslagen](uitslagen.md)
