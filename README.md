# OpenAI, Anthropic, Qwen2.5, Mistral & Deepseek - API Limits & Compatibility

## The missing context limit & parameter support guide for local and hosted LLMs

Since OpenAI won't just be normal and give us this, put together a quick reference for my own use that perhaps others can benefit from. This table represents the max current context window length, max input token, and max output token limits for OpenAI via API. This does not apply to ChatGPT through the UI. If anything looks wrong, please flag it or cut a PR to update, and I'll happily merge once confirmed accurate.

Are you using [open-webui](https://github.com/open-webui/open-webui)? You should configure the max context window in the **Settings -> Models** interface under advanced parameters; otherwise, you will always default to 2048 characters, which is far too small for many uses.

This table provides a quick reference to the key parameters of OpenAI's available API-driven models. These values apply to OpenAI's officially hosted API and may not match 3rd party providers.

### OpenAI API Model Reference

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

---

### Anthropic API Model Reference

| Model                  | Context Window | Max Output Tokens | Supports Temperature? | Supports Streaming? | Vision Support? |
|------------------------|---------------|-------------------|----------------------|---------------------|-----------------|
| **Claude 3.5 Sonnet**  | 200k tokens   | 8192 tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          |
| **Claude 3.5 Haiku**   | 200k tokens   | 8192 tokens       | ✅ Yes               | ✅ Yes              | ❌ No           |
| **Claude 3 Opus**      | 200k tokens   | 4096 tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          |
| **Claude 3 Sonnet**    | 200k tokens   | 4096 tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          |
| **Claude 3 Haiku**     | 200k tokens   | 4096 tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          |

#### Training Data Cut-off:
- Claude 3.5 Sonnet: April 2024  
- Claude 3.5 Haiku: July 2024  
- Claude 3 Opus: August 2023  
- Claude 3 Sonnet: August 2023  
- Claude 3 Haiku: August 2023  

---

### DeepSeek API Model Reference

Through official DeepSeek API. Self-hosted supports 128k.

| Model                        | Context Window | Max CoT Tokens | Max Output Tokens | Supports Streaming? | Vision Support? |
|------------------------------|---------------|---------------|-------------------|---------------------|-----------------|
| **deepseek-chat (deepseek v3)**   | 64K tokens    | -             | 8K tokens        | ✅ Yes              | ❌ No           |
| **deepseek-reasoner (deepseek r1)** | 64K tokens  | 32K tokens    | 8K tokens        | ✅ Yes              | ❌ No           |

---

### Qwen2.5 API Model Reference

Self-hosted maximums. Please note that you must configure your inference engine to these maximums, as the default (e.g., Ollama @ 2048 tokens) is generally much lower than the model maximum.

| Model                     | Context Window | Max Output Tokens | Supports Streaming? | Vision Support? |
|---------------------------|---------------|-------------------|---------------------|-----------------|
| **qwen2.5-coder-32b**     | 131,072 tokens | 8K tokens        | ✅ Yes              | ❌ No           |
| **qwen2.5-72b-instruct**  | 131,072 tokens | 8,192 tokens     | ✅ Yes              | ❌ No           |

---

### Mistral API Model Reference

Self-hosted maximums. Please note that you must configure your inference engine to these maximums, as the default (e.g., Ollama @ 2048 tokens) is generally much lower than the model maximum.

| Model                        | Context Window | Max Output Tokens | Supports Streaming? | Vision Support? |
|------------------------------|---------------|-------------------|---------------------|-----------------|
| **Mistral-7B-Instruct-v0**   | 32,000 tokens | 4,096 tokens      | ✅ Yes              | ❌ No           |
| **Mistral Medium**           | 32,000 tokens | 4,096 tokens      | ✅ Yes              | ❌ No           |
| **Mistral Small**            | 32,000 tokens | 4,096 tokens      | ✅ Yes              | ❌ No           |
| **Mistral Large**            | 32,000 tokens | 4,096 tokens      | ✅ Yes              | ❌ No           |
| **Mistral Nemo**             | 128,000 tokens | 4,096 tokens     | ✅ Yes              | ❌ No           |

---

### Other Model Reference

| Model                        | Context Window | Max Output Tokens | Supports Streaming? | Vision Support? |
|------------------------------|---------------|-------------------|---------------------|-----------------|
| **Llama3.3:70b**   | 131,072 tokens | 2,048 tokens      | ✅ Yes              | ❌ No           |
| **Phi4**           | 16,384 tokens | 16,384 tokens (*combined window - 16k total split between input & output)      | ✅ Yes              | ❌ No           |


### OpenAI API Model Endpoint Compatibility

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
