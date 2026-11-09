# team-gegevens

## Wat het teruggeeft

Geeft de gegevens van één team, zoals naam, competitie en looptijd.

## Parameters

| Naam | Type | Verplicht | Standaard | Waarden uit | Omschrijving |
|---|---|---|---|---|---|
| `teamcode` | integer | **ja** |  | [teams](teams.md) (`teamcode`) | Teamcode |
| `lokaleteamcode` | integer | **ja** |  | [teams](teams.md) (`lokaleteamcode`) | Teamcode lokaal |

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `team.teamnaam` | string | Teamnaam |
| `team.begindatum` | string | Begindatum |
| `team.begindatetime` | datetime | Begindatum |
| `team.einddatum` | string | Einddatum |
| `team.einddatetime` | datetime | Einddatum |
| `team.competitie` | string | Competitie |
| `team.geslacht` | string | Geslacht |
| `team.categorie` | string | Categorie |
| `team.shirtkleur` | string | Shirtkleur |
| `team.broekkleur` | string | Broekkleur |
| `team.kousen` | string | Kousen |
| `team.omschrijving` | string | Omschrijving |
| `team.teamfoto` | binary | Teamfoto |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/team-gegevens?client_id=$SPORTLINK_CLIENT_ID&teamcode=<teamcode>&lokaleteamcode=<lokaleteamcode>" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "team": {
    "teamnaam": "Voorbeeldclub 1",
    "begindatum": null,
    "begindatetime": null,
    "einddatum": null,
    "einddatetime": null,
    "competitie": "",
    "geslacht": "vrouw",
    "categorie": "Veld",
    "shirtkleur": null,
    "broekkleur": null,
    "kousen": null,
    "omschrijving": null,
    "teamfoto": null
  }
}
```

## Gerelateerd

- **Invoer uit:** [teams](teams.md)
- **Levert invoer voor:** geen
