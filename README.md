# WPGraphQL

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
