# WPGraphQL GraphQL API

WPGraphQL is an open-source WordPress plugin that adds a full-featured, extendable GraphQL API to any WordPress installation. It exposes WordPress content — including posts, pages, custom post types, users, comments, taxonomies, menus, media items, plugins, themes, and site settings — as a queryable GraphQL schema with Relay-compliant cursor-based pagination. The plugin ships with a built-in GraphiQL IDE in the WordPress dashboard and a flexible type registration system that allows the schema to be extended by other plugins.

The endpoint is host-specific, determined by each WordPress installation. By default the path is `/graphql` appended to the site's base URL, but this can be changed in the WordPress admin settings.

**Endpoint:** https://example.com/graphql *(host-specific; configurable per installation)*

**Documentation:** https://www.wpgraphql.com/docs/introduction

## Authentication

WPGraphQL supports multiple authentication approaches:

- **WordPress Nonce** — cookie/nonce authentication for requests made within the WordPress admin or from the same origin.
- **JWT Authentication** — stateless token-based auth via the WPGraphQL JWT Authentication extension plugin. Tokens are obtained via a `login` mutation and passed as a Bearer token in the `Authorization` header.
- **Application Passwords** — native WordPress Application Passwords (WordPress 5.6+) passed via HTTP Basic Auth.

Unauthenticated requests receive publicly visible content only. Private posts, draft content, and user email addresses require appropriate WordPress capabilities.

**References:**
- Documentation: https://www.wpgraphql.com/docs/introduction
- GettingStarted: https://www.wpgraphql.com/docs/quick-start
- Authentication: https://www.wpgraphql.com/docs/authentication-and-authorization
- GraphiQL IDE: https://www.wpgraphql.com/docs/using-the-graphiql-ide
- GitHub Source: https://github.com/wp-graphql/wp-graphql
- WordPress Plugin: https://wordpress.org/plugins/wp-graphql/
