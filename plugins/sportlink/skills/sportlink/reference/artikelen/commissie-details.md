# commissie-details

## Wat het teruggeeft

Geeft de gegevens van één commissie.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `commissiecode` | integer | **ja** |  | [commissies](commissies.md) (`commissiecode`) | Commissie code |

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `commissiedetails.commissienaam` | string | Commissienaam |
| `commissiedetails.afbeelding` | binary | Afbeelding |
| `commissiedetails.omschrijving` | string | Omschrijving |
| `commissiedetails.opmerkingen` | string | Opmerkingen |
| `commissiedetails.telefoon` | string | Telefoon |
| `commissiedetails.mobiel` | string | Mobiel |
| `commissiedetails.email` | string | E-mail |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/commissie-details?client_id=$SPORTLINK_CLIENT_ID&commissiecode=<commissiecode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "commissiedetails": {
    "commissienaam": "Activiteiten",
    "afbeelding": null,
    "omschrijving": "Activiteiten ",
    "opmerkingen": "",
    "telefoon": "",
    "mobiel": "",
    "email": ""
  }
}
```

## Gerelateerd

- **Invoer uit:** [commissies](commissies.md)
- **Levert invoer voor:** geen
