# pouleuitslagen

## Wat het teruggeeft

Geeft de uitslagen van een hele poule.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `aantaldagen` | integer | nee | `14` |  | Maximum aantal dagen vooruit |
| `weekoffset` | integer | nee | `-2` |  | Weeknummer vanaf nu |
| `poulecode` | integer | **ja** |  | [poulelijst](poulelijst.md) (`poulecode`) | Poule code |
| `eigenwedstrijden` | string | nee | `ja` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Eigenwedstrijden |
| `sorteervolgorde` | string | nee | `datum` | [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md) (`sorteervolgorde`) | Sorteervolgorde |
| `gebruiklokaleteamgegevens` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Gebruik lokale teamnamen |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen** (`eigenteam` markeert het eigen team).

| Veld | Type | Label |
|---|---|---|
| `wedstrijdcode` | integer | Wedstrijdcode |
| `wedstrijddatum` | datetime | Datum |
| `wedstrijdnummer` | integer | Wedstrijdnummer |
| `accommodatie` | string | Accommodatie |
| `datumopgemaakt` | string | Datum opgemaakt |
| `aanvangstijd` | date | Aanvangstijd |
| `wedstrijd` | string | Wedstrijd |
| `datum` | string | datum |
| `thuisteamid` | string | Thuisteamid |
| `thuisteam` | string | Thuisteam |
| `uitteamid` | string | Uitteamid |
| `uitteam` | string | Uitteam |
| `thuisteamclubrelatiecode` | string | Thuisteam-clubrelatiecode |
| `uitteamclubrelatiecode` | string | Uitteam-clubrelatiecode |
| `uitslag` | string | Uitslag |
| `eigenteam` | boolean | eigenteam |
| `status` | string | status |
| `meer` | link | Meer |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/pouleuitslagen?client_id=$SPORTLINK_CLIENT_ID&poulecode=<poulecode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "wedstrijdcode": 1772142,
    "wedstrijddatum": "2026-11-08T12:00:00+0100",
    "wedstrijdnummer": 12345,
    "accommodatie": "Sportpark Voorbeeld",
    "datumopgemaakt": "8 nov.",
    "aanvangstijd": "12:00",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "datum": "2026-11-08 00:00:00.00",
    "thuisteamid": "12650",
    "thuisteam": "Voorbeeldclub 1",
    "uitteamid": "2571",
    "uitteam": "Voorbeeldclub 1",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "uitslag": "12 - 16",
    "eigenteam": "true",
    "status": "Uitgespeeld",
    "meer": "wedstrijd-informatie?wedstrijdcode=1772142&poulecode=43361"
  }
]
```

## Valkuilen en bondsregels

- **KNVB:** voor competities tot en met Onder-9 geeft dit artikel geen standen of uitslagen. Een lege response bij een JO9-team is dus correct. Zie [bonden.md](../bonden.md#knvb).
- `aantaldagen` maximaal 250.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md), [poulelijst](poulelijst.md)
- **Levert invoer voor:** geen
