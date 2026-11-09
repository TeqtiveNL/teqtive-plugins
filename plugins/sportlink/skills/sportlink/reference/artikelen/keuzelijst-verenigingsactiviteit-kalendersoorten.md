# keuzelijst-verenigingsactiviteit-kalendersoorten

## Wat het teruggeeft

Geeft de soorten activiteiten in de clubagenda.

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
curl -s "https://data.sportlink.com/keuzelijst-verenigingsactiviteit-kalendersoorten?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "waarde": "CLUBEVENT",
    "omschrijving": "Activiteiten"
  },
  {
    "waarde": "ANNIVERSARY",
    "omschrijving": "Feesten & vieringen"
  },
  {
    "waarde": "OTHER",
    "omschrijving": "Overig"
  }
]
```

## Valkuilen en bondsregels

- De waarden verschillen per bond: haal ze op voor de club en cache ze. Zie [bonden.md](../bonden.md#standen-en-keuzelijsten).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
