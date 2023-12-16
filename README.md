# Native Lands Locator (NatLLo)
Native Lands Locator (NatLLo) is a custom GPT hosted by OpenAI that matches your inputs' geographic references with nearby native and indigenous lands. After identifying geographic entities and relating them to nearby native lands, it then explores the cultural and historical connections of the two. NatLlo has implications for further development using other models and approaches.
- See `modelcard.md` above for the mock Hugging Face model card.
- Watch a video walk-through of this repo and a model demonstration here: [youtube link]
- Try NatLLo yourself here: https://chat.openai.com/g/g-KP0esL5Q8-native-lands-locator-natllo

## 1. Overview

### 1-A. Motivation
Popular references to geographic locations rarely acknowledge these locations' belonging, past or present, to native and indigenous peoples. NatLlo enables users to explore the potential relationships between their input materials with native and indigenous peoples and their lands. In doing so, it aims to counter their historical invisibility and marginalization, fostering appreciation of their cultural and ecological significance. Ultimately, NatLlo promotes more locally inclusive considerations of place.

### 1-B. Contributions
- **Use Cases:** place-based education; project research and drafting
- **Research:** no comparable fine-tuned models currently on Hugging Face or elsewhere
- **Development:** adaption for other models; specification of issue areas (i.e., climate impact on indigenous lands, underresourced languages, etc.)

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

Interestingly though not surprisingly, in its technical report for GPT-4, OpenAI (2023) announces it no longer discloses details on the architectures and other aspects of its models:
> "Given both the competitive landscape and the safety implications of large-scale models like GPT-4, this report contains no further details about the architecture (including model size), hardware, training compute, dataset construction, training method, or similar."[^3]

As a guess, Algorithm 10 adjusted for GPT-4 might include the following changes:
- **Line 2:** updated token and positional embedding matrices
- **Line 6:** more efficient or adaptive attention mechanisms, potentially beyond sparse attention
- **Lines 5, 7, 8, 10:** enhanced layer normalization and MLP activation processes
- **Other:** steps or parameters that address bias in the model's output, potentially impacting various lines

### 2-B. Task Sequence
In the first screenshot below, I instruct NatLlo to surprise me with a random geographic entity, referring to natural language processing step (i). NatLlo then proceeds to complete steps (i-v) as internally prompted.

For the exact instructions that prompt NatLlo according this NLP task sequence (i-vi), see `instructionsprompt.md` above and view as code.

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

## 3. Demonstration
Currently lacking a dedicated Jupyter Notebook or a Hugging Face Space, please watch the NatLlo video tutorial linked below and above. Also consider testing NatLlo yourself using any of the materials linked here:
- Watch a video walk-through of this repo and a model demonstration here: [youtube link]
- Try NatLLo yourself here: https://chat.openai.com/g/g-KP0esL5Q8-native-lands-locator-natllo
- Demonstration/interaction sample materials:
  - News article (New York Times)[^4]: https://www.nytimes.com/2023/12/14/us/rain-storm-forecast-snow.html
  - Scientific article (American Meteorological Society)[^5]: https://journals.ametsoc.org/view/journals/wcas/16/1/WCAS-D-23-0025.1.xml
  - Poem (Simon Armitage)[^6]: https://www.simonarmitage.com/wp-content/uploads/Amended-Ark.pdf

The following screenshot displays the output NatLlo returned after receiving the poem "Ark" by Simon Armitage:

![screencapture-chat-openai-g-g-KP0esL5Q8-native-lands-locator-natllo-c-3b3a7951-5a26-4547-b0e9-bc2099c3c565-2023-12-15-14_45_32](https://github.com/sadkowsk/native-lands-locator/assets/143565317/42c10af5-cfaa-4df6-9a3c-59a18e22c622)

## 4. Critique

### 4-A. Strengths
- **Advanced Language Processing:** GPT-4's autoregressive decoder architecture, training, and input context length of 8,192 tokens effectively facilitate the language reasoning and generation required in NatLLo's latter output
- **Continual Improvement:** as a custom GPT, NatLlo’s capabilities self-update alongside updates to ChatGPT as it is exposed to more data and use cases
- **Accessibility:** GPT-4’s increasing multimodal capabilities bear positive implications for users requiring assistive technologies

### 4-B. Limitations
- **Biases:** risk of biases in GPT-4’s training dataset leading to unfair interpretations of indigenous peoples
- **Errors:** risk of GPT-4 providing incorrect information, especially when responding to complex requests
- **Knowledge Cutoff:** ChatGPT-4's Jan. 2022 knowledge cutoff can limit the currency and breadth of information it provides
- **Latency:** slow processing efficiency with documents uploaded to custom GPT’s knowledge base leads to time-outs
- **Model Appropriateness:** ChatGPT-4’s general-purpose nature not conducive to accurately and reliably returning NatLlo’s multi-part output
- **Fine-Tuning:** current lack of fine-tuning NatLlo on specific datasets leaves it dependent on GPT-4’s original training, likely limiting its effectiveness in certain downstream tasks
- **Evaluation:** current lack of benchmarking NatLlo’s downstream performance limits knowledge of how to strategically improve its efficiency, accuracy, and reliability

## 5. Implications
Next steps for further developing NatLlo might involve adapting it to other transformer models and rigorously testing its capabilities with reputable benchmarks, while upholding ethical practices pertaining to the portrayal of indigenous narratives and intellectual property.

### 5-A. Models and Evaluation
NatLlo's three-part output might excel best when shared between multiple models and methods. Below is a possible new configuration to address some of NatLlo's limitations:
- Named Entity Recognition: DistilBERT
- Retrieval-Augmented Generation: data source with more comprehensive information on indigenous peoples and lands
- Text summarization and question generation: GPT-4 or a free/open-source model like Mixtral 8x7B

Benchmarks and datasets for future evaluation, among many possibilities, include GLUE, F1, and CoNLL-2003.

### 5-B. Indigenous Ownership
Further adaptations and deployments of NatLlo should prioritize ensuring cultural sensitivity and accurate representation of indigenous peoples, including but not limited to respecting indigenous intellectual property and cultural heritage, and promoting inclusivity and diversity to honor indigenous perspectives.

[^1]: J. E. Lewis et al., “Indigenous Protocol and Artificial Intelligence Position Paper.” Accessed: Dec. 14, 2023. [Online]. Available: https://spectrum.library.concordia.ca/id/eprint/986506/

[^2]: M. Phuong and M. Hutter, “Formal Algorithms for Transformers.” arXiv, Jul. 19, 2022. Accessed: Dec. 14, 2023. [Online]. Available: http://arxiv.org/abs/2207.09238

[^3]: OpenAI, “GPT-4 Technical Report,” arXiv.org. Accessed: Dec. 14, 2023. [Online]. Available: https://arxiv.org/abs/2303.08774v3

[^4]: J. Jones, “Where’s the Snow? The East Coast Is in for Another Wet Weekend.,” The New York Times, Dec. 14, 2023. Accessed: Dec. 15, 2023. [Online]. Available: https://www.nytimes.com/2023/12/14/us/rain-storm-forecast-snow.html

[^5]: R. Oelviani et al., “Climate Change Driving Salinity: An Overview of Vulnerabilities, Adaptations, and Challenges for Indonesian Agriculture,” Weather, Climate, and Society, vol. 16, no. 1, pp. 29–49, Dec. 2023, doi: 10.1175/WCAS-D-23-0025.1.

[^6]: S. Armitage, Ark. 2019. Accessed: Dec. 15, 2023. [Online]. Available: https://www.simonarmitage.com/wp-content/uploads/Amended-Ark.pdf
