# Debug Guide

This guide explains how to use the debug endpoint to inspect and manage review summaries in the Product Reviews Summarizer project. The debug endpoint provides tools to understand the internal state of the summarization process and troubleshoot issues.

## Overview

The debug endpoint (`/api/v1/web/debug-internal/consumer`) allows you to:

- **List Summaries**: View all stored product review summaries
- **Remove All Summaries**: Clear all stored summaries for troubleshooting or reset
- **Remove a Specific Summary**: Remove a summary for a specific product and store

## Authentication

All debug requests may require authentication depending on your deployment. Include any required authentication headers when making requests to the debug endpoint.

## Available Operations

### 1. Get List of Summaries

Retrieve all stored product review summaries.

#### Example Request

```bash
curl -X POST "https://your-app-builder-endpoint/api/v1/web/debug-internal/consumer" \
  -H "Content-Type: application/json" \
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
  "status": "success",
  "message": "list",
  "data": {
    "list": [
      {
        "storeCode": "default",
        "productId": "123",
        "summary": "Great product!"
      },
      {
        "storeCode": "german_store_view",
        "productId": "456",
        "summary": "Sehr gut!"
      }
    ]
  }
}
```

### 2. Remove All Summaries

Clear all stored product review summaries. Useful for resetting the state.

#### Example Request

```bash
curl -X POST "https://your-app-builder-endpoint/api/v1/web/debug-internal/consumer" \
  -H "Content-Type: application/json" \
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
  "status": "success",
  "message": "all-summaries",
  "data": {
    "message": "All summaries removed"
  }
}
```

### 3. Remove a Specific Summary

Remove a summary for a specific product and store.

#### Example Request

```bash
curl -X POST "https://your-app-builder-endpoint/api/v1/web/debug-internal/consumer" \
  -H "Content-Type: application/json" \
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
  "status": "success",
  "message": "summary",
  "data": {
    "message": "Summary removed"
  }
}
```
