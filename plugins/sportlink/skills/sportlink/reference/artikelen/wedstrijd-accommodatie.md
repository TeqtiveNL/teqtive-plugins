# wedstrijd-accommodatie

## Wat het teruggeeft

Geeft de accommodatie van een wedstrijd: naam, adres, plaats, telefoon en route.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdcode` | integer | **ja** |  | [programma](programma.md) (`wedstrijdcode`) | Wedstrijdcode |

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `wedstrijd.thuisteam` |  | Thuisteam |
| `wedstrijd.accommodatienaam` |  | Accommodatienaam |
| `wedstrijd.adres` |  | Straat |
| `wedstrijd.plaats` |  | Plaats |
| `wedstrijd.telefoonnummer` |  | Telefoonnummer |
| `wedstrijd.route` | map | Route |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/wedstrijd-accommodatie?client_id=$SPORTLINK_CLIENT_ID&wedstrijdcode=<wedstrijdcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "wedstrijd": {
    "thuisteam": "Voorbeeldclub 1",
    "accommodatienaam": "Sportpark Voorbeeld",
    "adres": "Voorbeeldstraat 1",
    "plaats": "Voorbeeldstad",
    "telefoonnummer": "",
    "route": "https://example.org"
  }
}
```

## Gerelateerd

- **Invoer uit:** [programma](programma.md)
- **Levert invoer voor:** geen
