# scheidsrechtersaanstellingen

## Wat het teruggeeft

Geeft welke scheidsrechters bij welke wedstrijden zijn aangesteld, ook clubscheidsrechters.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `aantalregels` | integer | nee | `5` |  | Maximum aantal regels |
| `aantaldagen` | integer | nee | `15` |  | Maximum aantal dagen vooruit |
| `weekoffset` | integer | nee | `0` |  | Weeknummer vanaf nu |
| `sorteervolgorde` | string | nee | `datum` | [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md) (`sorteervolgorde`) | Sorteervolgorde |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen** (unieke sleutel: `wedstrijdcode`).

| Veld | Type | Label |
|---|---|---|
| `datetime` | datetime | Datum |
| `datum` | string | Datum |
| `aanvangstijd` | clocktime | Aanvangstijd |
| `scheidsrechters` | string | Scheidsrechter |
| `wedstrijd` | string | Wedstrijd |
| `wedstrijdcode` | integer | Wedstrijdcode |
| `wedstrijdnummer` | integer | Wedstrijdnummer |
| `info` | link | Wedstrijdinformatie |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/scheidsrechtersaanstellingen?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "datetime": "2026-11-10T21:00:00+0100",
    "datum": "10 Nov",
    "aanvangstijd": "21:00",
    "scheidsrechters": "Voornaam Achternaam",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "wedstrijdcode": 1772348,
    "wedstrijdnummer": 12345,
    "info": "<vrije tekst>"
  },
  {
    "datetime": "2026-11-14T17:55:00+0100",
    "datum": "14 Nov",
    "aanvangstijd": "17:55",
    "scheidsrechters": "Voornaam Achternaam",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "wedstrijdcode": 1772671,
    "wedstrijdnummer": 12345,
    "info": "<vrije tekst>"
  },
  {
    "datetime": "2026-11-15T11:00:00+0100",
    "datum": "15 Nov",
    "aanvangstijd": "11:00",
    "scheidsrechters": "Voornaam Achternaam",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "wedstrijdcode": 1772721,
    "wedstrijdnummer": 12345,
    "info": "<vrije tekst>"
  }
]
```

## Valkuilen en bondsregels

- Standaard 15 dagen en 5 regels.

## Gerelateerd

- **Invoer uit:** [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md)
- **Levert invoer voor:** geen
