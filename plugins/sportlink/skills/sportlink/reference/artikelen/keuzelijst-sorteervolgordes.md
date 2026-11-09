# keuzelijst-sorteervolgordes

## Wat het teruggeeft

Geeft de mogelijke sorteervolgordes voor programma en uitslagen.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `sorteervolgorde` | string | Sorteervolgorde |
| `omschrijving` | string | Omschrijving |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/keuzelijst-sorteervolgordes?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "sorteervolgorde": "datum",
    "omschrijving": "Datum, tijd"
  },
  {
    "sorteervolgorde": "datum-omgekeerd",
    "omschrijving": "Datum, tijd (omgekeerd)"
  },
  {
    "sorteervolgorde": "team",
    "omschrijving": "Team, datum, tijd"
  }
]
```

## Valkuilen en bondsregels

- De waarden verschillen per bond: haal ze op voor de club en cache ze. Zie [bonden.md](../bonden.md#standen-en-keuzelijsten).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** [afgelastingen](afgelastingen.md), [pouleuitslagen](pouleuitslagen.md), [programma](programma.md), [scheidsrechtersaanstellingen](scheidsrechtersaanstellingen.md), [uitslagen](uitslagen.md)
