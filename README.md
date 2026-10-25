# dealio.be

**[dealio.be](https://dealio.be)** — today's promotions from 65+ Belgian retailers, every discount worked out per item.

*Nederlands: [zie onderaan](#dealiobe-nederlands).*

## What dealio is

Dealio collects the current promotions of more than 65 Belgian retailers (supermarkets, drugstores, DIY, electronics, toys, pets, fashion) and works every discount out to a price per item, so "2+1 free", "second at half price" and "-25% from 2" become comparable numbers. Every store is fetched once a day, in the morning, and the site is updated as each store finishes. Prices are what the stores showed at that moment; the store has the last word.

Besides the promotions, the site has researched [buying guides](https://dealio.be/koopwijzer/) (models compared, tests, buyer ratings, every statement with its source), [meal ideas](https://dealio.be/kookinspiratie/) built from this week's supermarket promotions, [store-wide campaigns](https://dealio.be/acties/), Belgian [consumer news](https://dealio.be/nieuws/) and a weekly [promo index](https://dealio.be/promo-index/).

- Site: https://dealio.be
- For AI assistants (the page this README mirrors): https://dealio.be/mcp-server/
- Overview for language models: https://dealio.be/llms.txt

## The MCP server: dealio in your AI assistant

Ask an AI assistant about discounts in Belgium and it can query dealio's data directly over an [MCP](https://modelcontextprotocol.io) server, so it works with today's promotions instead of what it once learned. Every answer links to the promotion on dealio.be.

```
https://dealio.be/mcp
```

No account, no key. Streamable HTTP, read-only. Queries in Dutch work best (product names as the stores write them).

**Tools:** `search_deals` (text, store, category, minimum discount, maximum price, ending soon), `get_deal`, `list_stores`, `get_buying_guide`, `get_model`, `get_meal_ideas`, `get_news`, `get_campaigns`, `publish_card` (one promotion as a square picture with a short link, ready to post elsewhere).

### Add it to your client

The address is the same everywhere: `https://dealio.be/mcp`. If your program asks for a login or a key, choose **no authentication**. A server you add yourself is visible only to you; which plans may add custom servers is up to the maker of your program. The steps below are as each maker documents them (October 2026); we have tested Claude Code ourselves.

**Claude** (claude.ai, Claude Desktop and the phone app) — Dealio is in Claude's Connectors Directory as a *Community* connector (*Dealio: Belgian deals*). *Customize* › *Connectors* › *Discover* › search `dealio` › *Connect to Claude*. No sign-in: it connects at once. Once is enough: the connector is then available in the browser, on your computer and on your phone. In a conversation, switch it on via the **+** under the text box › *Connectors*; on the first question Claude may ask for permission (*Allow once* or *Always allow*). Not in the catalogue? Add it yourself: *Customize* › *Connectors* › *Add custom connector*, URL `https://dealio.be/mcp`, authentication *No sign-in*, then *Add* (one custom connector on the free plan).

**Claude Code**

```
claude mcp add --transport http dealio https://dealio.be/mcp
```

**ChatGPT** — go to chatgpt.com/plugins › **+** › *Add custom MCP server*. Name `dealio`, a short description, URL `https://dealio.be/mcp`, no authentication, then *Create as a plugin*. In a new conversation type `@dealio` and your question. Not every plan may add its own servers; where it is allowed with read-only rights, that is enough, since this server can only read.

**Codex** (also the ChatGPT desktop app and the Codex extension)

```
codex mcp add dealio --url https://dealio.be/mcp
```

**Le Chat (Mistral)** — *Connectors* › *+ Add Connector* › tab *Custom MCP Connector*. Name `dealio`, Server URL `https://dealio.be/mcp`, then *Connect*.

**Cursor** — put this in `~/.cursor/mcp.json` (the [`.mcp.json`](.mcp.json) in this repository is the same file):

```json
{ "mcpServers": { "dealio": { "url": "https://dealio.be/mcp" } } }
```

**VS Code** — put this in `.vscode/mcp.json` (note: a different format than Cursor):

```json
{ "servers": { "dealio": { "type": "http", "url": "https://dealio.be/mcp" } } }
```

**Gemini CLI**

```
gemini mcp add --transport http dealio https://dealio.be/mcp
```

**Any other program** that adds an MCP server by address (Streamable HTTP) should work with `https://dealio.be/mcp`. The server is also listed in the official [MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers?search=be.dealio) as `be.dealio/deals`.

### Try it

- "Which coffee capsules are on promotion this week at Delhaize or Colruyt?"
- "Which airfryer should I buy for a family of four?"
- "What can I cook on Saturday with the promotions at Aldi and Lidl? Vegetarian, please."
- "Is there cashback on a Siemens appliance anywhere?"

### What we keep

We count which tool is used, with which query and filters, how many results there were and which program sent the question (the name it gives itself). No IP address and nothing that identifies you. There is a per-minute limit so the server stays fast for everyone. Privacy: https://dealio.be/privacy/

---

# dealio.be (Nederlands)

**[dealio.be](https://dealio.be)** — de kortingen van vandaag bij 65+ Belgische winkels, elke korting omgerekend naar de prijs per stuk.

## Wat dealio is

Dealio verzamelt de lopende promoties van meer dan 65 Belgische winkels (supermarkten, drogisterijen, doe-het-zelf, elektronica, speelgoed, dieren, mode) en rekent elke korting om naar een prijs per stuk, zodat "2+1 gratis", "2e aan halve prijs" en "-25 % vanaf 2" vergelijkbare getallen worden. Elke winkel wordt één keer per dag opgehaald, 's ochtends, en de site wordt bijgewerkt zodra een winkel klaar is. Prijzen zijn wat de winkels op dat moment toonden; de winkel heeft het laatste woord.

Naast de kortingen heeft de site onderzochte [koopwijzers](https://dealio.be/koopwijzer/) (modellen naast elkaar, tests, beoordelingen van kopers, elke uitspraak met haar bron), [kookinspiratie](https://dealio.be/kookinspiratie/) uit de supermarktpromoties van deze week, [winkelacties](https://dealio.be/acties/), Belgisch [consumentennieuws](https://dealio.be/nieuws/) en een wekelijkse [promo-index](https://dealio.be/promo-index/).

- Site: https://dealio.be
- Voor AI-assistenten (de pagina waarvan deze README een kopie is): https://dealio.be/mcp-server/
- Overzicht voor taalmodellen: https://dealio.be/llms.txt

## De MCP-server: dealio in je AI-assistent

Vraag je een AI-assistent naar kortingen in België, dan kan die onze gegevens rechtstreeks opvragen via een [MCP](https://modelcontextprotocol.io)-server. Zo werkt hij met de kortingen van vandaag in plaats van met wat hij ooit geleerd heeft, en elk antwoord bevat een link naar de korting op dealio.be.

```
https://dealio.be/mcp
```

Geen account en geen sleutel nodig. Streamable HTTP, alleen lezen. Vragen in het Nederlands werken het best.

**Tools:** `search_deals` (zoektekst, winkel, categorie, minimale korting, maximumprijs, loopt binnenkort af), `get_deal`, `list_stores`, `get_buying_guide`, `get_model`, `get_meal_ideas`, `get_news`, `get_campaigns`, `publish_card` (één korting als vierkante afbeelding met een korte link, klaar om elders te plaatsen).

### Zo voeg je hem toe

Het adres is overal hetzelfde: `https://dealio.be/mcp`. Vraagt je programma naar een aanmelding of sleutel, kies dan **geen aanmelding**. Een server die je zelf toevoegt, ziet alleen jij; de maker van je programma bepaalt welke abonnementen dat mogen. Hieronder de weg per programma, zoals de maker ze beschrijft (oktober 2026); alleen Claude Code hebben we zelf getest.

**Claude** (claude.ai, Claude Desktop en de app op je telefoon) — Dealio staat in de Connectors Directory van Claude als *Community*-connector (*Dealio: Belgian deals*). *Customize* › *Connectors* › *Discover* › zoek `dealio` › *Connect to Claude*. Geen aanmelding: hij is meteen verbonden. Eén keer volstaat: de connector staat daarna in de browser, op je computer en op je telefoon. In een gesprek zet je hem aan via de **+** links onder het tekstvak › *Connectors*; bij de eerste vraag kan Claude om toestemming vragen (*Allow once* of *Always allow*). Niet in de catalogus? Voeg hem zelf toe: *Customize* › *Connectors* › *Add custom connector*, adres `https://dealio.be/mcp`, aanmelding *No sign-in*, dan *Add* (op het gratis plan één eigen connector).

**Claude Code**

```
claude mcp add --transport http dealio https://dealio.be/mcp
```

**ChatGPT** — ga naar chatgpt.com/plugins › **+** › *Add custom MCP server*. Naam `dealio`, een korte beschrijving, adres `https://dealio.be/mcp`, geen aanmelding, dan *Create as a plugin*. In een nieuw gesprek typ je `@dealio` en je vraag. Niet elk abonnement mag eigen servers toevoegen; waar het mag met alleen leesrechten volstaat dat, want onze server kan alleen lezen.

**Codex** (ook de ChatGPT-app op je computer en de Codex-extensie)

```
codex mcp add dealio --url https://dealio.be/mcp
```

**Le Chat (Mistral)** — *Connectors* › *+ Add Connector* › tabblad *Custom MCP Connector*. Naam `dealio`, Server URL `https://dealio.be/mcp`, dan *Connect*.

**Cursor** — zet dit in `~/.cursor/mcp.json` (de [`.mcp.json`](.mcp.json) in deze repository is hetzelfde bestand):

```json
{ "mcpServers": { "dealio": { "url": "https://dealio.be/mcp" } } }
```

**VS Code** — zet dit in `.vscode/mcp.json` (let op: een ander formaat dan Cursor):

```json
{ "servers": { "dealio": { "type": "http", "url": "https://dealio.be/mcp" } } }
```

**Gemini CLI**

```
gemini mcp add --transport http dealio https://dealio.be/mcp
```

**Ander programma?** Elk programma dat een MCP-server via een adres toevoegt (Streamable HTTP) zou moeten werken met `https://dealio.be/mcp`. De server staat ook in het officiële [MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers?search=be.dealio) als `be.dealio/deals`.

### Probeer eens

- «Welke koffiecapsules zijn deze week in promotie bij Delhaize of Colruyt?»
- «Welke airfryer moet ik kopen voor een gezin van vier?»
- «Wat kan ik zaterdag koken met de kortingen van Aldi en Lidl? Vegetarisch graag.»
- «Is er ergens cashback op een Siemens-toestel?»

### Wat we bijhouden

We tellen welke tool gebruikt wordt, met welke zoekvraag en filters, hoeveel resultaten er waren en welk programma de vraag stuurde (de naam die het zelf opgeeft). Geen IP-adres en niets dat jou aanwijst. Er geldt een limiet per minuut, zodat de server voor iedereen snel blijft. Privacy: https://dealio.be/privacy/

---

Prijzen en voorwaarden kunnen afwijken — de winkel heeft altijd het laatste woord. · Prices and conditions may differ; the store always has the last word.
