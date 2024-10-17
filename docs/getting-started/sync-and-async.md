---
sidebar_position: 2
---

# Sync and Async Requests

Skidio Labs offers two ways to process text-to-image generation requests: **Sync** and **Async**. Both use the same request body, but differ in how you receive the generated image.

- **Sync**: Receive the image immediately in the response.
- **Async**: Receive a job ID and check the status later or get notified via webhook.

## Request Format

Both sync and async requests use the same JSON format:

```json
{
  "input": {
    "api_key": "your-api-key"
  },
  "prompt": "your-image-prompt"
}
```

## Endpoints

- Sync: `https://skidiolabs.com/api/txt2img`
- Async: `https://skidiolabs.com/api/txt2img/async`

## Example Implementations

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
  <TabItem value="curl" label="cURL" default>

```bash
# Sync
curl -X POST "https://skidiolabs.com/api/txt2img" \
-H "Content-Type: application/json" \
-d '{
  "input": {
    "api_key": "your-api-key"
  },
  "prompt": "your-image-prompt"
}'

# Async
curl -X POST "https://skidiolabs.com/api/txt2img/async" \
-H "Content-Type: application/json" \
-d '{
  "input": {
    "api_key": "your-api-key"
  },
  "prompt": "your-image-prompt"
}'
```

  </TabItem>
  <TabItem value="python" label="Python">

```python
import requests

def make_request(endpoint):
    url = f"https://skidiolabs.com/api/txt2img{endpoint}"
    payload = {
        "input": {
            "api_key": "your-api-key"
        },
        "prompt": "your-image-prompt"
    }
    response = requests.post(url, json=payload)
    return response.json()

# Sync
sync_response = make_request("")

# Async
async_response = make_request("/async")
```

  </TabItem>
  <TabItem value="javascript" label="JavaScript">

```javascript
const makeRequest = async (endpoint) => {
  const url = `https://skidiolabs.com/api/txt2img${endpoint}`;
  const payload = {
    input: {
      api_key: 'your-api-key'
    },
    prompt: 'your-image-prompt'
  };

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(payload)
    });
    return await response.json();
  } catch (error) {
    console.error('Error:', error);
  }
};

// Sync
makeRequest('').then(data => console.log('Sync:', data));

// Async
makeRequest('/async').then(data => console.log('Async:', data));
```

  </TabItem>
  <TabItem value="postman" label="Postman">

1. Create a new request:
   - Method: `POST`
   - URL: `https://skidiolabs.com/api/txt2img` (for sync) or `https://skidiolabs.com/api/txt2img/async` (for async)
2. Go to the "Body" tab, select "raw", and choose "JSON" as the input format.
3. Enter the following JSON:
```json
{
  "input": {
    "api_key": "your-api-key"
  },
  "prompt": "your-image-prompt"
}
```
4. Click "Send" to submit the request.

  </TabItem>
</Tabs>

## Response

- **Sync**: The response contains the generated image.
- **Async**: The response contains a job ID, which you can use to check the status or retrieve the image later.

Remember to handle the responses accordingly based on whether you're using sync or async requests.