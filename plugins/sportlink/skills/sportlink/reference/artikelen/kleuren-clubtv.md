# kleuren-clubtv

## Wat het teruggeeft

Geeft de kleuren voor de club-tv-weergave.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `kleuren.primair` | string | Primairekleur |
| `kleuren.secundair` | string | Secundairekleur |
| `kleuren.tekst` | string | Tekstkleur |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/kleuren-clubtv?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "kleuren": {
    "primair": "#FFFFFF",
    "secundair": "#FFFFFF",
    "tekst": "#000000"
  }
}
```

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
