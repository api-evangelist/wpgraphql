# WPGraphQL Rate Limits

Source: https://www.wpgraphql.com/docs/known-limitations | https://www.wpgraphql.com/docs/performance | https://www.devtwins.com/blog/wpgraphql-increase-post-limit

## Overview

WPGraphQL itself does not impose hard API rate limits. Rate limiting behavior depends on the underlying WordPress hosting environment and any additional plugins or infrastructure layers (CDN, reverse proxy) configured by the site operator.

## Built-In Query Limits

### Connection Pagination Limit

WPGraphQL enforces a maximum number of nodes returned per connection to protect server resources:

| Setting | Default Value | Notes |
|---------|--------------|-------|
| Max nodes per request | 100 | Applies to all list connections (posts, users, terms, etc.) |
| Default page size | 10 | Used when `first`/`last` argument is not specified |

To increase the limit beyond 100 (not recommended for production), use the PHP filter:

```php
add_filter('graphql_connection_max_query_amount', function($amount, $source, $args, $context, $info) {
  return 200; // increase with caution
}, 10, 5);
```

**Warning:** Increasing this limit can significantly impact server performance and memory usage.

### Query Depth and Complexity

WPGraphQL does not enforce query depth limits or complexity scoring by default. These controls can be added via:

- **WPGraphQL Smart Cache** — adds operation complexity awareness and caching
- **Stellate** — GraphQL CDN proxy with configurable complexity-based rate limiting
- Custom PHP middleware registered via `graphql_request_data` hooks

## Hosting-Level Rate Limits

Rate limiting in headless WordPress setups is typically enforced at the hosting layer:

### Common HTTP Rate Limit Triggers

| Scenario | Typical Limit | Response Code |
|----------|--------------|---------------|
| Shared hosting requests | 300–600 req/min | HTTP 429 |
| Managed WP (Kinsta, WP Engine) | Varies by plan | HTTP 429 |
| Cloudflare (free tier) | 100,000 req/day | HTTP 429 |
| WP Engine (Basic) | Configurable | HTTP 429 |

### Mitigation Strategies

1. **Use GET requests** for read-only queries to enable HTTP-layer caching (Cloudflare, Varnish, etc.) and avoid hitting origin rate limits
2. **WPGraphQL Smart Cache** — tag-based caching that invalidates when WordPress content changes; requires host support for tag-based purging
3. **Persisted Queries** — hash queries on the client to reduce payload size and enable GET-based caching
4. **Object Caching** — enable Redis or Memcached on the WordPress host to speed up resolver performance
5. **CDN Caching** — proxy GraphQL GET requests through Cloudflare or a reverse proxy

## Performance Characteristics

- WPGraphQL is designed to be performant but is bounded by WordPress PHP execution time and database query limits
- Complex queries with deep nested connections can trigger N+1 query problems; WPGraphQL uses a data-loader pattern to batch related queries
- PHP `max_execution_time` (default 30s) and `memory_limit` (default 128MB) are the practical hard limits on any single request

## Recommendations

- Keep `first`/`last` values at or below 50 for production use
- Enable an object cache plugin (Redis Object Cache) on the WordPress host
- Use WPGraphQL Smart Cache with a compatible host for automated cache invalidation
- Monitor slow queries using the `graphql_log_query_time` filter or Query Monitor plugin
- For public read-only APIs, configure Cloudflare or a CDN to cache GraphQL GET requests
