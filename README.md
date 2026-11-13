# Nero Quote Builder

Turns a UK tradesperson's site visit into a priced, VAT-correct quote with a branded PDF and a phone page the customer accepts in one tap. For electricians, plumbers and heating engineers, builders, roofers and decorators.

**Endpoint:** `https://quote-builder.nerolabs.workers.dev/mcp` (MCP, Streamable HTTP)
**Sign-in:** No account sign-in. The first call (setup_trade) gives the business a private key starting qbk_. Your AI keeps it and passes it with each call; in apps that allow headers you can set it once as "Authorization: Bearer qbk_...". Lose the key and you set up again.
**How to connect:** https://quote-builder.nerolabs.workers.dev/docs
**Privacy:** https://quote-builder.nerolabs.workers.dev/privacy
**Support:** founder@neroengine.com

## Tools

| Tool | What it does |
|---|---|
| `setup_trade` | Set up or update the business quoting profile. Create a business, or update its saved settings (call with trade_key to update). |
| `get_trade` | Show the business profile, price book, stats and free allowance. The trade's saved settings, price book (most used first), quote stats (win rate, value won in the last 12 months) and, for a business that is not VAT registered, a warning when accepted work is nearing the £90,000 VAT registration threshold. |
| `save_price_items` | Save materials to the price book. Add or update materials in the trade's price book, so later quotes can use { code, qty } and the cost, unit and markup fill in. |
| `draft_quote` | Draft a priced, VAT-correct quote. Price a job after a site visit. |
| `revise_quote` | Change or withdraw a quote. Change a quote. Send only the fields that change (a list you send, such as materials, replaces that whole list). |
| `finalise_quote` | Finalise a quote and get the customer link. Lock a draft so the customer can answer it. |
| `quote_activity` | See what customers did with quotes. What customers have done since the trade last checked: quotes opened, accepted (with the name they signed, extras ticked and final total), questions asked, declined. |
| `get_quote` | Show one quote in full. One quote in full: lines, totals, VAT working with HMRC sources, margins (trade only), the customer's answer, history (drafted, sent, opened, accepted) and links. |
| `list_quotes` | List quotes. Recent quotes, newest first, with status (draft, sent, viewed, queried, accepted, declined, expired, withdrawn), total and whether there is news. |
| `reply_to_customer` | Answer a customer question on the quote page. Answer a customer's question. |
| `export_to_nero_work` | Export a quote in Nero Work format. The quote in the exact argument shape of the Nero Work exchange's submit_quote tool (labour_minor, materials_minor, vat_minor in pence, validity_hours, exclusions, notes), checked with Nero Work's own rules. |

Every tool carries a plain title and the read-only, destructive and open-world hints, so your AI app can ask before anything that changes data.

## Connect

- **Claude (web or desktop):** Settings, Connectors, Add custom connector, paste the endpoint.
- **ChatGPT:** Settings, Apps and connectors, Advanced settings, switch on Developer mode, then Create, paste the endpoint, No authentication.
- **Claude Code:** `claude mcp add --transport http quote-builder https://quote-builder.nerolabs.workers.dev/mcp`
- **Cursor, VS Code, Windsurf and others:**

```json
{ "mcpServers": { "quote-builder": { "type": "http", "url": "https://quote-builder.nerolabs.workers.dev/mcp" } } }
```

## Try asking

- "Set me up on Quote Builder: Brightline Electrical, VAT registered, day rate £280, my mate £160 a day, 15% on materials, 25% deposit."
- "Quote the Patel job: full rewire of a 3 bed semi, 11 days, with a 7 kW EV charger as an optional extra. Show me the total before you finalise."
- "Any news on my quotes? Has Mrs Patel opened hers or asked anything?"

## Good to know

- Free: 5 finalised quotes a month for every business, counted per UK calendar month. Drafts, revisions, replies and exports never count. There is no paid plan and no card.
- The tool never sends anything to your customers. You send the link yourself by text, WhatsApp or email.
- VAT is worked out from your VAT registration and each line's VAT type, with the HMRC rule named. You stay responsible for the prices and VAT treatment you choose.
- Every quote can be handed to Nero Work, the job exchange for trades, in its exact quote format.

## Privacy

What is kept, what is never kept, and how to get data deleted: https://quote-builder.nerolabs.workers.dev/privacy. Usage counts log the tool name, time, AI app name, country and a one-way scrambled caller code; never your questions, the answers or IP addresses.

This repository holds the listing only (README and server.json). The server runs at the endpoint above.

Built by Nero Labs (Nero Engine Group Ltd, UK).
