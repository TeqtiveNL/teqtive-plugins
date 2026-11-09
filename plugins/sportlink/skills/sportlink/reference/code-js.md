# Codevoorbeelden: JavaScript en TypeScript

De ClientID staat in de omgevingsvariabele `SPORTLINK_CLIENT_ID` op de server en wordt alleen server-side gelezen.

**Naamgeving:** functies, variabelen, types en commentaar zijn Engels, zoals `fetchUpcomingMatches` of `type Match`. Alleen de velden uit de API houden hun Nederlandse naam (`wedstrijdcode`, `aantaldagen`).

## Eén helper voor elk artikel

```ts
// sportlink.ts: minimal client for Sportlink Club.Dataservice (Node 18+, built-in fetch)
const BASE_URL = "https://data.sportlink.com";

export class SportlinkError extends Error {
  constructor(public status: number, public code: number | undefined, message: string) {
    super(message);
  }
}

export async function fetchArticle<T = unknown>(
  article: string,
  params: Record<string, string | number> = {},
): Promise<T> {
  const clientId = process.env.SPORTLINK_CLIENT_ID;
  if (!clientId) throw new Error("SPORTLINK_CLIENT_ID is not set");

  const url = new URL(`${BASE_URL}/${article}`);
  url.searchParams.set("client_id", clientId);
  for (const [key, value] of Object.entries(params)) url.searchParams.set(key, String(value));

  const res = await fetch(url);
  const body = await res.json();
  // Sportlink returns errors as { error: { message, code } }
  if (!res.ok || body?.error) {
    throw new SportlinkError(res.status, body?.error?.code, body?.error?.message ?? res.statusText);
  }
  return body as T;
}
```

Gebruik de foutcode (`err.code`) uit [foutcodes.md](foutcodes.md) om fouten af te handelen, bijvoorbeeld een melding voor de beheerder bij 4012.

## Navigatie volgen

```ts
// Standing for a team by name: teams (already carries poulecode) -> poulestand
type Team = {
  teamnaam: string;
  teamcode: number;
  lokaleteamcode: number;
  poulecode: number;
  competitiesoort: string;
};

export async function standingForTeam(teamName: string, competitiesoort?: string) {
  const teams = await fetchArticle<Team[]>("teams");
  const matches = teams.filter((t) => t.teamnaam === teamName);
  // A team can play in several competitions (league and cup): optionally filter on competitiesoort
  const team = matches.find((t) => !competitiesoort || t.competitiesoort === competitiesoort);
  return team ? fetchArticle("poulestand", { poulecode: team.poulecode }) : null;
}
```

Gebruik de veldnamen uit het artikelbestand (*Uitvoervelden*). De waarden van `competitiesoort` staan in `keuzelijst-competitiesoorten` en verschillen per bond. Voor alle poules van één team is er `teampoulelijst`.

## Caching

Sportlink documenteert geen rate limits. Cache daarom aan de serverkant:

```ts
// Tiny in-memory cache; use your framework's cache (Next.js revalidate, Redis, …) in production
const cache = new Map<string, { expires: number; value: unknown }>();

export async function cachedArticle<T>(article: string, params = {}, ttlSeconds = 300): Promise<T> {
  const key = article + JSON.stringify(params);
  const hit = cache.get(key);
  if (hit && hit.expires > Date.now()) return hit.value as T;
  const value = await fetchArticle<T>(article, params);
  cache.set(key, { expires: Date.now() + ttlSeconds * 1000, value });
  return value;
}
```

Richtwaarden: een paar minuten voor `programma`, `uitslagen` en `poulestand`; uren voor `clubgegevens`, `teams` en `keuzelijst-*`.

## In de browser

De API staat CORS van elke origin toe, dus een call vanuit de browser werkt technisch. De ClientID staat dan wel zichtbaar in de code van de pagina. Of dat acceptabel is, is nog niet beslist. Tot die tijd: laat de browser je eigen server-endpoint aanroepen, en laat die server de Sportlink-call doen.
