# keuzelijst-factuurstatussen

## Wat het teruggeeft

Geeft de statussen van facturen; alleen relevant voor de artikelen met ledenlogin, die buiten deze skill vallen.

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
curl -s "https://data.sportlink.com/keuzelijst-factuurstatussen?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "waarde": "ALLES",
    "omschrijving": "Alles"
  },
  {
    "waarde": "DEFINITIEF",
    "omschrijving": "Definitief"
  },
  {
    "waarde": "VOORLOPIG",
    "omschrijving": "Voorlopig"
  }
]
```

## Valkuilen en bondsregels

- De waarden verschillen per bond: haal ze op voor de club en cache ze. Zie [bonden.md](../bonden.md#standen-en-keuzelijsten).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
