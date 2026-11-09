# Navigatie tussen artikelen

Veel artikelen hebben een code nodig die uit een ander artikel komt. De vaste volgorde van sleutels is: **teamnaam → teamcode → poulecode → wedstrijdcode**. Verwar de interne codes niet met de publieke nummers: `wedstrijdcode` is iets anders dan `wedstrijdnummer`, en `poulecode` iets anders dan `publiekepoulecode`.

## De keten

```
teams ──teamcode + lokaleteamcode──► teampoulelijst ──poulecode──► poulestand
  │                                                      ├──► poule-programma, pouleuitslagen
  │                                                      ├──► poule-indeling
  │                                                      └──► keuzelijst-periodenummers ─► periodestand
  ├──► team-gegevens, team-indeling, team-sponsors, team-trainingenlijst
  └──► programma, uitslagen (filter op teamcode) ──wedstrijdcode──► wedstrijd-informatie,
        wedstrijd-thuisteam, wedstrijd-uitteam, wedstrijd-deelnemers, wedstrijd-officials,
        wedstrijd-accommodatie, wedstrijd-kleedkamers, wedstrijd-statistieken,
        wedstrijd-historische-resultaten

poulelijst        alle poules van de club (poulecode, publiekepoulecode, teamcode)
commissies        ──commissiecode──► commissie-details, commissie-leden
vrijwilligerstaken ──vrijwilligerstaakcode──► vrijwilligers
trainingenlijst   ──trainingid──► trainingdetails
keuzelijst-*      geldige waarden voor filterparameters (teamsoort, spelsoort, …)
```

`teamcode` en `lokaleteamcode` gaan altijd samen mee.

Een `poulecode` kan uit twee artikelen komen. De catalogus noemt `poulelijst` als bron: alle poules van de club. Voor de poules van één team gebruik je `teampoulelijst`.

## Voorbeeld: "Hoe staat JO13-1 ervoor?"

1. `teams`: zoek de rij met `teamnaam` "JO13-1". Die rij bevat al `poulecode`, `competitiesoort`, `competitienaam` en `klasse`.
2. Speelt het team in meer poules, zoals competitie en beker? Dan geeft `teampoulelijst` met `teamcode` en `lokaleteamcode` alle poules van dat team, met `poulecode`, `teamcode` en `teamnaam`.
3. `poulestand` met de gekozen `poulecode`.

## Relaties uit de catalogus

Per parameter vermeldt `/list` welk artikel geldige waarden levert (`sourcearticle`). Onderstaande tabel is daaruit gegenereerd.

| Artikel | Parameter | Komt uit | Verplicht |
|---|---|---|---|
| [commissie-details](artikelen/commissie-details.md) | `commissiecode` | [commissies](artikelen/commissies.md).`commissiecode` | ja |
| [commissie-leden](artikelen/commissie-leden.md) | `commissiecode` | [commissies](artikelen/commissies.md).`commissiecode` | ja |
| [keuzelijst-periodenummers](artikelen/keuzelijst-periodenummers.md) | `poulecode` | [poulelijst](artikelen/poulelijst.md).`poulecode` | ja |
| [periodestand](artikelen/periodestand.md) | `poulecode` | [poulelijst](artikelen/poulelijst.md).`poulecode` | ja |
| [poule-indeling](artikelen/poule-indeling.md) | `poulecode` | [poulelijst](artikelen/poulelijst.md).`poulecode` | ja |
| [poule-programma](artikelen/poule-programma.md) | `poulecode` | [poulelijst](artikelen/poulelijst.md).`poulecode` | ja |
| [poulestand](artikelen/poulestand.md) | `poulecode` | [poulelijst](artikelen/poulelijst.md).`poulecode` | ja |
| [pouleuitslagen](artikelen/pouleuitslagen.md) | `poulecode` | [poulelijst](artikelen/poulelijst.md).`poulecode` | ja |
| [programma](artikelen/programma.md) | `lokaleteamcode` | [teams](artikelen/teams.md).`lokaleteamcode` | nee |
| [programma](artikelen/programma.md) | `teamcode` | [teams](artikelen/teams.md).`teamcode` | nee |
| [team-gegevens](artikelen/team-gegevens.md) | `teamcode` | [teams](artikelen/teams.md).`teamcode` | ja |
| [team-gegevens](artikelen/team-gegevens.md) | `lokaleteamcode` | [teams](artikelen/teams.md).`lokaleteamcode` | ja |
| [team-indeling](artikelen/team-indeling.md) | `teamcode` | [teams](artikelen/teams.md).`teamcode` | ja |
| [team-indeling](artikelen/team-indeling.md) | `lokaleteamcode` | [teams](artikelen/teams.md).`lokaleteamcode` | ja |
| [team-sponsors](artikelen/team-sponsors.md) | `teamcode` | [teams](artikelen/teams.md).`teamcode` | ja |
| [team-sponsors](artikelen/team-sponsors.md) | `lokaleteamcode` | [teams](artikelen/teams.md).`lokaleteamcode` | ja |
| [team-trainingenlijst](artikelen/team-trainingenlijst.md) | `teamcode` | [teams](artikelen/teams.md).`teamcode` | ja |
| [team-trainingenlijst](artikelen/team-trainingenlijst.md) | `lokaleteamcode` | [teams](artikelen/teams.md).`lokaleteamcode` | ja |
| [teampoulelijst](artikelen/teampoulelijst.md) | `teamcode` | [teams](artikelen/teams.md).`teamcode` | ja |
| [teampoulelijst](artikelen/teampoulelijst.md) | `lokaleteamcode` | [teams](artikelen/teams.md).`lokaleteamcode` | ja |
| [trainingdetails](artikelen/trainingdetails.md) | `trainingid` | [trainingenlijst](artikelen/trainingenlijst.md).`trainingid` | ja |
| [uitslagen](artikelen/uitslagen.md) | `teamcode` | [teams](artikelen/teams.md).`teamcode` | nee |
| [uitslagen](artikelen/uitslagen.md) | `lokaleteamcode` | [teams](artikelen/teams.md).`lokaleteamcode` | nee |
| [vrijwilligers](artikelen/vrijwilligers.md) | `vrijwilligerstaakcode` | [vrijwilligerstaken](artikelen/vrijwilligerstaken.md).`vrijwilligerstaakcode` | ja |
| [wedstrijd-accommodatie](artikelen/wedstrijd-accommodatie.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
| [wedstrijd-deelnemers](artikelen/wedstrijd-deelnemers.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
| [wedstrijd-historische-resultaten](artikelen/wedstrijd-historische-resultaten.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
| [wedstrijd-informatie](artikelen/wedstrijd-informatie.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
| [wedstrijd-kleedkamers](artikelen/wedstrijd-kleedkamers.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
| [wedstrijd-officials](artikelen/wedstrijd-officials.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
| [wedstrijd-statistieken](artikelen/wedstrijd-statistieken.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
| [wedstrijd-thuisteam](artikelen/wedstrijd-thuisteam.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
| [wedstrijd-uitteam](artikelen/wedstrijd-uitteam.md) | `wedstrijdcode` | [programma](artikelen/programma.md).`wedstrijdcode` | ja |
