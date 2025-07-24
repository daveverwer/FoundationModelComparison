# Foundation Model Comparison

This repository contains the results of an experiment which aims to evaluate the performance of Apple’s [Foundation Model](https://developer.apple.com/documentation/foundationmodels) (available in iOS 26, macOS 26, watchOS 26, tvOS 26, and visionOS 26) against comparably sized open-source models running in [LM Studio](https://lmstudio.ai/) and popular hosted LLM services (which are _far_ larger and should be more capable).

The prompt is a text summarisation task. It requires the model to condense a lengthy journal entry into a single paragraph under 50 words, written in first person without meta-commentary.

The prompt is designed to be a real-world test of a prompt that might be useful in mobile applications. It tests whether the model can follow strict formatting constraints, maintain conciseness for UI display, and preserve narrative voice. This type of summarisation could be valuable for apps that need to digest long content (emails, articles, documents) into digestible snippets while respecting character limits and maintaining readability.

The full write-up of this experiment is available in [iOS Dev Weekly - Issue 719](https://iosdevweekly.com/issues/719/#start).

# Results

| Model                               | Word Count | Rating |
| ----------------------------------- | ---------- | ------ |
| Apple - Foundation Model            | 49         | 🟢     |
| Anthropic - Claude Sonnet 4         | 93         | 🔴 ¹   |
| Google - Gemini 2.5 Flash           | 100        | 🔴 ²   |
| Google - Gemini 2.5 Pro             | 46         | 🟢     |
| LM Studio - gemma-3n-e4b-it-mlx     | 63         | 🟠     |
| LM Studio - qwen2.5-3b-instruct-mlx | 76         | 🟠     |
| OpenAI - ChatGPT 4o                 | 51         | 🟢     |
| OpenAI - ChatGPT o3                 | 47         | 🟢     |
| OpenAI - ChatGPT o4-mini            | 45         | 🟢     |

## Notes:

¹ Claude Sonnet 4 consistently ignored the word limit, averaging around double what was requested.
² Gemini 2.5 Flash ignored the single paragraph requirement, and _also_ the word limit. 😬
