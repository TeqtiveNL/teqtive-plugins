# wedstrijd-officials

## Wat het teruggeeft

Geeft de aangestelde officials van een wedstrijd.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdcode` | integer | **ja** |  | [programma](programma.md) (`wedstrijdcode`) | Wedstrijdcode |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `officialnaam` | string | Naam |
| `officialomschrijving` | string | Functie |
| `relatiecode` | string | Relatienummer |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/wedstrijd-officials?client_id=$SPORTLINK_CLIENT_ID&wedstrijdcode=<wedstrijdcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "officialnaam": "Voornaam Achternaam",
    "officialomschrijving": "Scheidsrechter",
    "relatiecode": null
  }
]
```

## Gerelateerd

- **Invoer uit:** [programma](programma.md)
- **Levert invoer voor:** geen
