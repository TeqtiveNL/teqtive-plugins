# Bonden en bondsregels

- [Eén API, verschillende bonden](#één-api-verschillende-bonden)
- [Welke bonden](#welke-bonden)
- [Bondsregels](#bondsregels)
- [Standen en keuzelijsten](#standen-en-keuzelijsten)

## Eén API, verschillende bonden

Alle bonden gebruiken dezelfde URL, dezelfde artikelen en één `client_id` per club. De bond bepaalt niet *welke* artikelen er zijn, maar wel *of ze data teruggeven*: competitie-artikelen leveren alleen iets op als de bond zijn competitie in Sportlink voert.

Het artikel `info` geeft de bond van een club terug (veld `Bond`). Begin daarmee als de sport ertoe doet.

## Welke bonden

| Bond | Sport | Competitiedata via Dataservice |
|---|---|---|
| KNVB | voetbal (veld en zaal) | ja |
| KNKV | korfbal | waarschijnlijk ja (niet primair bevestigd) |
| NHV / HandbalNL | handbal | waarschijnlijk ja (niet primair bevestigd) |
| KNZB | zwemmen, waterpolo | waterpolo: ja. Zwemwedstrijden passen niet in teams en poules. |
| KNBSB | honk- en softbal | waarschijnlijk ja |
| Atletiekunie | atletiek | n.v.t.; vooral de artikelen over leden en vereniging |
| Reddingsbrigade Nederland | reddingsbrigade | n.v.t. |
| JBN | judo | n.v.t. |
| KBHB / Hockey Belgium | hockey (België) | ja |
| Nevobo | volleybal | **nee**: Sportlink beheert alleen de leden; zie hieronder |

**Geen Sportlink:**
- **KNHB (hockey in Nederland):** gebruikt LISA, AllUnited of PSD.
- **NBB (basketbal):** sinds 16 juni 2025 over naar Club.Basketball.nl (FOYS).

Vraagt een ontwikkelaar naar een club van deze bonden, zeg dan dat Club.Dataservice daar niet de bron is.

**Nevobo:** programma, uitslagen en standen komen uit de eigen feeds van de Nevobo (`api.nevobo.nl/export/…`), niet uit Club.Dataservice. Voor een volleybalclub gebruik je de artikelen over vereniging, leden en vrijwilligers. De Nevobo-feeds vallen buiten deze skill.

## Bondsregels

### KNVB

- **Jongste jeugd:** voor competities tot en met Onder-9 zijn er geen standen of uitslagen in `periodestand`, `poulestand`, `pouleuitslagen`, `uitslagen`, `wedstrijd-historische-resultaten` en `wedstrijd-statistieken`. `wedstrijd-informatie` toont de wedstrijd wel, maar zonder score. Het programma is er wel. Een lege stand bij een JO9-team is dus correct.
- **Privacy:** `team-indeling` geeft bij KNVB-clubs geen e-mailadressen of telefoonnummers terug.
- **Spelsoort:** veld en zaal (zaalvoetbal).
- **Reeksen:** de jeugd speelt een najaars- en een voorjaarsreeks, met promotie, degradatie en herindeling ertussen. De `teampoulelijst` van een team verandert daardoor midden in het seizoen.
- **Periodes:** bij de senioren wijzen periodestanden periodekampioenen aan. Die spelen met herkansers de nacompetitie.

### Overige bonden

Voor KNKV, NHV, KNZB en KNBSB zijn geen bondsregels gedocumenteerd. Ga uit van de generieke regels en verklaar lege velden met [foutcodes.md](foutcodes.md#lege-data).

## Standen en keuzelijsten

- **Neem standen altijd over uit de API.** De puntentelling verschilt per bond en sport (voetbal 3-1-0, volleybal per set, …). De kolommen van `poulestand` zijn op voetbal geschoeid (`doelpuntenvoor`, `gelijk`, `verliespunten`); bij andere sporten is hun betekenis niet gedocumenteerd.
- **Verliespunten:** punten die door verlies of gelijkspel zijn misgelopen. Daarmee vergelijk je teams die een ongelijk aantal wedstrijden hebben gespeeld.
- **Keuzelijsten verschillen per bond.** Waarden als spelsoort, competitiesoort, teamsoort, leeftijdscategorie en teampersoonrol staan in de `keuzelijst-*`-artikelen. Haal ze op voor de club en cache ze; hardcodeer ze niet. De sport zit in deze waarden, niet in de parameternamen.
