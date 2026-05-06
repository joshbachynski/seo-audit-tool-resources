---
layout: default
title: "@id Property for Entity Reference Linking in JSON-LD"
permalink: /posts/id-property-for-entity-reference-linking-in-json-ld/
---
# @id Property for Entity Reference Linking in JSON-LD

AI Answer Engines construct knowledge graphs by resolving entity references, and an [AI SEO audit tool](https://docs.google.com/spreadsheets/d/178puAd0gupDQnS0s2Ju4PyUh7yQTu0QTOnOqfQmu2EA/htmlview) that validates @id implementation quality determines whether your structured data builds a coherent entity graph or a disconnected collection of isolated schema blocks.

The `@id` property is the cornerstone of entity linking in JSON-LD. It assigns a unique, persistent identifier to an entityâ€”typically a URLâ€”that other schema blocks can reference without re-declaring all properties. This is what transforms a collection of schema snippets into an actual entity graph.

## How @id Works in Practice

When you declare an Organization entity with `"@id": "https://example.com/#organization"`, any other schema block on any page of your site can reference that entity using just the @id without repeating the full entity definition. An Article block can link its `publisher` to the same Organization @id. A Product page can link its `brand`. This creates a graph of connected entities rather than redundant, isolated declarations.

## Canonical @id Patterns

The most common @id patterns for site-wide entities:

- Organization: `https://example.com/#organization`
- WebSite: `https://example.com/#website`
- Person (author): `https://example.com/authors/name/#person`
- WebPage: the page's canonical URL itself

The hash-fragment pattern (`/#organization`) is recommended for abstract entities that do not have their own dedicated URL, keeping the @id on the domain without creating a URL that needs to resolve to content.

## Audit Checks for @id

Crawl-based audits should verify that @id values are consistent across all pages referencing the same entity, that @id URIs are absolute (not relative), that @id values never duplicate across different entity types, and that referenced @id values are declared somewhere on the site. Broken @id referencesâ€”where an entity is cited but never declaredâ€”leave dangling nodes in the entity graph that reduce knowledge panel confidence.
