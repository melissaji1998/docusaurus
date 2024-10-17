---
sidebar_position: 1
---

# Setting API Key and GET Image

To interact with Skidio Labs' API, you will need your API key and job ID. Follow the steps below to get your API key and use it to fetch the status and image of an async job.

## Step 1: Get your API Key

You can retrieve your API key by navigating to your **Settings** page at [https://skidiolabs.com/settings/api](https://skidiolabs.com/settings/api). This key will be used in all future requests for both sync and async job generations.

## Step 2: Get the Job ID

The **job ID** is returned when you submit an async job request. Save this ID, as it will be needed to check the status and retrieve the result of the job.

## Step 3: Fetch Image using Job ID

To get the image from an async job, use the following request format, providing your `api_key` and the `job_id` you received:

```json
{
  "input": {
    "api_key": "your-api-key",
    "job_id": "job-id-received"
  }
}
```

### Request URL

Make a **GET** request to the following endpoint:
```
https://skidiolabs.com/api/txt2img/status
```

### Example Implementations

You can use various methods to send this request. Below are a few examples:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
  <TabItem value="curl" label="cURL" default>

```bash
curl -X GET "https://skidiolabs.com/api/txt2img/status" \
-H "Content-Type: application/json" \
-d '{
  "input": {
    "api_key": "your-api-key",
    "job_id": "job-id-received"
  }
}'
```

  </TabItem>
  <TabItem value="python" label="Python">

```python
import requests

url = "https://skidiolabs.com/api/txt2img/status"
payload = {
  "input": {
    "api_key": "your-api-key",
    "job_id": "job-id-received"
  }
}

response = requests.get(url, json=payload)
print(response.json())
```

  </TabItem>
  <TabItem value="javascript" label="JavaScript">

```javascript
fetch('https://skidiolabs.com/api/txt2img/status', {
  method: 'GET',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    input: {
      api_key: 'your-api-key',
      job_id: 'job-id-received'
    }
  })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

  </TabItem>
  <TabItem value="postman" label="Postman">

In **Postman**, create a new request:
- **Method**: `GET`
- **URL**: `https://skidiolabs.com/api/txt2img/status`
- Go to the **Body** tab, select `raw`, and choose `JSON` as the input format. Enter the following JSON:
```json
{
  "input": {
    "api_key": "your-api-key",
    "job_id": "job-id-received"
  }
}
```

Click **Send** to retrieve the status of your async job, and download the image if the job is completed.

  </TabItem>
</Tabs>

## Important Note

Your **API key** is a critical part of every request made to Skidio Labs' API. Please ensure you **store it securely** and use it as-is in any future requests, including those for **sync** and **async** generations.
