# Native Lands Locator (NatLLo)
Native Lands Locator (NatLLo) is a custom GPT hosted by OpenAI that matches your inputs' geographic references with nearby native and indigenous lands. After identifying geographic entities and relating them to nearby native lands, it then explores the cultural and historical connections of the two. NatLlo has implications for further development using other models and approaches.
- Watch a video walk-through of this repo and a model demonstration here: [youtube link]
- Try NatLLo yourself here: https://chat.openai.com/g/g-KP0esL5Q8-native-lands-locator-natllo

## 1. Overview

### 1-A. Motivation
Popular references to geographic locations rarely acknowledge these locations' belonging, past or present, to native and indigenous peoples. NatLlo enables users to explore the potential relationships between their input materials with native and indigenous peoples and their lands. In doing so, it aims to counter their historical invisibility and marginalization, fostering appreciation of their cultural and ecological significance. By linking the geographic entities referenced in users' materials to nearby native lands, NatLlo promotes more locally inclusive considerations of global human diversity.

### 1-B. Contributions
- Use Cases: place-based education; project research and drafting
- Research: no comparable fine-tuned models currently on Hugging Face or elsewhere
- Development: adaption for other models; specification of issue areas (i.e., climate impact on indigenous lands, underresourced languages, etc.)

### 1-C. Terms and Ethics
This custom GPT operates at the intersection of geographic information systems, indigenous studies, and natural language processing. The *Indigenous Protocol and Artificial Intelligence Position Paper* by the Indigenous Protocol and Artificial Intelligence Working Group (2020) helps to explain the complexity of the term "indigenous":

> “The emerging identity of 'indigenous peoples' has been adopted as an umbrella term by Indigenous leaders in international arenas, such as the United Nations, while simultaneously opposing a rigorous definition. The use of this term reflects the need for a collective label that supersedes the boundaries of nationstates. It encompasses over 370 million Indigenous peoples from disparate geographical and political backgrounds who, despite distinct cultural differences, share common experiences resulting from the relationship between the Indigenous peoples and present-day nation states."[^1]

Please refer to the *Indigenous Protocol and Artificial Intelligence Position Paper* for further guidance on ethical considerations when engaging native and indigenous peoples in AI.

## 2. High-Level Approach

### 2-A. GPT Architecture
NatLlo is based on GPT-4, a decoder-only autoregressive transformer model. Phuong and Hutter (2022) provide the decoder-only architecture pseudocode in "Formal Algorithms for Transformers,"[^2] screenshot below:

<img width="855" alt="Screenshot 2023-12-14 at 11 14 18" src="https://github.com/sadkowsk/native-lands-locator/assets/143565317/6910c003-d493-4024-8d18-83046cca46b6">

> [!NOTE]
> Algorithm 10's pseudocode specifies the architecture for GPT-2. Phuong and Hutter explain the architecture pseudocode for GPT-3 "is identical except larger, and replaces dense attention in Line 6 by sparse attention, i.e. each token only uses a subset of the full context."

Likewise, based on GPT-4's technical report[^4], the formal pseudocode in Algorithm 10 would incorporate the additional changes to reflect GPT-4's architecture:
- *Increased Parameters and Scale:* Adjust the size of matrices and dimensions (e.g., embeddings, MLP layers) to reflect a larger model scale.
- *Advanced Attention Mechanisms:* Modify Line 6 to incorporate more efficient or adaptive attention mechanisms, potentially beyond sparse attention.
- *Optimized Token and Positional Embeddings:* Update the token and positional embedding matrices (Line 2) to reflect advancements in tokenization and embedding techniques.
- *Enhanced Layer Normalization and MLP Activation:* Revise the layer normalization and MLP activation processes (Lines 5, 7, 8, and 10) for improved efficiency and effectiveness.
- *Robustness and Bias Mitigation Techniques:* Integrate specific steps or parameters designed to address bias and robustness in the model's output, potentially impacting various lines of the algorithm.
- *Algorithmic Efficiency Improvements:* Implement changes across the algorithm to enhance computational efficiency, affecting the structure and computation of various layers and attention mechanisms.

### 2-B. Task Sequence
Prompt engineering methods

See *instructionsprompt.md* above for the exact instructions prompt that implements the following NLP task sequence:

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
- demo.ipynb, code credit to [@darinkist](https://github.com/darinkist/MediumArticle_InteractiveChatGPTSessionsInJupyterNotebook/tree/main)[^3]

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

[^1]: J. E. Lewis et al., “Indigenous Protocol and Artificial Intelligence Position Paper.” Accessed: Dec. 14, 2023. [Online]. Available: https://spectrum.library.concordia.ca/id/eprint/986506/

[^2]: M. Phuong and M. Hutter, “Formal Algorithms for Transformers.” arXiv, Jul. 19, 2022. Accessed: Dec. 14, 2023. [Online]. Available: http://arxiv.org/abs/2207.09238

[^3]: K. Rink, “Run Interactive Sessions With ChatGPT In Jupyter Notebook,” Medium. Accessed: Dec. 14, 2023. [Online]. Available: https://towardsdatascience.com/run-interactive-sessions-with-chatgpt-in-jupyter-notebook-87e00f2ee461

[^4]: OpenAI, “GPT-4 Technical Report,” arXiv.org. Accessed: Dec. 14, 2023. [Online]. Available: https://arxiv.org/abs/2303.08774v3

[^5]: L. Tunstall, L. von Werra, and T. Wolf, “Natural Language Processing with Transformers, Revised Edition,” O’Reilly Media, Inc. Accessed: Dec. 14, 2023. [Online]. Available: https://www.oreilly.com/library/view/natural-language-processing/9781098136789/

[^6]: J. White, “Prompt Engineering for ChatGPT,” Coursera. [Online]. Available: https://www.coursera.org/learn/prompt-engineering
