# wedstrijd-statistieken

## Wat het teruggeeft

Geeft statistieken van beide teams, zoals het percentage gewonnen wedstrijden thuis en uit.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdcode` | integer | **ja** |  | [programma](programma.md) (`wedstrijdcode`) | Wedstrijdcode |

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `thuisteam.naam` | string | Naam |
| `thuisteam.thuisgewonnen` | string | Thuis gewonnen |
| `thuisteam.uitgewonnen` | string | Uit gewonnen |
| `thuisteam.percentagegewonnen` | string | Procent gewonnen |
| `thuisteam.percentagethuisgewonnen` | string | Procent thuis gewonnen |
| `thuisteam.percentageuitgewonnen` | string | Procent uit gewonnen |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `uitteam.naam` | string | Naam |
| `uitteam.thuisgewonnen` | string | Thuis gewonnen |
| `uitteam.uitgewonnen` | string | Uit gewonnen |
| `uitteam.percentagegewonnen` | string | Procent gewonnen |
| `uitteam.percentagethuisgewonnen` | string | Procent thuis gewonnen |
| `uitteam.percentageuitgewonnen` | string | Procent uit gewonnen |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/wedstrijd-statistieken?client_id=$SPORTLINK_CLIENT_ID&wedstrijdcode=<wedstrijdcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "thuisteam": {
    "naam": "Voornaam Achternaam",
    "thuisgewonnen": "95",
    "uitgewonnen": "81",
    "percentagegewonnen": "62%",
    "percentagethuisgewonnen": "67%",
    "percentageuitgewonnen": "57%"
  },
  "uitteam": {
    "naam": "Voornaam Achternaam",
    "thuisgewonnen": "81",
    "uitgewonnen": "68",
    "percentagegewonnen": "51%",
    "percentagethuisgewonnen": "56%",
    "percentageuitgewonnen": "47%"
  }
}
```

## Valkuilen en bondsregels

- **KNVB:** voor competities tot en met Onder-9 geeft dit artikel geen standen of uitslagen. Een lege response bij een JO9-team is dus correct. Zie [bonden.md](../bonden.md#knvb).

## Gerelateerd

- **Invoer uit:** [programma](programma.md)
- **Levert invoer voor:** geen
