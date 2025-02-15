# OpenAI, Anthropic & Beyond - API Limits & Compatibility
## The missing OpenAI API Model Parameters Reference
Since OpenAI won't just be normal and give us this, put together a quick reference for my own use that perhaps other can benefit from. This table represents the the max current context window length, max input token and max output token limits for OpenAI via API. This does not apply to ChatGPT through the UI.

This table provides a quick reference to the key parameters of OpenAI's available API-driven models.

| Model         | Context Window | Max Output Tokens | Supports Temperature? | Supports Streaming? |
|--------------|---------------|-------------------|----------------------|---------------------|
| **GPT-4o**   | 128k tokens   | 16k tokens       | ✅ Yes               | ✅ Yes              |
| **GPT-4o-mini** | 128k tokens | 16k tokens       | ✅ Yes               | ✅ Yes              |
| **GPT-4**    | 128k tokens   | 16k tokens       | ✅ Yes               | ✅ Yes              |
| **GPT-3.5-turbo** | 16k tokens | 4k tokens       | ✅ Yes               | ✅ Yes              |
| **o3-mini**  | 200k tokens   | 100k tokens      | ❌ No               | ✅ Yes              |
| **o1**       | 200k tokens   | 100k tokens      | ✅ Yes               | ✅ Yes              |
| **o1-mini**  | 128k tokens   | 65,536 tokens    | ✅ Yes               | ✅ Yes              |
| **o1-preview** | 128k tokens | 32,768 tokens    | ❌ No               | ✅ Yes              |

# Anthropic API Model Reference
| Model                  | Context Window | Max Output Tokens | Supports Temperature? | Supports Streaming? | Vision Support? | Message Batches API? |
|------------------------|---------------|-------------------|----------------------|---------------------|-----------------|----------------------|
| **Claude 3.5 Sonnet**  | 200k tokens   | 8192 tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          | ✅ Yes               |
| **Claude 3.5 Haiku**   | 200k tokens   | 8192 tokens       | ✅ Yes               | ✅ Yes              | ❌ No           | ✅ Yes               |
| **Claude 3 Opus**      | 200k tokens   | 4096 tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          | ✅ Yes               |
| **Claude 3 Sonnet**    | 200k tokens   | 4096 tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          | ❌ No                |
| **Claude 3 Haiku**     | 200k tokens   | 4096 tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          | ✅ Yes               |

- **Training Data Cut-off:**
  - Claude 3.5 Sonnet: April 2024  
  - Claude 3.5 Haiku: July 2024  
  - Claude 3 Opus: August 2023  
  - Claude 3 Sonnet: August 2023  
  - Claude 3 Haiku: August 2023  

All models listed above support temperature adjustments and streaming responses.
# OpenAI API Model Endpoint Compatibility
This table provides a reference for which models are compatible with various OpenAI API endpoints.

| Endpoint                     | Compatible Models |
|------------------------------|------------------|
| **`/v1/assistants`**         | All o-series, all GPT-4o (except `chatgpt-4o-latest`), GPT-4o-mini, GPT-4, and GPT-3.5 Turbo models. The `retrieval` tool requires `gpt-4-turbo-preview` (and subsequent dated model releases) or `gpt-3.5-turbo-1106` (and subsequent versions). |
| **`/v1/audio/transcriptions`** | `whisper-1` |
| **`/v1/audio/translations`**  | `whisper-1` |
| **`/v1/audio/speech`**        | `tts-1`, `tts-1-hd` |
| **`/v1/chat/completions`**    | All o-series, GPT-4o (except for Realtime preview), GPT-4o-mini, GPT-4, and GPT-3.5 Turbo models and their dated releases. `chatgpt-4o-latest` dynamic model. Fine-tuned versions of `gpt-4o`, `gpt-4o-mini`, `gpt-4`, and `gpt-3.5-turbo`. |
| **`/v1/completions (Legacy)`** | `gpt-3.5-turbo-instruct`, `babbage-002`, `davinci-002` |
| **`/v1/embeddings`**          | `text-embedding-3-small`, `text-embedding-3-large`, `text-embedding-ada-002` |
| **`/v1/fine_tuning/jobs`**    | `gpt-4o`, `gpt-4o-mini`, `gpt-4`, `gpt-3.5-turbo` |
| **`/v1/moderations`**         | `text-moderation-stable`, `text-moderation-latest` |
| **`/v1/images/generations`**  | `dall-e-2`, `dall-e-3` |
| **`/v1/realtime (beta)`**     | `gpt-4o-realtime-preview`, `gpt-4o-realtime-preview-2024-10-01` |
