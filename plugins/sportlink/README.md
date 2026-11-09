# sportlink

Een Claude Code-plugin met kennis van de **Sportlink Club.Dataservice API**, voor ontwikkelaars die een clubsite of app bouwen. Claude weet daarmee:
- hoe je verbindt met je `client_id`
- welke artikelen (endpoints) er zijn, met hun parameters, uitvoervelden en voorbeeldresponses
- hoe je van teams via poules naar wedstrijden navigeert
- welke bondsregels gelden
- hoe je de data gebruikt in JavaScript/TypeScript en PHP/WordPress

> **Disclaimer:** dit is een onofficieel project. Het is niet gelieerd aan, gesponsord door of goedgekeurd door Sportlink. "Sportlink" wordt alleen gebruikt om te beschrijven waarvoor de plugin bedoeld is.

## Installeren

```bash
claude plugin marketplace add Miesjh/teqtive-plugins
```

```bash
claude plugin install sportlink@teqtive-plugins
```

## Gebruik

Stel je vraag gewoon in Claude Code, bijvoorbeeld "Hoe toon ik de stand van ons team op onze WordPress-site?" De skill laadt dan vanzelf.

- **Zonder ClientID** beantwoordt Claude vragen uit de kennis in de skill: artikelen, velden, codevoorbeelden en bondsregels.
- **Met ClientID** geeft Claude op verzoek een commando dat je zelf in je terminal draait. Je ClientID voer je daar verborgen in. Hij wordt nergens opgeslagen en verschijnt niet in de chat.

Je ClientID krijg je als je club Club.Dataservice bestelt via de Shop in Sportlink Club. Daarna vind je hem onder *Vereniging > Beheer > Gebruikersbeheer*, tabblad *Clubsite*.

## Welke sporten

De plugin werkt voor bonden die hun data in Sportlink voeren, zoals de KNVB, KNKV, NHV, KNZB en KNBSB. De KNHB (hockey) en de NBB (basketbal) gebruiken geen Sportlink. Programma, uitslagen en standen van de Nevobo (volleybal) komen uit de eigen feeds van de Nevobo, niet uit Club.Dataservice.

## Licentie

MIT © Teqtive. Zie [`LICENSE`](LICENSE).
