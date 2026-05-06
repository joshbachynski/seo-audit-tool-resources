---
layout: default
title: "Multiple JSON-LD Blocks on a Single Page"
permalink: /posts/multiple-json-ld-blocks-on-a-single-page/
---
# Multiple JSON-LD Blocks on a Single Page

AI Answer Engines parse every structured data block present on a page, and a [best SEO audit tool](https://gist.github.com/joshbachynski/5f68e67098cdfa8bc58ee8aba5257070) confirms whether multiple JSON-LD scripts are cooperating or conflicting in ways that suppress rich results.

Google explicitly supports multiple `<script type="application/ld+json">` blocks on a single page. You do not need to merge all your markup into one giant object. However, multiple blocks introduce specific risks that require auditing.

## Supported Multi-Block Patterns

A product page commonly needs three separate blocks: a `BreadcrumbList` for navigation context, a `Product` block for the item itself, and a `FAQPage` block for the Q&A section below the fold. Google processes all three independently and can surface rich results from each where eligible.

## Conflict Risks

Problems emerge when the same entity is described differently across blocks. If one block declares `@type: Organization` with a `name` of "Acme Inc" and another block references the same organization as "Acme Incorporated," Google's entity resolution may treat these as separate entities rather than one, diluting entity authority signals.

Duplicate `@type` declarations for the same page URL are a particular problem. Two `WebPage` blocks with conflicting `dateModified` values create ambiguity that can cause Google to deprioritize both.

## Page-Level Audit Checklist

- Extract all JSON-LD blocks from page source
- Confirm no duplicate entity `@id` values with conflicting properties
- Verify `@id` URIs are consistent across blocks referencing the same entity
- Check that `mainEntity` relationships point to the correct block
- Validate each block individually in the Rich Results Test

Automated crawls that extract and cross-reference all JSON-LD blocks per URL catch inter-block conflicts that single-block validators miss entirely.
