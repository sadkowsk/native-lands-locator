# Native Lands Locator (NatLLo)
Native Lands Locator (NatLLo) is a custom GPT hosted by OpenAI that matches your inputs' geographic references with nearby native and indigenous lands. After identifying geographic entities and relating them to nearby native lands, it then explores the cultural and historical connections of the two. NatLlo has implications for further development using other models and approaches.
- Watch a video walk-through of this repo and a model demonstration here: [youtube link]
- Try NatLLo yourself here: https://chat.openai.com/g/g-KP0esL5Q8-native-lands-locator-natllo

## 1. Overview

### 1-A. Motivation
Popular references to geographic locations rarely acknowledge these locations' belonging, past or present, to native and indigenous peoples. NatLlo enables users to explore the potential relationships between their input materials with native and indigenous peoples and their lands. In doing so, it aims to counter their historical invisibility and marginalization, fostering appreciation of their cultural and ecological significance. By linking the geographic entities referenced in users' materials to nearby native lands, NatLlo promotes more locally inclusive considerations of global human diversity.

### 1-B. Contributions
- *Use Cases:* place-based education; project research and drafting
- *Research:* no comparable fine-tuned models currently on Hugging Face or elsewhere
- *Development:* adaption for other models; specification of issue areas (i.e., climate impact on indigenous lands, underresourced languages, etc.)

### 1-C. Terms and Ethics
This custom GPT operates at the intersection of geographic information systems, indigenous studies, and natural language processing. The *Indigenous Protocol and Artificial Intelligence Position Paper* by the Indigenous Protocol and Artificial Intelligence Working Group (2020) helps to explain the complexity of the term "indigenous":

> “The emerging identity of 'indigenous peoples' has been adopted as an umbrella term by Indigenous leaders in international arenas, such as the United Nations, while simultaneously opposing a rigorous definition. The use of this term reflects the need for a collective label that supersedes the boundaries of nationstates. It encompasses over 370 million Indigenous peoples from disparate geographical and political backgrounds who, despite distinct cultural differences, share common experiences resulting from the relationship between the Indigenous peoples and present-day nation states."[^1]

Please refer to the *Indigenous Protocol and Artificial Intelligence Position Paper* for further guidance on ethical considerations when engaging native and indigenous peoples in AI.

## 2. Approach

### 2-A. GPT Architecture
NatLlo is based on GPT-4, a decoder-only autoregressive transformer model. Phuong and Hutter (2022) provide the decoder-only architecture pseudocode in "Formal Algorithms for Transformers,"[^2] screenshot below:

<img width="855" alt="Screenshot 2023-12-14 at 11 14 18" src="https://github.com/sadkowsk/native-lands-locator/assets/143565317/6910c003-d493-4024-8d18-83046cca46b6">

> [!NOTE]
> Algorithm 10's pseudocode specifies the architecture for GPT-2. Phuong and Hutter explain the architecture pseudocode for GPT-3 "is identical except larger, and replaces dense attention in Line 6 by sparse attention, i.e. each token only uses a subset of the full context."

In its technical report for GPT-4, OpenAI (2023) also announces why it will not disclose its architecture and other aspects of the model:
> "Given both the competitive landscape and the safety implications of large-scale models like GPT-4, this report contains no further details about the architecture (including model size), hardware, training compute, dataset construction, training method, or similar."[^4]

Alternatively, providing GPT-4 Phuong and Hutter's article and instructing it to reflect its own architecture in Algorithm 10 returned these speculations:

<img width="646" alt="Screenshot 2023-12-14 at 21 05 57" src="https://github.com/sadkowsk/native-lands-locator/assets/143565317/8ff76b29-c4ed-41be-a763-02004f90c941">

### 2-B. Task Sequence
In the first screenshot below, I instruct NatLlo to surprise me with a random geographic entity, referring to natural language processing step (i). NatLlo then proceeds to complete steps (i-v) as internally prompted.

For the exact instructions that prompt NatLlo according this NLP task sequence (i-vi), see `instructionsprompt.md` above.

**i. Response Customization:** This initial step depends on the user’s input. Responses are formatted based on whether the input includes a request for geographic entity identification, references geographic locations, or falls outside these criteria.

**ii. Named Entity Recognition:** As suggested in (i), NatLlo identifies geographic entities mentioned in the user-provided input.

![Screenshot 2023-12-15 at 09 17 50 copy](https://github.com/sadkowsk/native-lands-locator/assets/143565317/4150c055-7af7-408b-9809-0b0db666598a)

**iii. Information Retrieval:** NatLlo then performs an online search to find information about native/indigenous lands associated with these entities.

**iv. Data Formatting:** The first part of the key output includes a structured table containing the geographic entities in (i) and the retrieved native/indigenous entities in (ii).

![Screenshot 2023-12-15 at 09 17 50 copy 2](https://github.com/sadkowsk/native-lands-locator/assets/143565317/ede525c6-a6e3-471b-b0bc-42f0fafe9765)

**v. Text Summarization:** The second part of NatLlo’s output includes a set of concise descriptive statements—one for each geographic entity and native land pair. In cases where a Wikipedia page exists for a native/indigenous land, it also inserts a hyperlink.

![Screenshot 2023-12-15 at 09 17 50 copy 3](https://github.com/sadkowsk/native-lands-locator/assets/143565317/6a528513-c345-4b6d-ae9e-dd6c542a7407)

**vi. Question Generation:** NatLlo’s third output component involves synthesizing three new research questions based on the user's input and the identified geographic entities and native lands.

![Screenshot 2023-12-15 at 09 17 50 copy 4](https://github.com/sadkowsk/native-lands-locator/assets/143565317/126d3640-a8ec-4321-93b8-900d5fc04b35)

## 3. Model Card
- See `modelcard.md` above
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

[^6]: Hugging Face, “Tasks,” Hugging Face. Accessed: Dec. 14, 2023. [Online]. Available: https://huggingface.co/tasks

[^7]: J. White, “Prompt Engineering for ChatGPT,” Coursera. [Online]. Available: https://www.coursera.org/learn/prompt-engineering
