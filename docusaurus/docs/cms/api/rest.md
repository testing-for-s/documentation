---
title: REST API reference
description: >-
  Interact with your Content-Types using the REST API endpoints Strapi generates
  for you.
displayed_sidebar: cmsSidebar
sidebar_label: APIs Introduction
pagination_prev: cms/setup-deployment
pagination_next: cms/api/document
tags:
  - API
  - Content API
  - documentId
  - Documents
  - plural API ID
  - REST API
  - singular API ID
---

# REST API

Strapi's REST API allows you to interact with your content through HTTP requests. You can use the REST API to query, create, update and delete content in your Strapi application.

## Endpoints

The REST API endpoints are automatically generated based on your content types. The base URL for API calls is:

```
http://localhost:1337/api
```

For a content type named "articles", the endpoints would be:

- `GET /api/articles`: List articles
- `POST /api/articles`: Create a new article  
- `GET /api/articles/:id`: Get a specific article
- `PUT /api/articles/:id`: Update an article
- `DELETE /api/articles/:id`: Delete an article

## Authentication

Most API endpoints require authentication. You can authenticate requests by including an API token in the `Authorization` header:

```
Authorization: Bearer YOUR_API_TOKEN
```

API tokens can be generated in the Strapi admin panel under Settings > API Tokens.

## Request format

For POST and PUT requests, the request body should be in JSON format:

```json
{
  "data": {
    "title": "My Article Title",
    "content": "The article content..."
  }
}
```

## Response format  

API responses are returned in JSON format. Successful responses have the following structure:

```json
{
  "data": {
    "id": 1,
    "attributes": {
      "title": "Article title",
      "content": "Article content",
      "createdAt": "2023-06-14T12:00:00.000Z",
      "updatedAt": "2023-06-14T12:00:00.000Z"
    }
  },
  "meta": {}
}
```

## Querying and filtering

The REST API supports various query parameters for filtering, sorting, and pagination:

- `filters`: Filter records
- `sort`: Sort records
- `pagination[page]`: Paginate results 
- `fields`: Select specific fields
- `populate`: Populate relations

For example:

```
GET /api/articles?sort=title:asc&pagination[page]=2&pagination[pageSize]=10
```

## Error handling

Errors are returned with appropriate HTTP status codes and error messages:

```json
{
  "data": null,
  "error": {
    "status": 400,
    "name": "ValidationError", 
    "message": "title is a required field",
    "details": {}
  }
}
```

## Additional resources

- [REST API reference](/cms/api/rest) - Full documentation of REST API features
- [GraphQL API](/cms/api/graphql) - Query your content using GraphQL
- [Strapi Client](/cms/api/client) - JavaScript client library for the Strapi API
