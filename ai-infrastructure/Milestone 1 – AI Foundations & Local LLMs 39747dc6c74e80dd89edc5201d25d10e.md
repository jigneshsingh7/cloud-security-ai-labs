# Milestone 1 – AI Foundations & Local LLMs

# Lesson 1 – Tokens & Tokenization

A **token** is the smallest unit of text processed by an LLM. It is not necessarily a complete word.

Why Tokens?

- Handles unseen words

- Reduces vocabulary size

- Works well with code and structured text

- Supports multiple languages
- Improves efficiency

#### 📒 Why Don't LLMs Use Words Directly?

Large Language Models (LLMs) **do not process complete words directly** because a word-based vocabulary would become extremely large, inefficient, and difficult to maintain. Human language is constantly evolving, with new words, abbreviations, technical terms, programming languages, emojis, and domain-specific identifiers being created regularly.

Instead of memorizing every possible word, LLMs break text into **smaller reusable units called tokens**. This allows the model to understand both familiar and previously unseen text more efficiently.

Example

Instead of storing every AWS service name individually:

```
CloudFormation, CloudFront, CloudTrail, CloudWatch
```

the tokenizer can reuse smaller text pieces such as:

```
Cloud
Formation
Front
Trail
Watch
```

If AWS launches a new service called **CloudMagic**, the model can still process it because it already understands the reusable pieces rather than relying on a predefined dictionary entry.

> **Key Point:** Tokens allow the model to generalize instead of memorizing every possible word.
> 

---

**Tokenization** is The process of converting input text into tokens before sending it to the model.

Why is Tokenization Necessary?

Tokenization is necessary because neural networks **cannot understand raw text directly**. Before a sentence can be processed, it must first be converted into a numerical representation that the model can work with.

The tokenizer acts as a bridge between **human language** and **machine-readable input**.

Without tokenization, the model would struggle with:

- New or unseen words
- Different languages
- Programming code
- Numbers and mathematical expressions
- URLs and email addresses
- Cloud resource identifiers (ARNs, Instance IDs, etc.)
- Emojis and symbols

### Tokenization Pipeline

```
User Input
      │
      ▼
Tokenizer
      │
      ▼
Tokens
      │
      ▼
Token IDs (Numbers)
      │
      ▼
LLM
```

> **Key Point:** Tokenization converts human-readable text into a format that an LLM can process.
> 

---

#### 📒 How Does Tokenization Help AI Understand Multiple Languages, Code, and Symbols?

A tokenizer does **not treat English, Hindi, Python code, JSON, emojis, or numbers as completely different systems**. Instead, it converts all of them into tokens that the model can process uniformly.

This allows one model to understand many types of input without requiring a separate dictionary for each language or domain.

### Examples

| Input | Example |
| --- | --- |
| English | Hello World |
| Hindi | नमस्ते दुनिया |
| Python | `print("Hello")` |
| JSON | `{"name":"Jignesh"}` |
| AWS ARN | `arn:aws:iam::123456789012:role/Admin` |
| Emoji | 🚀🔥😊 |

All of these are first converted into **tokens**, and then into **numerical token IDs** before reaching the model.

> **Key Point:** Tokenization provides a common representation for text, code, symbols, and multiple languages.
> 

---

#### 📒 How Does Tokenization Affect AI Infrastructure?

Tokenization is not just a language concept—it directly impacts the design, performance, and cost of AI systems.

### 1. Context Window

The context window is measured in **tokens**, not words.

A model with a context window of **128K tokens** can process approximately that many tokens at one time, regardless of how many words they represent.

---

### 2. Performance

More tokens require more computation.

```
More Tokens
      ↓
More Processing
      ↓
Higher Latency
```

Long prompts therefore take longer to process than short prompts.

---

### 3. Memory Usage

Every token occupies memory during inference.

As the number of input tokens increases, memory usage also increases.

---

### 4. API Cost

Most AI providers charge based on **input and output tokens**, not the number of words.

Example:

```
Input Tokens
+
Output Tokens
=
Total Cost
```

Understanding token usage helps optimize AI application costs.

---

### 5. Infrastructure Design

Engineers designing AI systems must consider:

- Maximum context window
- Average token usage per request
- Memory requirements
- Latency
- Cost optimization

For applications like **RAG (Retrieval-Augmented Generation)**, efficient chunking and token management are essential to stay within the model's context window while maintaining response quality.

> **Key Point:** Tokenization influences performance, memory, scalability, and operational cost, making it a fundamental concept in AI Infrastructure.
>