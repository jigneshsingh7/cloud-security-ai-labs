# Notes

# 🧠 Cheat Sheet

| Concept | One-Line Definition | Running Example |
| --- | --- | --- |
| **AI** | Making machines perform tasks requiring human intelligence. | Understands your request. |
| **ML** | Learns patterns from data. | Learns what dogs look like. |
| **DL** | ML using deep neural networks. | Learns complex features like ears, fur, and face. |
| **Neural Network** | Layers of connected mathematical neurons. | Combines tiny features into "Golden Retriever." |
| **Foundation Model** | Large pre-trained model with broad knowledge. | Already knows English, dogs, football, and many other concepts. |
| **LLM** | Foundation Model focused on language. | Understands your text request and generates text. |
| **Multimodal FM** | Foundation Model that works across text, images, audio, etc. | Understands a photo and answers questions about it. |
| **ChatGPT** | An application that orchestrates multiple AI models. | Routes your request to the right model(s) and returns the final result. |

# Artificial Intelligence (AI)

### Definition

Artificial Intelligence (AI) is the broad field of creating machines that can perform tasks requiring human intelligence.

These tasks include:

- Learning
- Reasoning
- Problem Solving
- Understanding Language
- Recognizing Images
- Making Decisions

Think of AI as the **umbrella** that contains everything else.

# Machine Learning (ML)

### Definition

Machine Learning is a subset of AI where computers learn patterns from data instead of being explicitly programmed.

Instead of writing: if its dog it barks 

We give the computer thousands or millions of examples.

It learns the patterns itself.

### Example

Show the computer:

- 1 million dog photos
- 1 million cat photos

Eventually it learns:

> "These patterns usually belong to dogs."
> 

Nobody explicitly programmed those rules.

# Deep Learning (DL)

### Definition

Deep Learning is a type of Machine Learning that uses **Neural Networks** with many layers.

It can learn very complex patterns.

This powers:

- ChatGPT
- Self-driving cars
- Face recognition
- Voice assistants

---

### Example

Instead of learning only: Dog

Deep Learning learns: ears, nose, fur, eyes, body shape

Then combines them into: Golden retiever

---

# Neural Network

### Definition

A Neural Network is a mathematical model inspired by the human brain.

It consists of interconnected "neurons" arranged in layers.

```
Input

↓

Hidden Layer

↓

Hidden Layer

↓

Output
```

Each neuron learns a tiny piece of information.

Together they recognize complex patterns.

---

### Example

Input:

```
Image of a dog
```

Neuron 1:

> detects edges
> 

↓

Neuron 2:

> detects ears
> 

↓

Neuron 3:

> detects fur
> 

↓

Neuron 4:

> detects face
> 

↓

Output:

```
Golden Retriever
```

No single neuron understands the dog.

Together they do.

---

# 5️⃣ Foundation Model (FM)

### Definition

A Foundation Model is a **very large Deep Learning model** trained on enormous amounts of general-purpose data.

It is **not specialized** for one task.

Instead, it develops broad capabilities that can be adapted to many tasks.

It can:

- summarize
- translate
- answer questions
- write code
- reason
- generate content

Think of it as a graduate with a strong general education, ready to specialize when needed.

---

### Example

The Foundation Model already knows:

- English
- Dogs
- Football
- Colors
- Nature
- Stories

It learned all of this during pre-training.

---

# 6️⃣ Large Language Model (LLM)

### Definition

An LLM is a **Foundation Model specialized in understanding and generating language**.

Input:

```
Text
```

Output:

```
Text
```

Examples:

- Llama
- Gemma
- Qwen
- Mistral

---

### Example

User types:

> Show me a picture of a Golden Retriever playing football.
> 

The LLM understands:

- "Show"
- "Picture"
- "Golden Retriever"
- "Playing"
- "Football"

It understands the *meaning* of the request.

It does **not** create the image itself.

Instead, it produces a structured understanding that another model can use.

---

# 7️⃣ Multimodal Foundation Model

### Definition

A Multimodal Foundation Model can understand **multiple types of data**, called modalities.

Examples of modalities:

- Text
- Images
- Audio
- Video

Instead of only processing text, it can reason across several forms of input.

---

### Example

User uploads:

📷 Photo of a dog

and asks:

> What breed is this?
> 

The model processes:

Image ➜ Understanding ➜ Text Answer

Or the user asks:

> Create a picture of this dog wearing sunglasses.
> 

The system combines image understanding with image generation.

---

# 8️⃣ ChatGPT (The Application)

This is the biggest misconception.

ChatGPT is **not just an LLM**.

It is an application that coordinates multiple components.

```
                 User
                   │
                   ▼
               ChatGPT
                   │
     ┌─────────────┼─────────────┐
     │             │             │
     ▼             ▼             ▼
Vision Model      LLM      Image Generator
     │             │             │
     └─────────────┼─────────────┘
                   ▼
             Final Response
```

---

### Example

User says:

> Show me a picture of a Golden Retriever playing football.
> 

Flow:

1. ChatGPT receives the request.
2. The LLM understands the language.
3. The request is converted into a rich image prompt.
4. The image generation model creates the image.
5. ChatGPT returns the image.

The LLM never paints pixels itself.

---

#