# OpenAI, Anthropic, Qwen, Mistral, Deepseek, Llama, Phi, Gemini & More - API Max Context, Output Token Limits & Feature Compatibility

## The missing context limit & parameter support guide for local and hosted LLMs

Since OpenAI won't just be cool and give us a max context and max output parameter in the OpenAI API-compatible models endpoint spec, I put together a quick reference for my own use that perhaps others can benefit from. This table represents the max current context window length, max input token, and max output token limits for OpenAI via API. This does not apply to ChatGPT through the UI. If anything looks wrong, please flag it or cut a PR to update, and I'll happily merge once confirmed accurate.

> [!TIP]
Are you using [open-webui](https://github.com/open-webui/open-webui)? You can configure the max context window in a persistent manner under the **Settings -> Models** interface under advanced parameters.

> [!WARNING]
Editor's note - if you don't utilize a [k/v cache](https://www.microsoft.com/en-us/research/blog/llm-profiling-guides-kv-cache-optimization/), setting the max context (even if you're not filling it up) will use up a **ton** of VRAM and potentially degrade performance. I strongly encourage running Ollama with Flash Attention enabled via `OLLAMA_FLASH_ATTENTION=1` & set `OLLAMA_KV_CACHE_TYPE=q8_0` (you can use a q4_0 quant but quality will degrade more)

This table provides a quick reference to the key parameters of OpenAI's available API-driven models. These values apply to OpenAI's officially hosted API and may not match 3rd party providers.


## OpenAI API Model Reference

Tooling references MCP support.

Reasoning Option refers to the LLM API having an option to turn on thinking for the model.

### Core Generative Models

| Model | Context Window (Tokens) | Max Output Tokens | Image Input | Audio Input | Video Input | Tooling Support | Reasoning Option | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| GPT-5.2 Pro | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ✅ Yes | ✅ Yes | Version of GPT-5.2 that produces smarter and more precise responses. |
| GPT-5.2 | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ✅ Yes | ✅ Yes | The best model for coding and agentic tasks across industries |
| GPT-5.1 | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ✅ Yes | ✅ Yes | The best model for coding and agentic tasks with configurable reasoning effort |
| GPT-5.1 Codex Max | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ❌ No | ✅ Yes | Our most intelligent coding model optimized for long-horizon, agentic coding tasks. |
| GPT-5.1 Codex | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ❌ No | ✅ Yes | A version of GPT-5.1 optimized for agentic coding in Codex. |
| GPT-5 Codex | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ❌ No | ✅ Yes | A version of GPT-5 optimized for agentic coding in Codex |
| GPT-5 | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ✅ Yes | ✅ Yes | Previous intelligent reasoning model for coding and agentic tasks with configurable reasoning effort |
| GPT-5 mini | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ✅ Yes | ✅ Yes | Faster, cost-efficient GPT-5 variant. |
| GPT-5 nano | 400,000 | 128,000 | ✅ Yes | ❌ No | ❌ No | ✅ Yes | ✅ Yes | Fastest, most cost-efficient GPT-5 variant. |
| GPT-4.1 | 1,047,576 | 32,768 | ✅ Yes | ❌ No | ❌ No | ✅ Yes | ❌ No | Smartest non-reasoning model. |
| GPT-4.1 mini | 1,047,576 | 32,768 | ✅ Yes | ❌ No | ❌ No | ❌ No | ❌ No | Smaller, faster version of GPT-4.1. |
| GPT-4.1 nano | 1,047,576 | 32,768 | ✅ Yes | ❌ No | ❌ No | ❌ No | ❌ No | Fastest, most cost-efficient version of GPT-4.1. |
| GPT-4o | 128,000 | 16,384 | ✅ Yes | ❌ No | ❌ No | ❌ No | ❌ No | Omni-modal predecessor to GPT-5. |
| GPT-4o mini | 128,000 | 16,384 | ✅ Yes | ❌ No | ❌ No | ❌ No | ❌ No | Fast, affordable small model for focused tasks. |
| GPT-4 | 8,192 | 8,192 | ❌ No | ❌ No | ❌ No | ❌ No | ❌ No | Older base GPT-4 (Text-only). |
| GPT-4 Turbo | 128,000 | 4,096 | ✅ Yes | ❌ No | ❌ No | ❌ No | ❌ No | An older high-intelligence GPT model, supports images. |
| GPT-3.5 Turbo | 16,385 | 4,096 | ❌ No | ❌ No | ❌ No | ❌ No | ❌ No | Legacy GPT model for chat and non-chat tasks. |
| o1 | 200,000 | 100,000 | ✅ Yes | ❌ No | ❌ No | ❌ No | ✅ Yes | Previous full o-series reasoning model. |
| o1 mini | 128,000 | 65,536 | ❌ No | ❌ No | ❌ No | ❌ No | ✅ Yes | Small model alternative to o1 (Deprecated). |
| o1 Preview | 128,000 | 32,768 | ❌ No | ❌ No | ❌ No | ❌ No | ✅ Yes | Preview of our first o-series reasoning model (Deprecated). |
| o1 pro | 200,000 | 100,000 | ✅ Yes | ❌ No | ❌ No | ❌ No | ✅ Yes | Version of o1 with more compute. |
| o3 | 200,000 | 100,000 | ✅ Yes | ❌ No | ❌ No | ❌ No | ✅ Yes | Reasoning model for complex tasks, succeeded by GPT-5. |
| o3 mini | 200,000 | 100,000 | ❌ No | ❌ No | ❌ No | ❌ No | ✅ Yes | A small model alternative to o3. |
| o4 mini | 200,000 | 100,000 | ✅ Yes | ❌ No | ❌ No | ❌ No | ✅ Yes | Fast, cost-efficient reasoning model, succeeded by GPT-5 mini. |

### Specialized and Non-Generative Models

| Model Name | Category | Multimodal Capability | Notes |
| :--- | :--- | :--- | :--- |
| o3 deep research | Deep Research | Unknown | Most powerful deep research model. |
| GPT Audio | Audio Processing | Audio input/Text output | For audio input/output via Chat Completions API. |
| GPT-4o mini TTS | Audio (TTS) | Text input/Audio output | Text-to-speech model. |
| GPT-4o Transcribe | Audio (STT) | Audio input/Text output | Speech-to-text model. |
| DALL-E 3 | Image Generation | Text input/Image output | Previous generation image generation model. |
| GPT Image 1 | Image Generation | Text input/Image output | State-of-the-art image generation model. |
| GPT-OSS 120b | Open-Weight | Text Only | Most powerful open-weight model, fits into an H100 GPU. |
| GPT-OSS 20b | Open-Weight | Text Only | Medium-sized open-weight model for low latency. |

---

### Anthropic API Model Reference

| Model                  | Context Window | Max Output Tokens | Supports Temperature? | Supports Streaming? | Vision Support? |
|------------------------|---------------|-------------------|----------------------|---------------------|-----------------|
| **Claude 3.7 Sonnet**  | 200k tokens   | 8k tokens (128k extended w/ output-128k-2025-02-19 header)        | ✅ Yes               | ✅ Yes              | ✅ Yes          |
| **Claude 3.5 Sonnet**  | 200k tokens   | 8k tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          |
| **Claude 3.5 Haiku**   | 200k tokens   | 8k tokens       | ✅ Yes               | ✅ Yes              | ❌ No           |
| **Claude 3 Opus**      | 200k tokens   | 4k tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          |
| **Claude 3 Sonnet**    | 200k tokens   | 4k tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          |
| **Claude 3 Haiku**     | 200k tokens   | 4k tokens       | ✅ Yes               | ✅ Yes              | ✅ Yes          |

#### Training Data Cut-off:
- Claude 3.7 Sonnet: October 2024  
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
| **deepseek-chat (deepseek v3)**   | 64k tokens    | -             | 8k tokens        | ✅ Yes              | ❌ No           |
| **deepseek-reasoner (deepseek r1)** | 64k tokens  | 32K tokens    | 8k tokens        | ✅ Yes              | ❌ No           |

---

### Qwen API Model Reference

Self-hosted maximums. Please note that you must configure your inference engine to these maximums, as the default (e.g., Ollama @ 2048 tokens) is generally much lower than the model maximum.

| Model                     | Context Window | Max Output Tokens | Supports Streaming? | Vision Support? |
|---------------------------|---------------|-------------------|---------------------|-----------------|
| **qwen2.5-coder-32b**     | 131,072 tokens | 8k tokens        | ✅ Yes              | ❌ No           |
| **qwen2.5-72b-instruct**  | 131,072 tokens | 8k tokens     | ✅ Yes              | ❌ No           |
| **qwen2.5-3b**  | 32k tokens (default, 128k possible) | 8k tokens     | ✅ Yes              | ❌ No           |
| **qwq**  | 32k tokens | 8k tokens     | ✅ Yes              | ❌ No           |

---

### Mistral API Model Reference

Self-hosted maximums.

| Model                        | Context Window | Max Output Tokens | Supports Streaming? | Vision Support? |
|------------------------------|---------------|-------------------|---------------------|-----------------|
| **Mistral-7B-Instruct-v0**   | 32k tokens | 4k tokens      | ✅ Yes              | ❌ No           |
| **Mistral Medium**           | 32k tokens | 4k tokens      | ✅ Yes              | ❌ No           |
| **Mistral Small**            | 32k tokens | 4k tokens      | ✅ Yes              | ❌ No           |
| **Mistral Large**            | 32k tokens | 4k tokens      | ✅ Yes              | ❌ No           |
| **Mistral Nemo**             | 128k tokens | 4k tokens     | ✅ Yes              | ❌ No           |

---

### Gemini API Model Reference

Includes Gemini (hosted) and Gemma (self hosted).

| Model                        | Context Window | Max Output Tokens | Supports Streaming? | Vision Support? |
|------------------------------|---------------|-------------------|---------------------|-----------------|
| **gemini-2.0-flash**         | 1,048k tokens | 8k tokens      | ✅ Yes              | ❌ No           |
| **gemini-2.5-pro**           | 1,048k tokens | 64k tokens     | ✅ Yes              | ❌ No           |
| **gemma-3**                  | 128k tokens   | Unclear tokens | ✅ Yes              | ❌ No           |
---

### Other Model Reference

| Model                        | Context Window | Max Output Tokens | Supports Streaming? | Vision Support? |
|------------------------------|---------------|-------------------|---------------------|-----------------|
| **Llama3.3:70b**   | 131,072 tokens | 2k tokens      | ✅ Yes              | ❌ No           |
| **Phi4**           | 16k tokens | 16k tokens (*combined window - 16k total split between input & output)      | ✅ Yes              | ❌ No           |
| **Phi4**           | 16k tokens | 16k tokens      | ✅ Yes              | ❌ No           |


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
