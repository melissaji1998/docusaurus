---
sidebar_position: 1
---

# Model Usage

This page provides detailed information on how to use our text-to-image generation models. All models use the same input format, with slight variations in parameters depending on the specific model.

## Request Format

Use the following JSON format for your requests:

```json
{
  "input": {
    "api_key": "your-api-key"
  },
  "webhook": "https://your-callback-url/endpoint",
  "model": "model-name",
  "prompt": "your image description",
  "negative_prompt": "elements to avoid in the image",
  "width": 1024,
  "height": 1024,
  "batch_size": 1,
  "steps": 6,
  "seed": 87,
  "guidance_scale": 3.5
}
```

## Available Models

Currently, we offer the following text-to-image models:

1. flux-schnell
2. flux-dev
3. sd3
4. sdxl
5. sdxl-turbo
6. sd1.5
<!-- 7. sd1.5-realdream -->

To use a specific model, simply change the `"model"` parameter in your request.

## Example Usage

Here's an example using the `flux-schnell` model:

```json
{
  "input": {
    "api_key": "your-api-key"
  },
  "webhook": "https://your-callback-url/endpoint",
  "model": "flux-schnell",
  "prompt": "A serene Japanese garden with a koi pond and cherry blossoms",
  "negative_prompt": "people, modern elements, urban scenes",
  "width": 1024,
  "height": 1024,
  "batch_size": 1,
  "steps": 6,
  "seed": 42,
  "guidance_scale": 3.5
}
```

### Example Implementations

Here are example implementations for different languages and tools:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
  <TabItem value="curl" label="cURL" default>

```bash
curl -X POST "https://skidiolabs.com/api/txt2img" \
-H "Content-Type: application/json" \
-d '{
  "input": {
    "api_key": "your-api-key"
  },
  "webhook": "https://your-callback-url/endpoint",
  "model": "flux-schnell",
  "prompt": "A serene Japanese garden with a koi pond and cherry blossoms",
  "negative_prompt": "people, modern elements, urban scenes",
  "width": 1024,
  "height": 1024,
  "batch_size": 1,
  "steps": 6,
  "seed": 42,
  "guidance_scale": 3.5
}'
```

  </TabItem>
  <TabItem value="python" label="Python">

```python
import requests

url = "https://skidiolabs.com/api/txt2img"
payload = {
  "input": {
    "api_key": "your-api-key"
  },
  "webhook": "https://your-callback-url/endpoint",
  "model": "flux-schnell",
  "prompt": "A serene Japanese garden with a koi pond and cherry blossoms",
  "negative_prompt": "people, modern elements, urban scenes",
  "width": 1024,
  "height": 1024,
  "batch_size": 1,
  "steps": 6,
  "seed": 42,
  "guidance_scale": 3.5
}

response = requests.post(url, json=payload)
print(response.json())
```

  </TabItem>
  <TabItem value="javascript" label="JavaScript">

```javascript
fetch('https://skidiolabs.com/api/txt2img', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    input: {
      api_key: 'your-api-key'
    },
    webhook: 'https://your-callback-url/endpoint',
    model: 'flux-schnell',
    prompt: 'A serene Japanese garden with a koi pond and cherry blossoms',
    negative_prompt: 'people, modern elements, urban scenes',
    width: 1024,
    height: 1024,
    batch_size: 1,
    steps: 6,
    seed: 42,
    guidance_scale: 3.5
  })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

  </TabItem>
  <TabItem value="postman" label="Postman">

1. Create a new POST request
2. URL: `https://skidiolabs.com/api/txt2img`
3. Headers: Add `Content-Type: application/json`
4. Body: Select "raw" and choose "JSON", then paste the following:

```json
{
  "input": {
    "api_key": "your-api-key"
  },
  "webhook": "https://your-callback-url/endpoint",
  "model": "flux-schnell",
  "prompt": "A serene Japanese garden with a koi pond and cherry blossoms",
  "negative_prompt": "people, modern elements, urban scenes",
  "width": 1024,
  "height": 1024,
  "batch_size": 1,
  "steps": 6,
  "seed": 42,
  "guidance_scale": 3.5
}
```

5. Click "Send" to make the request

  </TabItem>
</Tabs>

## Sample Prompts

Here are some sample prompts to get you started:

1. "A futuristic cityscape with flying cars and neon lights"
2. "A magical forest with glowing mushrooms and fairy lights"
3. "An underwater scene of a coral reef teeming with colorful fish"
4. "A steampunk-inspired clockwork mechanism with gears and brass"
5. "A cozy cabin in the woods during a snowy winter night"

Feel free to use these prompts or create your own to explore the capabilities of our models.

## Parameter Descriptions

| Parameter | Description |
|-----------|-------------|
| api_key | Your unique API key for authentication (inside the `input` object) |
| webhook | (Optional) URL to receive a callback when the async job is complete |
| model | The name of the text-to-image model to use |
| prompt | A detailed description of the image you want to generate |
| negative_prompt | Elements or styles you want to avoid in the generated image |
| width | The width of the generated image in pixels |
| height | The height of the generated image in pixels |
| batch_size | The number of images to generate in a single request |
| steps | The number of denoising steps (higher values may increase quality but take longer) |
| seed | A number to initialize the random generator (use the same seed to reproduce results) |
| guidance_scale | Controls how closely the image matches the prompt (higher values adhere more strictly) |

## Tips for Effective Prompts

1. Be specific and descriptive in your prompts.
2. Use adjectives to define styles, moods, and details.
3. Specify artistic styles or mediums for unique results (e.g., "oil painting", "digital art", "pencil sketch").
4. Use the negative prompt to exclude unwanted elements or styles.
5. Experiment with different guidance scales to find the right balance between creativity and prompt adherence.

Remember, the quality and specificity of your prompt greatly influence the generated image. Don't hesitate to experiment and refine your prompts to achieve the desired results.

## Model-Specific Notes

- All current models are text-to-image (txt2img) only.
- Different models may have slightly different strengths or specializations. For example:
  - `sdxl-turbo` is optimized for faster generation times.
  <!-- - `sd1.5-realdream` may be particularly good at photorealistic images. -->
  - `flux-schnell` and `flux-dev` are our custom models with unique capabilities.

Experiment with different models to find the one that best suits your specific use case and style preferences.
