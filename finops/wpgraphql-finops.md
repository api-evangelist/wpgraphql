# WPGraphQL FinOps

Source: https://www.wpgraphql.com/ | https://opencollective.com/wp-graphql | https://wordpress.org/plugins/wp-graphql/

## Cost Structure

WPGraphQL is a free, open-source plugin with zero licensing cost. All costs in a WPGraphQL deployment are infrastructure costs associated with running WordPress.

### Direct Plugin Cost

| Component | Cost |
|-----------|------|
| WPGraphQL core plugin | $0 (GPL open source) |
| WPGraphQL Smart Cache | $0 (GPL open source) |
| WPGraphQL for ACF | $0 (GPL open source) |
| WPGraphQL IDE | $0 (GPL open source) |

## Infrastructure Cost Drivers

### WordPress Hosting

Hosting costs are the primary cost center for WPGraphQL deployments. Headless WordPress setups typically require more capable hosting than traditional WordPress sites.

| Hosting Type | Monthly Cost Range | GraphQL Suitability |
|-------------|-------------------|---------------------|
| Shared hosting (Bluehost, SiteGround) | $3–$30 | Low — PHP concurrency limits cause bottlenecks |
| Managed WordPress (WP Engine Basic) | $25–$60 | Medium — good for moderate traffic |
| Managed WordPress (WP Engine Growth) | $115–$290 | High — includes Smart Cache support |
| Managed WordPress (Kinsta Business) | $115–$575 | High — Redis included, good GraphQL performance |
| Pantheon Performance | $175–$700 | High — full page caching, object caching |
| Self-hosted VPS (DigitalOcean, Linode) | $6–$100 | Variable — requires configuration effort |

### Headless Frontend Hosting

Headless WordPress architectures pair WPGraphQL with a separate frontend. Frontend hosting costs are separate:

| Platform | Monthly Cost Range |
|----------|--------------------|
| Vercel (Pro) | $20+/month |
| Netlify (Pro) | $19+/month |
| Cloudflare Pages | $0–$20/month |
| Self-hosted (VPS) | $6–$50/month |

### CDN and Caching

Caching GraphQL responses reduces origin server load and hosting costs significantly:

| Solution | Cost | Benefit |
|----------|------|---------|
| Cloudflare Free | $0 | Basic HTTP caching for GET requests |
| Cloudflare Pro | $20/month | Advanced caching rules and analytics |
| Stellate (GraphQL CDN) | $0–$249+/month | Tag-based GraphQL caching, rate limiting |
| WP Engine EverCache | Included with plan | Tag-based caching with WPGraphQL Smart Cache |

## Cost Optimization Strategies

### Query Optimization

- Use pagination with small page sizes (`first: 10`) to reduce PHP memory and database load per request
- Enable persisted queries to reduce payload size and allow GET-based caching
- Avoid querying unused fields — GraphQL's selective fetching reduces data transfer costs

### Caching

- **WPGraphQL Smart Cache** (free) reduces origin hits by 80–95% when used with a compatible host
- Tag-based cache invalidation ensures fresh content without over-fetching
- Redis Object Cache reduces database query load, lowering PHP execution time and server costs

### Hosting Selection

- For small to medium sites: Managed WordPress plans ($25–$60/month) with Redis included offer the best cost/performance ratio
- For high-traffic headless sites: VPS with Nginx, PHP-FPM, and Redis provides the most cost-effective at scale
- Avoid shared hosting for GraphQL-heavy workloads — concurrency limits cause timeouts that increase operational burden

## Open Source Contribution Cost

WPGraphQL is community-funded through Open Collective. Organizations relying on WPGraphQL commercially are encouraged to contribute:

- **Open Collective:** https://opencollective.com/wp-graphql
- **Backer tiers:** From $5/month (individual) to custom corporate sponsorship
- Primary maintainer Jason Bahl is employed by Automattic, providing long-term project stability

## Total Cost of Ownership Example

### Small Headless Blog (< 10k monthly visitors)

| Component | Monthly Cost |
|-----------|-------------|
| WPGraphQL plugin | $0 |
| Shared/managed WP hosting | $10–$30 |
| Vercel (Hobby/Pro) | $0–$20 |
| Cloudflare (Free) | $0 |
| **Total** | **$10–$50/month** |

### Medium Headless Site (50k–200k monthly visitors)

| Component | Monthly Cost |
|-----------|-------------|
| WPGraphQL plugin | $0 |
| Managed WP (WP Engine Growth) | $115–$290 |
| Vercel Pro | $20+ |
| Cloudflare Pro | $20 |
| **Total** | **$155–$330/month** |

### High-Traffic Headless Platform (1M+ monthly visitors)

| Component | Monthly Cost |
|-----------|-------------|
| WPGraphQL plugin | $0 |
| Managed WP (Enterprise) or VPS cluster | $500–$2,000+ |
| Stellate GraphQL CDN | $249+ |
| Vercel Enterprise or custom CDN | $500+ |
| **Total** | **$1,249–$2,500+/month** |
