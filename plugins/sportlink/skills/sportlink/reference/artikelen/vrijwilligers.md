# vrijwilligers

## Wat het teruggeeft

Geeft wie een vrijwilligerstaak doet en wanneer.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `vrijwilligerstaakcode` | integer | **ja** |  | [vrijwilligerstaken](vrijwilligerstaken.md) (`vrijwilligerstaakcode`) | Vrijwilligerstaakcode |
| `weekoffset` | integer | nee | `0` |  | Weeknummer vanaf nu |
| `aantaldagen` | integer | nee | `30` |  | Maximum aantal dagen vooruit |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `naam` | string | Naam |
| `datumvanaf` | datetime | Datum vanaf |
| `datumtot` | datetime | Datum tot |
| `tijdvanaf` | string | Tijd vanaf |
| `tijdtot` | string | Tijd tot |
| `lokatie` | string | Lokatie |
| `heledag` | string | Hele dag |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/vrijwilligers?client_id=$SPORTLINK_CLIENT_ID&vrijwilligerstaakcode=<vrijwilligerstaakcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "naam": "<Naam>",
    "datumvanaf": "<Datum vanaf>",
    "datumtot": "<Datum tot>",
    "tijdvanaf": "<Tijd vanaf>",
    "tijdtot": "<Tijd tot>",
    "lokatie": "<Lokatie>",
    "heledag": "<Hele dag>"
  }
]
```

## Valkuilen en bondsregels

- Bevat persoonsgegevens.

## Gerelateerd

- **Invoer uit:** [vrijwilligerstaken](vrijwilligerstaken.md)
- **Levert invoer voor:** geen
