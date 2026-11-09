# kleuren-clubdata

## Wat het teruggeeft

Geeft de websitekleuren die de club in Sportlink heeft ingesteld.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `kleuren.header` | string | Headerkleur |
| `kleuren.menu` | string | Menukleur |
| `kleuren.achtergrond` | string | Achtergrondkleur |
| `kleuren.tekst` | string | Tekstkleur |
| `kleuren.menuselectie` | string | Menuselectiekleur |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/kleuren-clubdata?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "kleuren": {
    "header": "#FFFE5C",
    "menu": "#FF5644",
    "achtergrond": "#f77a45",
    "tekst": "#6FFF4A",
    "menuselectie": "#58FFEB"
  }
}
```

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
