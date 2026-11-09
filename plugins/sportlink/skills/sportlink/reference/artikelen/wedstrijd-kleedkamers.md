# wedstrijd-kleedkamers

## Wat het teruggeeft

Geeft de kleedkamers voor thuisteam, uitteam en scheidsrechter bij een wedstrijd.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `wedstrijdcode` | integer | **ja** |  | [programma](programma.md) (`wedstrijdcode`) | Wedstrijdcode |

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `kleedkamers.scheidsrechters-kleedkamer` |  | Scheidsrechterskleedkamer |
| `kleedkamers.thuisteam-kleedkamer` |  | Thuisteamkleedkamer |
| `kleedkamers.uitteam-kleedkamer` |  | Uitteamkleedkamer |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/wedstrijd-kleedkamers?client_id=$SPORTLINK_CLIENT_ID&wedstrijdcode=<wedstrijdcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "kleedkamers": {
    "scheidsrechters-kleedkamer": "",
    "thuisteam-kleedkamer": "",
    "uitteam-kleedkamer": ""
  }
}
```

## Gerelateerd

- **Invoer uit:** [programma](programma.md)
- **Levert invoer voor:** geen
