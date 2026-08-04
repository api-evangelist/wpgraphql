# WPGraphQL

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Open-source WordPress plugin that exposes a full-featured extendable GraphQL API for WordPress data including posts, pages, users, menus, taxonomies, media, and plugins.

- **Website:** https://www.wpgraphql.com/
- **Documentation:** https://www.wpgraphql.com/docs/introduction
- **GitHub:** https://github.com/wp-graphql/wp-graphql
- **WordPress.org:** https://wordpress.org/plugins/wp-graphql/
- **Open Collective:** https://opencollective.com/wp-graphql

## Overview

WPGraphQL transforms any WordPress site into a headless CMS by providing a full GraphQL API for all WordPress core data types. Created by Jason Bahl and backed by Automattic as a Canonical Plugin, WPGraphQL enables developers to build decoupled frontends using modern frameworks like Next.js, Svelte, Astro, and SvelteKit while content creators continue using the WordPress admin they know.

The plugin ships with a GraphiQL IDE directly in the WordPress dashboard, making it easy to explore the schema and test queries without additional tooling.

## Key Features

- Full GraphQL API for posts, pages, custom post types, users, menus, taxonomies, and media
- Built-in GraphiQL IDE in the WordPress admin dashboard
- Cursor-based pagination with up to 100 nodes per request
- Extendable schema via PHP hooks (`register_graphql_field`, `register_graphql_connection`)
- Authentication via WordPress nonces, application passwords, or JWT (via extension)
- WPGraphQL Smart Cache for tag-based cache invalidation
- Support for WooCommerce, Advanced Custom Fields, Yoast SEO, and many other plugins via extensions
- Free and open source (GPL v2 or later)

## Repository Contents

- `apis.yml` — APIs.json 0.19 catalog entry for WPGraphQL
- `graphql/wpgraphql-graphql.md` — GraphQL schema overview, example queries and mutations
- `plans/wpgraphql-plans.md` — Pricing and plan information (free/open source)
- `rate-limits/wpgraphql-rate-limits.md` — Rate limiting behavior and mitigation strategies
- `finops/wpgraphql-finops.md` — Infrastructure cost analysis and total cost of ownership

## Maintainer

Kin Lane (kin@apievangelist.com) — [API Evangelist](https://apievangelist.com)
