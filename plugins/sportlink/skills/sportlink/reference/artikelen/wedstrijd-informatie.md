# wedstrijd-informatie

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Valkuilen en bondsregels](#valkuilen-en-bondsregels)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft alle details van één wedstrijd: nummer, veld, tijden, rijders, officials en score.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdcode` | integer | **ja** |  | [programma](programma.md) (`wedstrijdcode`) | Wedstrijdcode |

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `wedstrijdinformatie.wedstrijdnummer` | integer | Wedstrijdnummer |
| `wedstrijdinformatie.wedstijdnummerintern` | integer | Wedstijdnummerintern |
| `wedstrijdinformatie.veldnaam` |  | Veld |
| `wedstrijdinformatie.veldlocatie` |  | Veldlocatie |
| `wedstrijdinformatie.vertrektijd` |  | Vertrektijd |
| `wedstrijdinformatie.rijder` |  | Rijder |
| `wedstrijdinformatie.thuisscore` |  | Thuisscore |
| `wedstrijdinformatie.thuisscore-regulier` |  | Thuisscore regulier |
| `wedstrijdinformatie.thuisscore-nv` |  | Thuisscore na verlenging |
| `wedstrijdinformatie.thuisscore-s` |  | Thuisscore strafschoppen |
| `wedstrijdinformatie.uitscore` |  | Uitscore |
| `wedstrijdinformatie.uitscore-regulier` |  | Uitscore regulier |
| `wedstrijdinformatie.uitscore-nv` |  | Uitscore na verlenging |
| `wedstrijdinformatie.uitscore-s` |  | Uitscore strafschoppen |
| `wedstrijdinformatie.klasse` |  | Klasse |
| `wedstrijdinformatie.wedstrijdtype` |  | Wedstrijdtype |
| `wedstrijdinformatie.competitietype` |  | Competitietype |
| `wedstrijdinformatie.categorie` |  | Categorie |
| `wedstrijdinformatie.wedstrijddatetime` | datetime | Wedstrijddatum |
| `wedstrijdinformatie.wedstrijddatum` | string | Wedstrijddatum |
| `wedstrijdinformatie.wedstrijddatumopgemaakt` | string | Wedstrijddatum opgemaakt |
| `wedstrijdinformatie.aanvangstijd` |  | Aanvangstijd |
| `wedstrijdinformatie.aanvangstijdopgemaakt` |  | Aanvangstijd opgemaakt |
| `wedstrijdinformatie.duur` |  | Duur |
| `wedstrijdinformatie.speltype` |  | Speltype |
| `wedstrijdinformatie.aanduiding` |  | Aanduiding |
| `wedstrijdinformatie.poulecode` | integer | Poulecode |
| `wedstrijdinformatie.poule` |  | Poule |
| `wedstrijdinformatie.thuisteamid` | integer | Thuisteamid |
| `wedstrijdinformatie.thuisteam` |  | Thuisteam |
| `wedstrijdinformatie.uitteamid` | integer | Uitteamid |
| `wedstrijdinformatie.uitteam` |  | Uitteam |
| `wedstrijdinformatie.opmerkingen` |  | Opmerkingen |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `officials.verenigingsscheidsrechtercode` |  | Verenigingsscheidsrechtercode |
| `officials.verenigingsscheidsrechter` |  | Verenigingsscheidsrechter |
| `officials.overigeofficialcode` |  | Overige officialcode |
| `officials.overigeofficial` |  | Overige official |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `matchofficials.scheidsrechters` |  | Scheidsrechters |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `kleedkamers.thuis` |  | Thuis |
| `kleedkamers.uit` |  | Uit |
| `kleedkamers.official` |  | Official |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `accommodatie.naam` |  | Naam |
| `accommodatie.straat` |  | Straat |
| `accommodatie.plaats` |  | Plaats |
| `accommodatie.telefoon` |  | Telefoonnummer |
| `accommodatie.routeplanner` | map | Routeplanner |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `thuisteam.naam` |  | Naam |
| `thuisteam.code` |  | Code |
| `thuisteam.website` |  | Website |
| `thuisteam.shirtkleur` |  | Shirtkleur |
| `thuisteam.straat` |  | Straat |
| `thuisteam.postcodeplaats` |  | Postcode en plaats |
| `thuisteam.telefoon` |  | Telefoon |
| `thuisteam.email` |  | Email |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `uitteam.naam` |  | Naam |
| `uitteam.code` |  | Code |
| `uitteam.website` |  | Website |
| `uitteam.shirtkleur` |  | Shirtkleur |
| `uitteam.straat` |  | Straat |
| `uitteam.postcodeplaats` |  | Postcode en plaats |
| `uitteam.telefoon` |  | Telefoon |
| `uitteam.email` |  | Email |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/wedstrijd-informatie?client_id=$SPORTLINK_CLIENT_ID&wedstrijdcode=<wedstrijdcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "wedstrijdinformatie": {
    "wedstrijdnummer": 12345,
    "wedstijdnummerintern": 1772348,
    "veldnaam": "zaal 1",
    "veldlocatie": "Sportpark Voorbeeld",
    "vertrektijd": null,
    "rijder": "",
    "thuisscore": null,
    "thuisscore-regulier": null,
    "thuisscore-nv": null,
    "thuisscore-s": null,
    "uitscore": null,
    "uitscore-regulier": null,
    "uitscore-nv": null,
    "uitscore-s": null,
    "klasse": "Poule",
    "wedstrijdtype": "Reguliere competitie",
    "competitietype": "Dames Midweek",
    "categorie": "B",
    "wedstrijddatetime": "2026-11-10T21:00:00+0100",
    "wedstrijddatum": "2026-11-10",
    "wedstrijddatumopgemaakt": "10 nov.",
    "aanvangstijd": "21:00:00",
    "aanvangstijdopgemaakt": "21:00",
    "duur": "50",
    "speltype": "Zaal",
    "aanduiding": "Dames Midweek",
    "poulecode": 43597,
    "poule": "NW C DMW-02 Z (35+)",
    "thuisteamid": 4245,
    "thuisteam": "Voorbeeldclub 1",
    "uitteamid": 4230,
    "uitteam": "Voorbeeldclub 1",
    "opmerkingen": ""
  },
  "officials": {
    "verenigingsscheidsrechtercode": null,
    "verenigingsscheidsrechter": null,
    "overigeofficialcode": null,
    "overigeofficial": null
  },
  "matchofficials": {
    "scheidsrechters": "Voornaam Achternaam"
  },
  "kleedkamers": {
    "thuis": "",
    "uit": "",
    "official": ""
  },
  "accommodatie": {
    "naam": "Voornaam Achternaam",
    "straat": "Voorbeeldstraat 1",
    "plaats": "Voorbeeldstad",
    "telefoon": "",
    "routeplanner": "https://example.org"
  },
  "thuisteam": {
    "naam": "Voornaam Achternaam",
    "code": "XYZ9999",
    "website": "https://example.org",
    "shirtkleur": "Oranje",
    "straat": "Voorbeeldstraat 1",
    "postcodeplaats": "1234 AB",
    "telefoon": "0600000000",
    "email": "naam@example.org"
  },
  "uitteam": {
    "naam": "Voornaam Achternaam",
    "code": "XYZ9999",
    "website": "https://example.org",
    "shirtkleur": "Blauw",
    "straat": "Voorbeeldstraat 1",
    "postcodeplaats": "1234 AB",
    "telefoon": "0600000000",
    "email": "naam@example.org"
  }
}
```

## Valkuilen en bondsregels

- **KNVB:** tot en met Onder-9 staat de wedstrijd er wel, maar zonder score.

## Gerelateerd

- **Invoer uit:** [programma](programma.md)
- **Levert invoer voor:** geen
