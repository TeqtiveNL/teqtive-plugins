# bestuur

## Wat het teruggeeft

Geeft de bestuursleden van de club met hun functie en contactgegevens.

## Parameters

Geen parameters, behalve `client_id`.

## Uitvoervelden

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `voorzitter.naam` | string | Naam |
| `voorzitter.email` | email | Email |
| `voorzitter.email2` | email | 2e Email |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `secretaris.naam` | string | Naam |
| `secretaris.email` | email | Email |
| `secretaris.email2` | email | 2e Email |

Vorm volgens de catalogus: een **object**; geneste velden staan als `pad.veld`.

| Veld | Type | Label |
|---|---|---|
| `penningmeester.naam` | string | Naam |
| `penningmeester.email` | email | Email |
| `penningmeester.email2` | email | 2e Email |

## Voorbeeld-call

Eerst de ClientID verborgen invoeren en de maskering klaarzetten: zie [verbinden.md](../verbinden.md#live-patroon). Daarna:

```bash
curl -s "https://data.sportlink.com/bestuur?client_id=$SPORTLINK_CLIENT_ID" | python3 -c "$SPORTLINK_MASK"
```

## Voorbeeldresponse

Geanonimiseerde response van een echte club (maximaal 3 rijen).

```json
{
  "voorzitter": {
    "naam": "Voornaam Achternaam",
    "email": null,
    "email2": null
  },
  "secretaris": {
    "naam": "Voornaam Achternaam",
    "email": "naam@example.org",
    "email2": ""
  },
  "penningmeester": {
    "naam": "Voornaam Achternaam",
    "email": "naam@example.org",
    "email2": ""
  }
}
```

## Valkuilen en bondsregels

- Bevat persoonsgegevens; wat zichtbaar is, hangt af van het privacyniveau van elk lid.

## Gerelateerd

- **Invoer uit:** geen
- **Levert invoer voor:** geen
