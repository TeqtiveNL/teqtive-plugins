# Foutcodes en lege data

## Foutvorm

Bij een fout geeft de API JSON in deze vorm:

```json
{"error": {"message": "Invalid or expired client id", "code": 4012}}
```

Herken een fout aan de `code`, want die is stabiel. De `message` kan veranderen.

## Codes

| HTTP | code | Betekenis | Wat te doen |
|---|---|---|---|
| 400 | 4001 | conditiefout; de details staan in een `messages`-array | lees de `messages`; meestal een parameterwaarde buiten de grenzen |
| 400 | 4002 | verplicht argument ontbreekt | controleer de verplichte parameters in het artikelbestand |
| 401 | 4011 | token ontbreekt of is ongeldig | hoort bij artikelen met ledenlogin, en die vallen buiten deze skill |
| 401 | 4012 | `client_id` ontbreekt of is ongeldig | controleer of `$SPORTLINK_CLIENT_ID` in deze terminal gezet is en of de club nog abonnee is |
| 403 | 4031 | het token mist de vereiste scope | buiten deze skill (ledenlogin) |
| 404 | 4041 | het artikel bestaat niet | controleer de artikelnaam in `/list` |
| 500 | 5001 | serverfout bij Sportlink | later opnieuw proberen |

4012 gaat vóór 4041. Een verkeerd gespelde artikelnaam met een ongeldige ClientID geeft dus 4012, niet 4041.

## Lege data

Een lege lijst is meestal geen fout. Controleer in deze volgorde:

1. **Bondsregel:** een bond kan data weglaten, bijvoorbeeld standen bij de jongste jeugd. Zie [bonden.md](bonden.md).
2. **Bond voert de competitie niet in Sportlink:** dan geven competitie-artikelen niets terug. Zie [bonden.md](bonden.md).
3. **Seizoensmoment:** in de zomer lopen de indeling en planning nog, waardoor het programma ontbreekt. Na een herindeling, zoals tussen de najaars- en voorjaarsreeks, verandert de `teampoulelijst`.
4. **Privacyniveau:** leden met het niveau "Afgeschermd" verschijnen niet, en niet-leden nooit.
5. **Lokaal team zonder koppeling:** oefenwedstrijden van een lokaal team verschijnen alleen als dat team aan een bondsteam gekoppeld is.
6. **Periode-parameters:** `aantaldagen` en `weekoffset` bepalen het tijdvenster. Een te klein venster geeft een lege lijst.

Bij data die verkeerd is, ligt de oorzaak in Sportlink Club (de club) of bij de bond. De API geeft alleen door wat daar staat.
