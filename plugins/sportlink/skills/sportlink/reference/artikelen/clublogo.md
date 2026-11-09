# clublogo

## Wat het teruggeeft

Geeft het logo van de club.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `ClubData.Logo` |  | Logo |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/clublogo?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
{
  "ClubData": {
    "Logo": "<Logo>"
  }
}
```

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
