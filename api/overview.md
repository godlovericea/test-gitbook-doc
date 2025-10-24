# API Overview

Complete API documentation for Test GitBook platform.

## 📋 Introduction

This section provides comprehensive API documentation for integrating with our platform.

## 🎯 API Basics

### Base URL

```
https://api.example.com/v1
```

### API Versioning

We use URL-based versioning:

- `v1` - Current stable version
- `v2` - Beta features (coming soon)

### Response Format

All API responses are in JSON format:

```json
{
  "status": "success",
  "data": {
    // Response data
  },
  "meta": {
    "timestamp": "2024-10-24T10:30:00Z",
    "version": "v1"
  }
}
```

## 🔐 Authentication

See the [Authentication Guide](authentication.md) for detailed information.

Quick overview:

```bash
# Using API Key
curl -H "Authorization: Bearer YOUR_API_KEY" \
  https://api.example.com/v1/users
```

## 📊 Rate Limiting

| Plan | Requests/Hour | Requests/Day |
|------|--------------|--------------|
| Free | 100 | 1,000 |
| Plus | 1,000 | 10,000 |
| Pro | 10,000 | 100,000 |

### Rate Limit Headers

```http
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1635724800
```

## 🚀 Quick Start

### 1. Get Your API Key

```bash
# Sign up and get your API key
API_KEY="your_api_key_here"
```

### 2. Make Your First Request

```bash
curl -X GET \
  -H "Authorization: Bearer $API_KEY" \
  -H "Content-Type: application/json" \
  https://api.example.com/v1/users/me
```

### 3. Parse Response

```javascript
// JavaScript example
const response = await fetch('https://api.example.com/v1/users/me', {
  headers: {
    'Authorization': 'Bearer YOUR_API_KEY',
    'Content-Type': 'application/json'
  }
});

const data = await response.json();
console.log(data);
```

## 📚 API Endpoints

### Users

```http
GET    /v1/users          # List all users
GET    /v1/users/:id      # Get user by ID
POST   /v1/users          # Create user
PUT    /v1/users/:id      # Update user
DELETE /v1/users/:id      # Delete user
```

### Documents

```http
GET    /v1/documents      # List documents
GET    /v1/documents/:id  # Get document
POST   /v1/documents      # Create document
PUT    /v1/documents/:id  # Update document
DELETE /v1/documents/:id  # Delete document
```

### Search

```http
GET    /v1/search         # Search documents
POST   /v1/search/ai      # AI-powered search
```

## 🔧 Request Examples

### GET Request

```bash
curl -X GET \
  "https://api.example.com/v1/users?page=1&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Response:**

```json
{
  "status": "success",
  "data": [
    {
      "id": "user_123",
      "name": "John Doe",
      "email": "john@example.com"
    }
  ],
  "meta": {
    "page": 1,
    "limit": 10,
    "total": 100
  }
}
```

### POST Request

```bash
curl -X POST \
  "https://api.example.com/v1/users" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Jane Smith",
    "email": "jane@example.com"
  }'
```

**Response:**

```json
{
  "status": "success",
  "data": {
    "id": "user_124",
    "name": "Jane Smith",
    "email": "jane@example.com",
    "created_at": "2024-10-24T10:30:00Z"
  }
}
```

### PUT Request

```bash
curl -X PUT \
  "https://api.example.com/v1/users/user_124" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Jane Doe"
  }'
```

### DELETE Request

```bash
curl -X DELETE \
  "https://api.example.com/v1/users/user_124" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## ⚠️ Error Handling

### Error Response Format

```json
{
  "status": "error",
  "error": {
    "code": "INVALID_REQUEST",
    "message": "Invalid user ID provided",
    "details": {
      "field": "id",
      "reason": "must be a valid UUID"
    }
  }
}
```

### Common Error Codes

| Code | Status | Description |
|------|--------|-------------|
| `UNAUTHORIZED` | 401 | Invalid or missing API key |
| `FORBIDDEN` | 403 | Insufficient permissions |
| `NOT_FOUND` | 404 | Resource not found |
| `RATE_LIMIT_EXCEEDED` | 429 | Too many requests |
| `INTERNAL_ERROR` | 500 | Server error |

## 🌐 SDKs and Libraries

### Official SDKs

```javascript
// JavaScript/TypeScript
npm install @example/api-client

import { ApiClient } from '@example/api-client';

const client = new ApiClient({ apiKey: 'YOUR_API_KEY' });
const users = await client.users.list();
```

```python
# Python
pip install example-api-client

from example import ApiClient

client = ApiClient(api_key='YOUR_API_KEY')
users = client.users.list()
```

```go
// Go
go get github.com/example/api-client-go

import "github.com/example/api-client-go"

client := apiclient.New("YOUR_API_KEY")
users, err := client.Users.List()
```

## 📖 Additional Resources

- [Authentication Guide](authentication.md)
- [Rate Limiting Details](#rate-limiting)
- [Best Practices](#best-practices)
- [Changelog](#changelog)

## 🔔 Webhooks

Subscribe to events:

```json
{
  "url": "https://your-app.com/webhook",
  "events": ["user.created", "user.updated", "user.deleted"]
}
```

## 🧪 Testing

### Sandbox Environment

Use our sandbox for testing:

```
https://sandbox-api.example.com/v1
```

### Test API Keys

Sandbox keys always start with `test_`:

```
test_sk_1234567890abcdef
```

## 📝 Best Practices

1. **Use HTTPS**: Always use HTTPS for API requests
2. **Handle Errors**: Implement proper error handling
3. **Cache Responses**: Cache GET requests when appropriate
4. **Respect Rate Limits**: Implement exponential backoff
5. **Keep Keys Secret**: Never expose API keys in client-side code

---

**Next:** [Authentication Guide](authentication.md) →

