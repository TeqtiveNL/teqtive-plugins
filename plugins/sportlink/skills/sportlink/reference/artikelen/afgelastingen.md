# afgelastingen

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Valkuilen en bondsregels](#valkuilen-en-bondsregels)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft de afgelaste wedstrijden van de club in een tijdvenster.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `aantaldagen` | integer | nee | `30` |  | Maximum aantal dagen vooruit |
| `aantalregels` | integer | nee | `20` |  | Maximum aantal regels |
| `weekoffset` | integer | nee | `0` |  | Weeknummer vanaf nu |
| `gebruiklokaleteamgegevens` | string | nee | `NEE` | [keuzelijst-boolean](keuzelijst-boolean.md) (`waarde`) | Gebruik lokale teamnamen |
| `sorteervolgorde` | string | nee | `datum` | [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md) (`sorteervolgorde`) | Sorteervolgorde |

## Uitvoervelden

Vorm volgens de catalogus: een **lijst van rijen** (unieke sleutel: `wedstrijdcode`).

| Veld | Type | Label |
|---|---|---|
| `wedstrijdcode` | integer | Code |
| `wedstrijdnummer` | integer | Wedstrijdnummer |
| `teamnaam` | string | Teamnaam |
| `thuisteamclubrelatiecode` | string | Thuisteam-clubrelatiecode |
| `uitteamclubrelatiecode` | string | Uitteam-clubrelatiecode |
| `thuisteam` | string | Thuisteam |
| `thuisteamid` | string | Thuisteamid |
| `thuisteamlogo` | string | Thuisteam logo |
| `uitteam` | string | Uitteam |
| `uitteamid` | string | Uitteamid |
| `uitteamlogo` | string | Uitteam logo |
| `accommodatie` | string | Accommodatie |
| `teamvolgorde` | string | Teamvolgorde |
| `rijders` | string | Rijders |
| `scheidsrechters` | string | Scheidsrechters |
| `veld` | string | Veld |
| `zaalofveld` | string | Zaal of veld |
| `vertrektijd` | string | Vertrektijd |
| `aanvangstijd` | string | Aanvangstijd |
| `status` | string | Status |
| `datum` | string | Datum |
| `wedstrijddatum` | datetime | Wedstrijddatum |
| `wedstrijd` | string | Wedstrijd |
| `plaats` | string | Plaats |
| `info` | link | Wedstrijdinformatie |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/afgelastingen?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

*Synthetisch voorbeeld, opgebouwd uit de uitvoervelden.*

```json
[
  {
    "wedstrijdcode": 0,
    "wedstrijdnummer": 0,
    "teamnaam": "<Teamnaam>",
    "thuisteamclubrelatiecode": "<Thuisteam-clubrelatiecode>",
    "uitteamclubrelatiecode": "<Uitteam-clubrelatiecode>",
    "thuisteam": "<Thuisteam>",
    "thuisteamid": "<Thuisteamid>",
    "thuisteamlogo": "<Thuisteam logo>",
    "uitteam": "<Uitteam>",
    "uitteamid": "<Uitteamid>",
    "uitteamlogo": "<Uitteam logo>",
    "accommodatie": "<Accommodatie>",
    "teamvolgorde": "<Teamvolgorde>",
    "rijders": "<Rijders>",
    "scheidsrechters": "<Scheidsrechters>",
    "veld": "<Veld>",
    "zaalofveld": "<Zaal of veld>",
    "vertrektijd": "<Vertrektijd>",
    "aanvangstijd": "<Aanvangstijd>",
    "status": "<Status>",
    "datum": "<Datum>",
    "wedstrijddatum": "<Wedstrijddatum>",
    "wedstrijd": "<Wedstrijd>",
    "plaats": "<Plaats>",
    "info": "<Wedstrijdinformatie>"
  }
]
```

## Valkuilen en bondsregels

- Standaard 30 dagen en 20 regels. Een afgelasting door de bond, de club of de scheidsrechter verschijnt hier en in de wedstrijdstatus.

## Gerelateerd

- **Invoer uit:** [keuzelijst-boolean](keuzelijst-boolean.md), [keuzelijst-sorteervolgordes](keuzelijst-sorteervolgordes.md)
- **Levert invoer voor:** geen
