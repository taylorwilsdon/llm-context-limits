# openai-api-limits
## OpenAI API Model Parameters Reference
Since OpenAI won't just be normal and give us this, put together a quick reference for my own use that perhaps other can benefit from. This table represents the the max current context window length, max input token and max output token limits for OpenAI via API. This does not apply to ChatGPT through the UI.


| Model Name          | Max Context Length | Max Input Tokens | Max Output Tokens | Supports Temperature | Supports Streaming |
|---------------------|--------------------|------------------|-------------------|----------------------|--------------------|
| **gpt-4**           | 8,192 tokens       | 8,192 tokens     | 4k tokens      | Yes                  | Yes                |
| **gpt-4o**       | 128k tokens      | 32,768 tokens    | 16k tokens     | Yes                  | Yes                |
| **gpt-3.5-turbo**   | 4,096 tokens       | 4,096 tokens     | 4,096 tokens      | Yes                  | Yes                |
| **gpt-3.5-turbo-16k**| 16,384 tokens      | 16,384 tokens    | 16,384 tokens     | Yes                  | Yes                |
| **o1-preview**| 128k tokens       | 4,096 tokens     | 32k tokens      | Yes                  | Yes                |
| **o1-mini**  | 128k tokens       | 2,048 tokens     | 64k tokens      | Yes                  | Yes                |
| **o3-mini**| 200k tokens       | 2,048 tokens     | 100k tokens      | Yes                  | Yes                |
| **text-ada-001**    | 2,048 tokens       | 2,048 tokens     | 2,048 tokens      | Yes                  | Yes                |
| **code-davinci-002**| 8,000 tokens       | 8,000 tokens     | 8,000 tokens      | Yes                  | Yes                |
| **code-cushman-001**| 2,048 tokens       | 2,048 tokens     | 2,048 tokens      | Yes                  | Yes                |
