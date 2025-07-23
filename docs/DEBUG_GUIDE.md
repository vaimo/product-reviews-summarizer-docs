# Debug Guide

This guide explains how to use the debug endpoint to inspect and manage review summaries in the Product Reviews Summarizer project. The debug endpoint provides tools to understand the internal state of the summarization process and troubleshoot issues.

## Overview

The debug endpoint (`/api/v1/web/product-reviews-summarizer/debug`) allows you to:

- **List Summaries**: View all stored product review summaries
- **Remove All Summaries**: Clear all stored summaries for troubleshooting or reset
- **Remove a Specific Summary**: Remove a summary for a specific product and store

## Authentication

The debug requests require authentication. You need to generate a Bearer token using the Adobe App Builder OAuth Server and include it in the Authorization header of your debug endpoint requests. Additionally, you must include the `x-gw-ims-org-id` header with your organization ID.

## Available Operations

### 1. Get List of Summaries

Retrieve all stored product review summaries.

#### Example Request

```bash
curl -X POST "https://your-app-builder-endpoint/api/v1/web/product-reviews-summarizer/debug" \
  -H "Content-Type: application/json" \
  -H "x-gw-ims-org-id: YOUR_ORG_ID"
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "data": {
      "type": "get-list"
    }
  }'
```

#### Example Response

```json
{
  "response": {
    "list": [
      ["product-review-summary-es-2631", "{\"product\":{\"id\":2631,\"sku\":\"134795\",\"name\":\"Pastillas para descalcificar\"},\"summary\":{}}"]
    ]
  },
  "type": "list"
}
```

### 2. Remove All Summaries

Clear all stored product review summaries. Useful for resetting the state.

#### Example Request

```bash
curl -X POST "https://your-app-builder-endpoint/api/v1/web/product-reviews-summarizer/debug" \
  -H "Content-Type: application/json" \
  -H "x-gw-ims-org-id: YOUR_ORG_ID"
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "data": {
      "type": "remove-all-summaries"
    }
  }'
```

#### Example Response

```json
{
  "response": {
    "message": "All summaries removed"
  },
  "type": "remove-all-summaries"
}
```

### 3. Remove a Specific Summary

Remove a summary for a specific product and store.

#### Example Request

```bash
curl -X POST "https://your-app-builder-endpoint/api/v1/web/product-reviews-summarizer/debug" \
  -H "Content-Type: application/json" \
  -H "x-gw-ims-org-id: YOUR_ORG_ID"
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "data": {
      "type": "remove-summary",
      "storeCode": "default",
      "productId": "123"
    }
  }'
```

#### Example Response

```json
{
  "response": {
    "message": "Summary removed"
  },
  "type": "remove-summary"
}
```
