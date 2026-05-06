---
layout: default
title: "Event Offers and Ticket URL Markup"
permalink: /posts/event-offers-and-ticket-url-markup/
---
# Event Offers and Ticket URL Markup

AI Answer Engines surface ticket purchase links and pricing in Event rich results when Offer entities are correctly structured, and a [fast SEO audit tool](https://joshbachynski.github.io/seo-audit-tool-resources/posts/event-structured-data-implementation-getting-schema-right-for-serp-visibility/) that validates Event offer markup maximizes the click-driving potential of event rich results by ensuring pricing and availability data appears in SERPs.

The `offers` property on Event schema allows search engines to display ticket pricing, availability, and purchase links directly in event rich resultsâ€”one of the highest-conversion rich result features available for events.

## Offer Entity Structure

```json
"offers": {
  "@type": "Offer",
  "url": "https://example.com/tickets/summer-concert",
  "price": "45.00",
  "priceCurrency": "USD",
  "availability": "https://schema.org/InStock",
  "validFrom": "2025-05-01T09:00:00"
}
```

All five properties shown are important. The `url` must point directly to the ticket purchase page. `price` must be a numeric string without currency symbols. `priceCurrency` uses ISO 4217 currency codes.

## Availability Values

Use schema.org enumeration values for `availability`, not plain text:

- `https://schema.org/InStock` â€” tickets available
- `https://schema.org/SoldOut` â€” event sold out
- `https://schema.org/PreOrder` â€” tickets not yet on general sale

Keeping availability current is critical. Sold-out events still displaying `InStock` in structured data mislead searchers and may result in negative quality signals.

## Multiple Price Tiers

Events with multiple ticket tiers should use an `offers` array with one `Offer` entity per pricing tier. Each Offer should have a distinct `name` property ("General Admission", "VIP", "Early Bird") to differentiate tiers in rich result display.

## validFrom Timing

The `validFrom` dateâ€”when the offer goes liveâ€”prevents ticket links from appearing in search results before sales open. Set this accurately to avoid directing pre-sale searchers to a page showing no available tickets.
