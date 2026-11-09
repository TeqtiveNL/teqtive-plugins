# Verbinden met Club.Dataservice

- [Basis](#basis)
- [De ClientID](#de-clientid)
- [Live-patroon](#live-patroon)
- [Response en caching](#response-en-caching)
- [Testomgeving en JS-library](#testomgeving-en-js-library)

## Basis

| | |
|---|---|
| Basis-URL | `https://data.sportlink.com/<artikel>` |
| Methode | `GET`, met alle invoer als query-parameters |
| Authenticatie | query-parameter `client_id`, verplicht bij elk artikel behalve `list` |
| Formaat | altijd JSON (`application/json;charset=utf-8`); een XML-variant bestaat niet |
| CORS | `Access-Control-Allow-Origin: *` |
| Catalogus | `https://data.sportlink.com/list`: alle artikelen met hun invoer en uitvoer, zonder ClientID op te vragen |

Voorbeeld: `https://data.sportlink.com/poulestand?client_id=$SPORTLINK_CLIENT_ID&poulecode=<poulecode>`

## De ClientID

- **Wat:** één sleutel per club. Hij geeft toegang tot de artikelen van die ene club.
- **Hoe krijg je hem:** de club bestelt Club.Dataservice in de Shop van Sportlink Club. Daarna staat de ClientID onder *Vereniging > Beheer > Gebruikersbeheer*, tabblad *Clubsite*.
- **Leveranciers:** een websitebouwer mag de ClientID van de club gebruiken, maar de club moet zelf abonnee zijn.
- **Controle:** het artikel `info` geeft de bond van de club terug (`{"Info":{"ClientId":…,"Bond":…}}`). Daarmee test je of de key werkt en voor welke bond de club speelt.

## Live-patroon

De ontwikkelaar draait dit zelf in zijn eigen terminal. De ClientID wordt verborgen gevraagd en nergens opgeslagen. Hij bestaat alleen als variabele in die ene terminal.

**Stap 1: ClientID verborgen invoeren.** Kies de regel die bij de shell hoort.

zsh (standaard op macOS):

```bash
read -s "SPORTLINK_CLIENT_ID?ClientID: "; echo
```

bash:

```bash
read -s -p "ClientID: " SPORTLINK_CLIENT_ID; echo
```

**Stap 2: de maskering klaarzetten.** Dit Python-fragment vervangt elke sleutel waarin `client` voorkomt door `***`, op elk niveau:

```bash
SPORTLINK_MASK='import json, sys
def mask(x):
    if isinstance(x, dict):
        return {k: ("***" if "client" in k.lower() else mask(v)) for k, v in x.items()}
    if isinstance(x, list):
        return [mask(i) for i in x]
    return x
print(json.dumps(mask(json.load(sys.stdin)), indent=2, ensure_ascii=False))'
```

Het maskeren moet **recursief** zijn: `info` en andere artikelen geven de ClientID genest terug, en een maskering op alleen het bovenste niveau laat hem dan in de uitvoer staan.

**Stap 3: het artikel aanroepen.** Vervang `<artikel>` en de parameters:

```bash
curl -s "https://data.sportlink.com/<artikel>?client_id=$SPORTLINK_CLIENT_ID&<param>=<waarde>" | python3 -c "$SPORTLINK_MASK"
```

Stap 3 kan daarna in dezelfde terminal net zo vaak herhaald worden als nodig. Elk artikelbestand bevat deze call, al ingevuld voor dat artikel.

## Response en caching

- De meeste artikelen geven een **lijst van rijen**. De kolommen staan per artikel in het artikelbestand onder *Uitvoervelden*.
- Lege data is vaak geen fout: zie [foutcodes.md](foutcodes.md#lege-data).
- Sportlink zet een nginx-cache voor de API. Een wijziging in Sportlink Club is daardoor niet altijd meteen zichtbaar.
- Rate limits zijn niet gedocumenteerd en er komen geen rate-limit-headers mee. Cache aan de kant van de clubsite: minuten voor programma en uitslagen, uren voor clubgegevens en keuzelijsten.

## Testomgeving en JS-library

- Er bestaat een testomgeving op `https://datatest.sportlink.com`, met een eigen `/list`. Het is onbekend of een productie-ClientID daar werkt. Gebruik standaard productie.
- Sportlink heeft een officiële JavaScript-library voor clubsites in de browser: https://sportlinkservices.github.io/navajofeeds-json-parser/. Deze skill schrijft voorbeelden rechtstreeks op de REST-artikelen; noem de library als optie voor wie hem wil gebruiken.
