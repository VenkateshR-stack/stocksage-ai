# StockSage AI

StockSage turns a product link into a price and availability watch. It records observations in the browser, detects price drops and stock transitions, remembers the last time an item was available, and uses NVIDIA Nemotron on Nebius Token Factory to interpret product pages and produce a short buy-or-wait signal.

Built for the **Nebius × NVIDIA Global AI Hackathon** — **Best Apps and Agents** track.

**Live demo:** https://stocksage-ai.venz1z.chatgpt.site

**Source:** https://github.com/VenkateshR-stack/stocksage-ai

Hackathon materials: [Devpost draft](DEVPOST_SUBMISSION.md) · [demo script](DEMO_SCRIPT.md) · [submission checklist](HACKATHON_CHECKLIST.md)

## Demo features

- Paste a product URL from Amazon, Flipkart, Nykaa, or another public retailer.
- Extract JSON-LD and Open Graph product data on the server.
- Call NVIDIA Nemotron through the Nebius Token Factory OpenAI-compatible API.
- Store a private price/stock timeline in browser local storage.
- Detect price drops, target hits, out-of-stock changes, and restocks.
- Show when a product was last observed in stock.
- Remain useful in demo mode before the Nebius secret is connected.

## Runtime flow

```text
Product link → server-side page fetch → structured metadata
                                          ↓ if ambiguous
                         NVIDIA Nemotron on Token Factory
                                          ↓
                     normalized price + stock snapshot
                                          ↓
            browser history → transition alerts → SageSignal
```

## Configuration

Configure these server-side environment variables in the hosting platform:

| Variable | Required | Purpose |
| --- | --- | --- |
| `NEBIUS_API_KEY` | Yes for AI extraction | Token Factory API key |
| `NEBIUS_BASE_URL` | No | Defaults to `https://api.tokenfactory.nebius.com/v1` |
| `NEBIUS_MODEL` | No | Defaults to `nvidia/nemotron-3-super-120b-a12b` |

Never commit the API key.

## Build

The hosted version is a dependency-free Cloudflare Worker.

```bash
bash scripts/build.sh
node scripts/validate-artifact.mjs
```

## Retailer compatibility

Retailers can block automated requests or render product data only after browser scripts run. StockSage reports these failures rather than inventing a price. A production release should add official affiliate/product feeds and store-specific adapters behind the same normalized snapshot API.

## Roadmap

- Durable cloud history and scheduled background checks
- Email, WhatsApp, Telegram, and browser-push delivery
- Cross-store matching for the same product
- Coupon, shipping, bank-offer, and per-unit price comparison
- Restock probability and expected sale-window forecasting

## License

MIT

