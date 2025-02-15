# openai-api-limits
## OpenAI API Model Parameters Reference
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
