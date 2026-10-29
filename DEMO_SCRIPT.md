# StockSage AI — demo script

Target length: 2 minutes 20 seconds. Maximum allowed: 3 minutes.

## 0:00–0:15 — Problem

"Price trackers tell us when a product gets cheaper. Restock tools tell us when it returns. But shoppers need both—and they need to know what happened before. This is StockSage AI."

Show the dashboard hero and the live-demo badge.

## 0:15–0:40 — The one-link workflow

"I can paste a product link from Amazon, Flipkart, Nykaa, or another public retailer. StockSage fetches the page, extracts product metadata, and uses NVIDIA Nemotron through Nebius Token Factory to normalize unclear page information."

Paste a public test URL, choose **Track product**, and point out the resulting product card. If the retailer blocks the request, use the built-in sample data and say that the app reports blocked extraction rather than fabricating a result.

## 0:40–1:10 — Price intelligence

Open the Sony card.

"StockSage records each observation in a private browser history. It shows the current price, the target, the recent trend, and a SageSignal that turns the numbers into a simple buy-or-wait explanation."

Point to the price chart, target-price control, and price-drop alert.

## 1:10–1:40 — Restock intelligence

Open the Dyson card.

"The important difference is stock memory. This item is out of stock, and StockSage remembers when it was last seen available. When a later check changes from out of stock to in stock, it creates a restock alert. This enables messages such as: back in stock now, or last observed in stock two days ago."

Point to the stock badge, history, and notification feed.

## 1:40–2:05 — Architecture

"Under the hood, the edge endpoint first reads structured JSON-LD and Open Graph fields. Nemotron 3 Super 120B on Token Factory handles inconsistent or incomplete pages and returns a normalized snapshot. The browser then computes price and stock transitions. We keep uncertainty visible and never invent a price."

Briefly show the architecture section in the README or the on-screen AI status.

## 2:05–2:20 — Close

"Next we will add scheduled cloud checks, durable history, cross-store matching, and push, email, Telegram, and WhatsApp delivery. StockSage: paste any product link, know when to buy—and when it comes back."

End on the dashboard with the project name and public URL visible.

## Recording checklist

- Record at 1080p with browser zoom near 100%.
- Keep the final video under 3:00.
- Do not display API keys, browser passwords, email, or private tabs.
- Upload to YouTube as **Public** or **Unlisted** and verify it opens in a signed-out window.
- Use title: `StockSage AI — Nebius × NVIDIA Global AI Hackathon Demo`.


