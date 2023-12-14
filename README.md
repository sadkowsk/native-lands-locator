# Native Lands Locator (NatLLo)
Native Lands Locator (NatLLo) is a custom GPT hosted by OpenAI that matches your inputs' geographic references with nearby native and indigenous lands. After identifying in-context geographic entities and relating them to nearby native lands, it then explores the cultural and historical connections of the two. NatLlo has implications for further development using other models and approaches.
- Watch a video walk-through of this repo and a model demonstration here: [youtube link]
- Try NatLLo yourself here: https://chat.openai.com/g/g-KP0esL5Q8-native-lands-locator-natllo

## 1. Overview

### 1-A. Motivation
- Problem: native and indigenous peoples and their lands typically go unmentioned
- Opportunity: NatLLo helps users explore the potential relationships of their resources—from online content to personal work—with native and indigenous lands

### 1-B. Domain Context
This custom GPT operates at the intersection of geographic information systems, indigenous studies, and natural language processing. Native and indigenous peoples and lands are defined as "quote."

### 1-C. Possibilities
- Imagined output, outcome
- Example use cases
- Research contribution

### 1-D. Considerations
- Policy
- Ethics: 

## 2. High-Level Approach

### 2-A. GPT Architecture
Explanation

<img width="855" alt="Screenshot 2023-12-14 at 11 14 18" src="https://github.com/sadkowsk/native-lands-locator/assets/143565317/6910c003-d493-4024-8d18-83046cca46b6">

### 2-B. Task Sequence
See instructionsprompt.md above for the exact instructions prompt that implements the following NLP task sequence:
1. Named Entity Recognition
2. Information Retrieval/Search
3. Data Extraction and Formatting
4. Text Generation and Summarization
5. Question Generation
6. Conditional Logic and Decision Making

## 3. Model Card
- See modelcard.md above
- Also see https://cdn.openai.com/papers/gpt-4-system-card.pdf

## 4. Dataset Fine-Tuning

## 5. Downstream Task Evaluation
- F1 score for extractive question answering

## 6. Demonstration
- Tutorial video screenshots

## 7. Critique

### 7-A. Strengths
- Contribution

### 7-B. Limitations
- Efficiency/latency
- Token cost
- Model appropriateness

## 8. Implications

### 8-A. Extended Uses

### 8-B. Best-Fit Models
- RoBERTa (encoder-only)
- Encoder-decoder

### 8-C. Alternative Deployment

### 8-D. Indigenous Ownership
Further adaptations and deployments of NatLlo should ensure cultural sensitivity and accuracy, respecting consent and representation of native/indigenous communities, safeguarding intellectual property and cultural heritage, and promoting inclusivity and diversity to honor the diverse narratives and perspectives of these groups in a respectful and ethical manner.

## 9. Resources
- Research articles
- Hugging Face course
- Coursera prompt engineering course
- NLPT textbook
- Guides—i.e., “Fine-Tuning a Pretrained Model”
- Indigenous authorities
