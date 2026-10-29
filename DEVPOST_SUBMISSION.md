# StockSage AI — Devpost submission draft

## Project name

StockSage AI

## Tagline

Paste any product link. Know when to buy—and when it comes back.

## Track

Best Apps and Agents

## Inspiration

Shopping alerts usually solve only half the problem. A price tracker may report a discount, but it often cannot tell whether the item is actually available. A restock notifier may announce that something returned, but it forgets the price history and cannot explain whether the current offer is good. StockSage combines both signals in one simple workflow: paste a link and build a useful product timeline.

## What it does

StockSage accepts a public product URL from stores such as Amazon, Flipkart, Nykaa, and other retailers. It fetches the page on the server, extracts structured product metadata, and uses NVIDIA Nemotron through Nebius Token Factory when the page is ambiguous. Each successful check becomes a local observation containing the price, currency, availability, and timestamp.

From those observations, StockSage can surface:

- current price and availability;
- price drops, price rises, and target-price hits;
- out-of-stock to in-stock transitions;
- when the product was last observed in stock;
- a compact price/stock history; and
- a short SageSignal that explains whether the user should buy, wait, or monitor.

The current hackathon build stores history privately in the user's browser and supports manual refreshes. Scheduled cloud checks and external notifications are the next production milestone.

## How we built it

The demo is a lightweight edge application. A server-side endpoint validates and fetches the submitted URL, then reads JSON-LD and Open Graph metadata. NVIDIA Nemotron 3 Super 120B on Nebius Token Factory converts incomplete or inconsistent page data into a normalized product snapshot. The browser maintains a timestamped history and computes price and stock transitions without sending that personal watchlist to a database.

The project is intentionally dependency-light so it is quick to deploy and easy to audit. It is open-sourced under the MIT License.

## Challenges we ran into

Retail pages vary widely: some expose complete schema.org Product data, some use only social metadata, and some render data with JavaScript or block automated requests. We handled this by layering deterministic metadata extraction with a Nemotron fallback and by reporting extraction failures rather than inventing a price.

Another challenge was presenting stock history honestly when the app has only just begun tracking an item. StockSage distinguishes demo history from observations collected in the user's browser and never claims to know events it has not seen.

## Accomplishments that we're proud of

- One-link workflow that joins price tracking and restock intelligence.
- An AI-assisted normalizer that works beyond a single retailer's page format.
- Clear transition logic for restocks, price drops, and target hits.
- A useful demo mode that communicates the product vision without fabricating live data.
- A fast, polished interface that works on desktop and mobile.

## What we learned

The most trustworthy shopping agent is not the one that produces the most confident answer. It is the one that separates observed facts, extracted metadata, AI interpretation, and unknowns. Nemotron is most valuable as a reasoning and normalization layer around deterministic page signals—not as a replacement for them.

## What's next for StockSage

- scheduled cloud checks with durable history;
- browser push, email, Telegram, and WhatsApp alerts;
- cross-store product matching and price comparison;
- coupons, shipping, bank offers, and per-unit cost;
- regional price and currency support;
- restock-probability and sale-window forecasting; and
- official retailer and affiliate feeds for higher reliability.

## Built with

- Nebius Token Factory
- NVIDIA Nemotron 3 Super 120B
- JavaScript
- Cloudflare Workers-compatible edge runtime
- HTML and CSS

## Demo URL

https://stocksage-ai.venz1z.chatgpt.site

## Source code URL

https://github.com/VenkateshR-stack/stocksage-ai

## Demo video URL

Add the public YouTube video URL here after recording and uploading the demo.

## Nebius feedback

Token Factory's OpenAI-compatible interface made it straightforward to place Nemotron behind a small edge endpoint. The most useful improvement for this use case would be clearer model-specific structured-output examples and an easy way to inspect per-request latency and token cost during hackathon development.


