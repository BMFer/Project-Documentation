# API Reference

## Overview

This document provides a complete reference for the [Project Name] API.

## Base URL

```
https://api.example.com/v1
```

## Authentication

### API Key Authentication

Include your API key in the request header:

```http
Authorization: Bearer YOUR_API_KEY
```

## Endpoints

### Resource 1

#### GET /resource1

Retrieve a list of resources.

**Request:**

```http
GET /resource1
```

**Parameters:**

| Parameter | Type   | Required | Description           |
|-----------|--------|----------|-----------------------|
| `limit`   | number | No       | Number of items (default: 10) |
| `offset`  | number | No       | Pagination offset (default: 0) |

**Response:**

```json
{
  "data": [
    {
      "id": "123",
      "name": "Example",
      "created_at": "2025-01-01T00:00:00Z"
    }
  ],
  "meta": {
    "total": 100,
    "limit": 10,
    "offset": 0
  }
}
```

**Status Codes:**

- `200 OK` - Success
- `400 Bad Request` - Invalid parameters
- `401 Unauthorized` - Missing or invalid authentication
- `500 Internal Server Error` - Server error

#### POST /resource1

Create a new resource.

**Request:**

```http
POST /resource1
Content-Type: application/json
```

```json
{
  "name": "New Resource",
  "description": "Resource description"
}
```

**Response:**

```json
{
  "id": "124",
  "name": "New Resource",
  "description": "Resource description",
  "created_at": "2025-01-01T00:00:00Z"
}
```

#### GET /resource1/{id}

Retrieve a specific resource by ID.

**Request:**

```http
GET /resource1/123
```

**Response:**

```json
{
  "id": "123",
  "name": "Example",
  "description": "Description",
  "created_at": "2025-01-01T00:00:00Z",
  "updated_at": "2025-01-01T00:00:00Z"
}
```

#### PUT /resource1/{id}

Update an existing resource.

**Request:**

```http
PUT /resource1/123
Content-Type: application/json
```

```json
{
  "name": "Updated Name",
  "description": "Updated description"
}
```

#### DELETE /resource1/{id}

Delete a resource.

**Request:**

```http
DELETE /resource1/123
```

**Response:**

```json
{
  "message": "Resource deleted successfully"
}
```

## Error Handling

All error responses follow this format:

```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable error message",
    "details": {}
  }
}
```

## Rate Limiting

- **Rate Limit**: 1000 requests per hour
- **Headers**:
  - `X-RateLimit-Limit`: Total requests allowed
  - `X-RateLimit-Remaining`: Remaining requests
  - `X-RateLimit-Reset`: Unix timestamp when limit resets

## Webhooks

Configure webhooks to receive real-time notifications.

**Webhook Payload:**

```json
{
  "event": "resource.created",
  "data": {
    "id": "123",
    "name": "Example"
  },
  "timestamp": "2025-01-01T00:00:00Z"
}
```

## Code Examples

### cURL

```bash
curl -X GET "https://api.example.com/v1/resource1" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### JavaScript

```javascript
const response = await fetch('https://api.example.com/v1/resource1', {
  headers: {
    'Authorization': 'Bearer YOUR_API_KEY'
  }
});
const data = await response.json();
```

### Python

```python
import requests

headers = {'Authorization': 'Bearer YOUR_API_KEY'}
response = requests.get('https://api.example.com/v1/resource1', headers=headers)
data = response.json()
```
