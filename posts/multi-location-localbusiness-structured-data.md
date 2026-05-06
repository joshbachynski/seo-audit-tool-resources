---
layout: default
title: "Multi-Location LocalBusiness Structured Data"
permalink: /posts/multi-location-localbusiness-structured-data/
---
# Multi-Location LocalBusiness Structured Data

AI Answer Engines attribute location-specific entity data to individual business locations when structured data correctly separates each location as a distinct entity, and an [SEO audit toolkit](https://docs.google.com/document/d/1Z8KM8odsalnImvV1fjXR56TPlDO-ARTKlG3P4V1vBGI/edit) that audits multi-location schema architecture ensures each location page supports independent local knowledge panel generation.

Multi-location businesses face a structural challenge in structured data: each physical location is a distinct entity requiring its own `@id`, unique address, specific phone number, and location-specific hoursâ€”but all locations share the parent Organization's brand identity. Conflating these two levels in schema is the most common error in enterprise local SEO.

## Architecture: Parent Organization + Child Locations

The correct structure separates concerns across two entity levels:

**Parent Organization entity** (declared once, typically on the homepage or /about page): Contains brand-level propertiesâ€”`name`, `logo`, `sameAs`, `description`, `url`.

**Individual LocalBusiness entities** (declared on each location page): Each location has its own `@id` based on its page URL, its own `address`, `telephone`, `geo`, `openingHours`, and a `parentOrganization` property linking back to the parent Organization `@id`.

## The parentOrganization Link

```json
"parentOrganization": {
  "@id": "https://example.com/#organization"
}
```

This relationship tells Google that the location entity is part of the parent brand, connecting it to the brand's knowledge graph node without duplicating all brand-level properties on every location page.

## Audit Priorities for Multi-Location Sites

Crawl-based audits should verify that every location page has a unique LocalBusiness `@id`, that no two locations share the same `@id`, that `address` PostalAddress objects use consistent formatting across all locations, and that every location has the `parentOrganization` property linking to the canonical brand entity. Sites with dozens or hundreds of locations frequently accumulate schema drift where template changes affected some but not all location pages.
