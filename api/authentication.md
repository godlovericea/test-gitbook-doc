# Authentication

Learn how to authenticate with the API.

## 🔐 Overview

Our API uses API keys for authentication. All API requests must include your API key in the `Authorization` header.

## 🔑 Getting Your API Key

### Step 1: Sign Up

1. Create an account at https://example.com/signup
2. Verify your email address
3. Log in to your dashboard

### Step 2: Generate API Key

1. Go to Settings → API Keys
2. Click "Generate New API Key"
3. Save your API key securely (it's shown only once)

{% hint style="warning" %}
**Important**: Never share your API key or commit it to version control. Store it securely as an environment variable.
{% endhint %}

## 🚀 Using API Keys

### Header Format

```http
Authorization: Bearer YOUR_API_KEY
```

### Example Request

```bash
curl -X GET \
  -H "Authorization: Bearer sk_live_1234567890abcdef" \
  -H "Content-Type: application/json" \
  https://api.example.com/v1/users/me
```

### Language-Specific Examples

#### JavaScript/Node.js

```javascript
const fetch = require('node-fetch');

const API_KEY = process.env.API_KEY;

async function getUser() {
  const response = await fetch('https://api.example.com/v1/users/me', {
    method: 'GET',
    headers: {
      'Authorization': `Bearer ${API_KEY}`,
      'Content-Type': 'application/json'
    }
  });
  
  const data = await response.json();
  return data;
}
```

#### Python

```python
import requests
import os

API_KEY = os.environ.get('API_KEY')

def get_user():
    headers = {
        'Authorization': f'Bearer {API_KEY}',
        'Content-Type': 'application/json'
    }
    
    response = requests.get(
        'https://api.example.com/v1/users/me',
        headers=headers
    )
    
    return response.json()
```

#### Go

```go
package main

import (
    "fmt"
    "net/http"
    "os"
)

func getUser() error {
    apiKey := os.Getenv("API_KEY")
    
    req, err := http.NewRequest("GET", "https://api.example.com/v1/users/me", nil)
    if err != nil {
        return err
    }
    
    req.Header.Set("Authorization", fmt.Sprintf("Bearer %s", apiKey))
    req.Header.Set("Content-Type", "application/json")
    
    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        return err
    }
    defer resp.Body.Close()
    
    return nil
}
```

## 🔒 API Key Types

### Test Keys

```
test_sk_1234567890abcdef
```

- Used in sandbox environment
- No real data or charges
- Perfect for development

### Live Keys

```
sk_live_1234567890abcdef
```

- Used in production
- Real data and operations
- Keep these secure!

## 🛡️ Security Best Practices

### 1. Environment Variables

{% hint style="success" %}
**Best Practice**: Store API keys in environment variables, not in code.
{% endhint %}

```bash
# .env file
API_KEY=sk_live_1234567890abcdef
API_URL=https://api.example.com/v1
```

**Never commit .env files:**

```bash
# .gitignore
.env
.env.local
*.key
```

### 2. Key Rotation

Rotate your API keys regularly:

1. Generate a new API key
2. Update your applications
3. Delete the old key
4. Verify everything works

### 3. Scope and Permissions

Create keys with minimal required permissions:

```json
{
  "key_name": "production-app",
  "permissions": ["read:users", "write:documents"],
  "expires_at": "2025-01-01T00:00:00Z"
}
```

### 4. IP Whitelisting

Restrict API keys to specific IPs:

```json
{
  "key_id": "key_123",
  "allowed_ips": [
    "203.0.113.1",
    "203.0.113.2"
  ]
}
```

## ⚠️ Authentication Errors

### 401 Unauthorized

**Problem**: Invalid or missing API key

```json
{
  "status": "error",
  "error": {
    "code": "UNAUTHORIZED",
    "message": "Invalid API key"
  }
}
```

**Solutions**:
- Check if API key is included in headers
- Verify the API key is correct
- Ensure the key hasn't expired

### 403 Forbidden

**Problem**: Valid key but insufficient permissions

```json
{
  "status": "error",
  "error": {
    "code": "FORBIDDEN",
    "message": "Insufficient permissions to access this resource"
  }
}
```

**Solutions**:
- Check key permissions
- Upgrade your plan
- Request additional permissions

## 🔄 OAuth 2.0 (Coming Soon)

We're working on OAuth 2.0 support for third-party integrations:

```
# Authorization endpoint
GET https://auth.example.com/oauth/authorize

# Token endpoint
POST https://auth.example.com/oauth/token

# Supported flows
- Authorization Code
- Client Credentials
```

## 🧪 Testing Authentication

### Test Your API Key

```bash
# Quick test
curl -X GET \
  -H "Authorization: Bearer YOUR_API_KEY" \
  https://api.example.com/v1/auth/verify
```

**Success Response:**

```json
{
  "status": "success",
  "data": {
    "valid": true,
    "key_id": "key_123",
    "permissions": ["read:users", "write:documents"],
    "expires_at": "2025-01-01T00:00:00Z"
  }
}
```

### Verify Permissions

```bash
curl -X GET \
  -H "Authorization: Bearer YOUR_API_KEY" \
  https://api.example.com/v1/auth/permissions
```

## 📊 Monitoring

### Track API Key Usage

View usage in your dashboard:

- Total requests
- Requests by endpoint
- Error rates
- Rate limit status

### Set Up Alerts

Configure alerts for:
- Unusual activity
- Rate limit approaching
- Authentication failures
- Key expiration

## 🔧 Advanced Configuration

### Using Multiple Keys

```javascript
// Different keys for different services
const KEYS = {
  user_service: process.env.USER_SERVICE_KEY,
  document_service: process.env.DOCUMENT_SERVICE_KEY,
  search_service: process.env.SEARCH_SERVICE_KEY
};

function getApiKey(service) {
  return KEYS[service];
}
```

### Automatic Key Rotation

```javascript
// Implement automatic key rotation
class ApiKeyManager {
  constructor() {
    this.primaryKey = process.env.PRIMARY_API_KEY;
    this.secondaryKey = process.env.SECONDARY_API_KEY;
  }
  
  async rotateKeys() {
    // Generate new key
    const newKey = await this.generateNewKey();
    
    // Switch to secondary
    this.primaryKey = this.secondaryKey;
    this.secondaryKey = newKey;
    
    // Update configuration
    await this.updateConfig();
  }
  
  getCurrentKey() {
    return this.primaryKey;
  }
}
```

## 📚 Related Resources

- [API Overview](overview.md)
- [Rate Limiting](#)
- [Error Handling](#)
- [Best Practices](#)

## 🆘 Need Help?

If you're having authentication issues:

1. Check our [Troubleshooting Guide](../guides/troubleshooting.md)
2. Contact support@example.com
3. Join our [Discord Community](https://discord.gg/example)

---

**Next:** [API Endpoints](overview.md#api-endpoints) →

