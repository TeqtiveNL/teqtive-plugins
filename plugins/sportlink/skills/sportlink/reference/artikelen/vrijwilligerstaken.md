# vrijwilligerstaken

## Wat het teruggeeft

Geeft de vrijwilligerstaken van de club.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `vrijwilligerstaakcode` | integer | Code |
| `naam` | string | Naam |
| `taakbeheerder` | string | Taakbeheerder |
| `omschrijving` | string | Omschrijving |
| `startdatum` | datetime | Startdatum |
| `einddatum` | datetime | Einddatum |
| `locatie` | string | Locatie |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/vrijwilligerstaken?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "vrijwilligerstaakcode": 0,
    "naam": "<Naam>",
    "taakbeheerder": "<Taakbeheerder>",
    "omschrijving": "<Omschrijving>",
    "startdatum": "<Startdatum>",
    "einddatum": "<Einddatum>",
    "locatie": "<Locatie>"
  }
]
```

## Valkuilen en bondsregels

- De `vrijwilligerstaakcode` gebruik je in [vrijwilligers](vrijwilligers.md).

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** [vrijwilligers](vrijwilligers.md)
