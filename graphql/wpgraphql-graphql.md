# WPGraphQL GraphQL API

Source: https://www.wpgraphql.com/docs/introduction

## Overview

WPGraphQL exposes all WordPress data through a single GraphQL endpoint, typically available at `https://your-site.com/graphql`. The schema is fully introspectable and can be explored using the built-in GraphiQL IDE in the WordPress admin dashboard.

## Endpoint

- **Default endpoint:** `https://your-wordpress-site.com/graphql`
- **Method:** POST (recommended) or GET (for caching via HTTP layer)
- **Content-Type:** `application/json`

## Core Types

### Posts and Pages

```graphql
query GetPosts {
  posts(first: 10) {
    nodes {
      id
      title
      date
      slug
      excerpt
      content
      author {
        node {
          name
        }
      }
      categories {
        nodes {
          name
          slug
        }
      }
      tags {
        nodes {
          name
          slug
        }
      }
      featuredImage {
        node {
          sourceUrl
          altText
        }
      }
    }
  }
}
```

### Users

```graphql
query GetUsers {
  users(first: 10) {
    nodes {
      id
      name
      email
      slug
      roles {
        nodes {
          name
        }
      }
    }
  }
}
```

### Menus

```graphql
query GetMenu {
  menu(id: "primary", idType: LOCATION) {
    menuItems {
      nodes {
        id
        label
        url
        parentId
      }
    }
  }
}
```

### Taxonomies and Terms

```graphql
query GetCategories {
  categories(first: 20) {
    nodes {
      id
      name
      slug
      count
      description
      parent {
        node {
          name
        }
      }
    }
  }
}
```

### Media

```graphql
query GetMediaItems {
  mediaItems(first: 10) {
    nodes {
      id
      title
      sourceUrl
      mimeType
      mediaDetails {
        width
        height
        sizes {
          name
          sourceUrl
          width
          height
        }
      }
    }
  }
}
```

## Mutations

### Create Post

```graphql
mutation CreatePost($input: CreatePostInput!) {
  createPost(input: $input) {
    post {
      id
      title
      status
      slug
    }
  }
}
```

### Update Post

```graphql
mutation UpdatePost($input: UpdatePostInput!) {
  updatePost(input: $input) {
    post {
      id
      title
      modified
    }
  }
}
```

### Delete Post

```graphql
mutation DeletePost($id: ID!) {
  deletePost(input: { id: $id }) {
    deletedId
    post {
      title
    }
  }
}
```

## Pagination

WPGraphQL uses cursor-based pagination for all list connections.

```graphql
query GetPostsWithPagination($after: String) {
  posts(first: 10, after: $after) {
    pageInfo {
      hasNextPage
      hasPreviousPage
      startCursor
      endCursor
    }
    nodes {
      id
      title
      slug
    }
  }
}
```

- **Default limit:** 10 nodes per request
- **Maximum limit:** 100 nodes per request (configurable via `graphql_connection_max_query_amount` filter)

## Authentication

WPGraphQL supports two authentication patterns:

1. **WordPress Nonce:** For requests made within the WordPress admin context
2. **JWT Authentication:** Via the WPGraphQL JWT Authentication plugin (third-party)
3. **Application Passwords:** Native WordPress feature supported for API requests

```
Authorization: Bearer <jwt_token>
```

## Schema Extension

The schema can be extended using PHP filter hooks:

```php
add_action('graphql_register_types', function() {
  register_graphql_field('Post', 'customField', [
    'type' => 'String',
    'resolve' => function($post) {
      return get_post_meta($post->databaseId, 'custom_field', true);
    }
  ]);
});
```

## Notable Extensions

- **WPGraphQL for ACF** — exposes Advanced Custom Fields
- **WPGraphQL for WooCommerce (WooGraphQL)** — adds e-commerce data
- **WPGraphQL Smart Cache** — adds tag-based cache invalidation
- **WPGraphQL JWT Authentication** — adds JWT-based auth
- **WPGraphQL Yoast SEO** — exposes Yoast SEO meta fields
