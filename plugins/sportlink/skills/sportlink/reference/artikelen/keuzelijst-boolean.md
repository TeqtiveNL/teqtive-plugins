# keuzelijst-boolean

## Wat het teruggeeft

Geeft de geldige ja/nee-waarden voor parameters zoals `gebruiklokaleteamgegevens`.

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
curl -s "https://data.sportlink.com/keuzelijst-boolean?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "waarde": "JA",
    "omschrijving": "Ja"
  },
  {
    "waarde": "NEE",
    "omschrijving": "Nee"
  }
]
```

## Valkuilen en bondsregels

- De waarden verschillen per bond: haal ze op voor de club en cache ze. Zie [bonden.md](../bonden.md#standen-en-keuzelijsten).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** [afgelastingen](afgelastingen.md), [commissie-leden](commissie-leden.md), [poule-programma](poule-programma.md), [poulestand](poulestand.md), [pouleuitslagen](pouleuitslagen.md), [programma](programma.md), [team-indeling](team-indeling.md), [teams](teams.md), [uitslagen](uitslagen.md), [wedstrijd-thuisteam](wedstrijd-thuisteam.md), [wedstrijd-uitteam](wedstrijd-uitteam.md)
