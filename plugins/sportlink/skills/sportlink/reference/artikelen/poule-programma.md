# poule-programma

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Valkuilen en bondsregels](#valkuilen-en-bondsregels)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft het programma van een hele poule, ook van wedstrijden zonder eigen team.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `poulecode` | integer | **ja** |  | [poulelijst](poulelijst.md) (`poulecode`) | Poule code |
| `aantaldagen` | integer | nee | `30` |  | Maximum aantal dagen vooruit |
| `weekoffset` | integer | nee | `0` |  | Weeknummer vanaf nu |
| `eigenwedstrijden` | string | nee | `ja` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Eigenwedstrijden |
| `gebruiklokaleteamgegevens` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Gebruik lokale teamnamen |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen**.

| Veld | Type | Label |
|---|---|---|
| `wedstrijdcode` | integer | Wedstrijdcode |
| `wedstrijddatum` | datetime | Datum |
| `datum` | date | Datum |
| `aanvangstijd` | clocktime | Tijd |
| `thuisteam` | string | Thuis |
| `uitteam` | string | Uit |
| `thuisteamclubrelatiecode` | string | Thuisteam-clubrelatiecode |
| `uitteamclubrelatiecode` | string | Uitteam-clubrelatiecode |
| `accommodatie` | string | Accommodatie |
| `plaats` | string | Plaats |
| `status` | string | Status |
| `wedstrijdnummer` | string | Wedstrijdnummer |
| `datumopgemaakt` | string | Datumopgemaakt |
| `wedstrijd` | string | Wedstrijd |
| `thuisteamid` | string | Thuisteamid |
| `uitteamid` | string | uitteamid |
| `eigenteam` | boolean | eigenteam |
| `meer` | link | Meer |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/poule-programma?client_id=$SPORTLINK_CLIENT_ID&poulecode=<poulecode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
[
  {
    "wedstrijdcode": 1772962,
    "wedstrijddatum": "2026-11-14T19:30:00+0100",
    "datum": "2026-11-14 00:00:00.00",
    "aanvangstijd": "19:30",
    "thuisteam": "Voorbeeldclub 1",
    "uitteam": "Voorbeeldclub 1",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "accommodatie": "Sportpark Voorbeeld",
    "plaats": "Voorbeeldstad",
    "status": "Te spelen",
    "wedstrijdnummer": 12345,
    "datumopgemaakt": "14 nov.",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "thuisteamid": "2397",
    "uitteamid": "2571",
    "eigenteam": "true",
    "meer": "wedstrijd-informatie?wedstrijdcode=1772962&poulecode=43361"
  },
  {
    "wedstrijdcode": 1773264,
    "wedstrijddatum": "2026-11-22T14:00:00+0100",
    "datum": "2026-11-22 00:00:00.00",
    "aanvangstijd": "14:00",
    "thuisteam": "Voorbeeldclub 1",
    "uitteam": "Voorbeeldclub 1",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "accommodatie": "Sportpark Voorbeeld",
    "plaats": "Voorbeeldstad",
    "status": "Te spelen",
    "wedstrijdnummer": 12345,
    "datumopgemaakt": "22 nov.",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "thuisteamid": "2571",
    "uitteamid": "13729",
    "eigenteam": "true",
    "meer": "wedstrijd-informatie?wedstrijdcode=1773264&poulecode=43361"
  },
  {
    "wedstrijdcode": 1773699,
    "wedstrijddatum": "2026-11-29T12:00:00+0100",
    "datum": "2026-11-29 00:00:00.00",
    "aanvangstijd": "12:00",
    "thuisteam": "Voorbeeldclub 1",
    "uitteam": "Voorbeeldclub 1",
    "thuisteamclubrelatiecode": "XYZ9999",
    "uitteamclubrelatiecode": "XYZ9999",
    "accommodatie": "Sportpark Voorbeeld",
    "plaats": "Voorbeeldstad",
    "status": "Te spelen",
    "wedstrijdnummer": 12345,
    "datumopgemaakt": "29 nov.",
    "wedstrijd": "Voorbeeldclub 1 - Tegenstander 1",
    "thuisteamid": "2335",
    "uitteamid": "2571",
    "eigenteam": "true",
    "meer": "wedstrijd-informatie?wedstrijdcode=1773699&poulecode=43361"
  }
]
```

## Valkuilen en bondsregels

- Standaard 30 dagen vanaf deze week (`weekoffset=0`). Met `eigenwedstrijden` beperk je tot de eigen wedstrijden.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [poulelijst](poulelijst.md)
- **Levert invoer voor:** geen
