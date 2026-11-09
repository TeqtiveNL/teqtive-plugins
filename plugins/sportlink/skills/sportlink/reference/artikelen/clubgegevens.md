# clubgegevens

- [Wat het teruggeeft](#wat-het-teruggeeft)
- [Parameters](#parameters)
- [Uitvoervelden](#uitvoervelden)
- [Voorbeeld-call](#voorbeeld-call)
- [Voorbeeldresponse](#voorbeeldresponse)
- [Gerelateerd](#gerelateerd)

## Wat het teruggeeft

Geeft de gegevens van de club: naam, code, adressen, contact en clubkleuren.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `gegevens.thuisshirtkleur` | string | Thuisshirtkleur |
| `gegevens.thuisbroekkleur` | string | Thuisbroekkleur |
| `gegevens.thuissokkenkleur` | string | Thuissokkenkleur |
| `gegevens.uitshirtkleur` | string | Uitshirtkleur |
| `gegevens.uitbroekkleur` | string | Uitbroekkleur |
| `gegevens.uitsokkenkleur` | string | Uitsokkenkleur |
| `gegevens.clubcode` | string | Clubcode |
| `gegevens.clubnaam` | string | Clubnaam |
| `gegevens.informatie` | string | Informatie |
| `gegevens.privacystatementclub` | string | Tijdelijke url naar de privacy statement van de club |
| `gegevens.oprichtingsdatum` | string | Oprichtingsdatum |
| `gegevens.oprichtingsdatetime` | datetime | Oprichtingsdatum |
| `gegevens.telefoonnummer` | string | Telefoonnummer |
| `gegevens.fax` | string | Fax |
| `gegevens.email` | email | Email |
| `gegevens.website` | string | Website |
| `gegevens.facebook` | string | Facebook |
| `gegevens.instagram` | string | Instagram |
| `gegevens.twitter` | string | Twitter |
| `gegevens.youtube` | string | Youtube |
| `gegevens.straatnaam` | string | Straatnaam |
| `gegevens.huisnummer` | string | Huisnummer |
| `gegevens.nummertoevoeging` | string | Nummertoevoeging |
| `gegevens.postcode` | string | Postcode |
| `gegevens.plaats` | string | Plaats |
| `gegevens.banknummer` | string | Banknummer |
| `gegevens.tennamevan` | string | Te name van |
| `gegevens.tennamevanplaats` | string | Te name van plaats |
| `gegevens.naamsecretaris` | string | Naam secretaris |
| `gegevens.kvknummer` | string | KvK-nummer |
| `gegevens.logo` | binary | Logo |
| `gegevens.kleinlogo` | binary | Klein logo |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `bezoekadres.naam` | string | Naam |
| `bezoekadres.straatnaam` | string | Straatnaam |
| `bezoekadres.huisnummer` | string | Huisnummer |
| `bezoekadres.nummertoevoeging` | string | Nummertoevoeging |
| `bezoekadres.postcode` | string | Postcode |
| `bezoekadres.plaats` | string | Plaats |
| `bezoekadres.route` | map | Route |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/clubgegevens?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "gegevens": {
    "thuisshirtkleur": "Oranje",
    "thuisbroekkleur": "Zwart",
    "thuissokkenkleur": "Zwart",
    "uitshirtkleur": "Oranje",
    "uitbroekkleur": "Zwart",
    "uitsokkenkleur": "Zwart",
    "clubcode": "XYZ9999",
    "clubnaam": "Voorbeeldclub",
    "informatie": "",
    "privacystatementclub": null,
    "oprichtingsdatum": "1900-01-01",
    "oprichtingsdatetime": "1900-01-01",
    "telefoonnummer": "0600000000",
    "fax": "",
    "email": "naam@example.org",
    "website": "https://example.org",
    "facebook": "",
    "instagram": "",
    "twitter": "",
    "youtube": "",
    "straatnaam": "Voorbeeldstraat 1",
    "huisnummer": "Voorbeeldstraat 1",
    "nummertoevoeging": "",
    "postcode": "1234 AB",
    "plaats": "Voorbeeldstad",
    "banknummer": "NL00BANK0123456789",
    "tennamevan": "Voorbeeldclub",
    "tennamevanplaats": "",
    "naamsecretaris": "Voornaam Achternaam",
    "kvknummer": "",
    "logo": "https://example.org/afbeelding.png",
    "kleinlogo": "https://example.org/afbeelding.png"
  },
  "bezoekadres": {
    "naam": "Voornaam Achternaam",
    "straatnaam": "Voorbeeldstraat 1",
    "huisnummer": "Voorbeeldstraat 1",
    "nummertoevoeging": "",
    "postcode": "1234 AB",
    "plaats": "Voorbeeldstad",
    "route": "https://example.org"
  }
}
```

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
