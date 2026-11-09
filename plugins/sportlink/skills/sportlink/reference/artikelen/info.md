# info

## Wat het teruggeeft

Geeft de ClientID en de bond van de club terug; gebruik het om te testen of een key werkt en om de sport te bepalen.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `client_id` | string | **ja** |  |  | Client id |

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `Info.ClientId` | string | Client id |
| `Info.Bond` | string | Bond |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/info?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "Info": {
    "ClientId": "<CLIENT_ID>",
    "Bond": "NHV"
  }
}
```

## Valkuilen en bondsregels

- De response bevat de ClientID zelf (genest in `Info`). Maskeer recursief, zie [verbinden.md](../verbinden.md#live-patroon).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
