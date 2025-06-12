# What's Happening in Representation Learning? A Look at REP4NLP 2025

_A workshop on representation learning_

---

## Introduction: Why I Care About Representation Learning

Representation Learning is one of the primatives of intelligence. [TODO: Insert explanation for previous sentence and give some "we all do it examples"] It stands at the heart of of the effectiveness of Deep nueral nets and I've found it a compelling part of ML and NLP for years. [TODO maybe Word2Vec story here not sure]

[Nevertheless, in all the excitement over increasingly larger models and their agentic capabilities that I use and develop daily my active search --received less attention-- in this more fundamental task has fallen by the wayside but- I have been able to dedicate as much time to it as I owuld have liked] In the last couple of weeks I've wanted to take a closer look at the current state of representation learning for NLP by surveying the papers accepted to REP4NLP 2025 workshop held this past May at ACL in Albuquerque New Mexico. This is what I've found interesting.

Before we begin some caveats. First and foremost the papers in this workshop will only provide a limited snapshot of the field an by their very nature will tend to be a lagging indicator of what people are working on and talking about now. Second I don't claim to be the most up to date member of the NLP community, so some reference or methods might be lost on me, but I do have a strong interest in the subfield and have followed it for many year. [TODO maybe Word2Vec story here not sure]. That said let's start!

## REP4NLP 2025: What the Community is Working On

I will not attempt to define what is or isn't representation learning, but the call for paper of the workshop asked for [TODO add call for papers]. The accepted papers reflect this and they can broadly be split into difference categories. We'll take a general look at these broad categories and then focus on some of the paper I found most interesting.

### 🔬 **Interpretability and Understanding Model Representations**

**Tracking Universal Features Through Fine-Tuning and Model Merging**
📊 **OpenReview:** N/A | **Suggestion:** [Analyze (Standout)](#tracking-universal-features-through-fine-tuning-and-model-merging) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.1/)
<small>🏷️ **Tags:** #feature-analysis #model-merging #sparse-autoencoders #transfer-learning</small>

**A Comparative Study of Learning Paradigms in Large Language Models via Intrinsic Dimension**
📊 **OpenReview:** N/A | **Suggestion:** [Analyze (Standout)](#a-comparative-study-of-learning-paradigms-in-large-language-models-via-intrinsic-dimension) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.2/)
<small>🏷️ **Tags:** #intrinsic-dimension #in-context-learning #supervised-fine-tuning #representation-analysis</small>

**Reverse Probing: Evaluating Knowledge Transfer via Finetuned Task Embeddings for Coreference Resolution**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.3/)
<small>🏷️ **Tags:** #probing #knowledge-transfer #coreference-resolution #evaluation-methodology</small>
**Notes:** Not that interesting but has good vibes - like the methodological flip of typical probing. Instead of probing complex task representations on simple tasks, they probe simple task embeddings on complex tasks. Neat finding that semantic similarity tasks (paraphrase detection) transfer best to coreference resolution.

### 📝 **Text Embeddings**

**Prompt Tuning Can Simply Adapt Large Language Models to Text Encoders**
📊 **OpenReview:** N/A | **Suggestion:** Read (If you like embeedings) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.12/)
<small>🏷️ **Tags:** #prompt-tuning #text-encoders #parameter-efficiency #llm-adaptation</small>
**Notes:** Interesting comparison between bidirectional attention and unidirectional one. Cool that it is on embeddings. Interesting to combine with diffusion LLMs.

**Large Language Models Are Overparameterized Text Encoders**
📊 **OpenReview:** N/A | **Suggestion:** Read (If you like embeedings) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.7/)
<small>🏷️ **Tags:** #model-pruning #overparameterization #text-encoders #efficiency</small>
**Notes:** Super cool finding: can prune 30% of layers with negligible impact, 80% with modest drop. Big question: if 30% of parameters do nothing semantically, what ARE they doing? Possibilities: implicit regularization? optimization dynamics? generation-specific computation not needed for encoding? L3Prune method is elegantly simple (3 lines of code) yet effective. Raises fundamental questions about parameter efficiency and what different model components actually contribute.

### 🏗️ **Alternative Architectures & Pre-training Objectives**

**State Space Models are Strong Text Rerankers**
📊 **OpenReview:** N/A | **Suggestion:** Skim | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.13/)
<small>🏷️ **Tags:** #state-space-models #mamba #text-reranking #information-retrieval</small>
**Notes:** Main thing here is that there's a lot to experiment with across multiple dimensions: 1) Model architecture (SSMs vs Transformers), 2) Model objective (different pretraining approaches), 3) Finetuning strategies, 4) RLHF approaches. Interesting finding that Mamba models are competitive but less efficient than Transformers with flash attention. Shows the rich experimental space opened up by alternative architectures.

**Punctuation Restoration Improves Structure Understanding without Supervision**
📊 **OpenReview:** N/A | **Suggestion:** Skim | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.14/)
<small>🏷️ **Tags:** #punctuation-restoration #structural-understanding #unsupervised-learning #linguistic-structure</small>
**Notes:** Paper itself doesn't look that interesting but the core idea is quite cool. The concept of finding increasingly complex objectives to learn better representations is compelling. Shows that punctuation restoration improves structure-related tasks (NER, chunning, POS tagging) by ≥2%p in 16/18 experiments. Suggests current pretraining objectives (MLM, autoregressive) miss important structural knowledge.

**DEPTH: Discourse Education through Pre-Training Hierarchically**
📊 **OpenReview:** N/A | **Suggestion:** [Read (Standout)](#depth-discourse-education-through-pre-training-hierarchically) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.10/)
<small>🏷️ **Tags:** #discourse-learning #hierarchical-pretraining #educational-nlp</small>

### ⚡ **Efficiency Gains**

**Choose Your Words Wisely: Domain-adaptive Masking Makes Language Models Learn Faster**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.5/)
<small>🏷️ **Tags:** #domain-adaptation #efficient-training #masked-language-modeling #biomedical-nlp</small>

**Amuro & Char: Analyzing the Relationship between Pre-Training and Fine-Tuning of Large Language Models**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.4/)
<small>🏷️ **Tags:** #pre-training #fine-tuning #continual-learning #model-analysis</small>

**Vocabulary-level Memory Efficiency for Language Model Fine-tuning**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.8/)
<small>🏷️ **Tags:** #memory-efficiency #vocabulary-optimization #fine-tuning #resource-optimization</small>

### 🧠 **Multi-Modal or Task-specific**

**Cross-Modal Learning for Music-to-Music-Video Description Generation**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.11/)
<small>🏷️ **Tags:** #cross-modal #music-video #multimodal-learning #generation</small>

**Efficient Document-level Event Relation Extraction**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.9/)
<small>🏷️ **Tags:** #event-extraction #efficiency #document-level #two-stage-framework</small>

**Investigating Adapters for Parameter-efficient Low-resource Automatic Speech Recognition**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.6/)
<small>🏷️ **Tags:** #adapters #parameter-efficiency #speech-recognition #low-resource</small>

## Standout Papers

### Tracking Universal Features Through Fine-Tuning and Model Merging

_Niels Nielsen Horn, Desmond Elliott_

#### My thoughts

- Clever application of SAEs to track individual features across model adaptations - directly addresses core questions in mechanistic interpretability
- The core question is compelling: "Does a Python exception detection feature survive being adapted through Lua fine-tuning and diluted through model merging?"
- Could have major implications for understanding why model merging works and how to do it more intelligently
- Connects to current work on sparse autoencoders from Anthropic, though at much smaller scale
- Would love to see this scaled up and compared with LoRA approaches for understanding what gets preserved vs. adapted

### DEPTH: Discourse Education through Pre-Trained Hierarchically

_Zachary Elisha Bamberger, Ofek Glick, Chaim Baskin, Yonatan Belinkov_

#### My thoughts

- Interesting attempt to address discourse understanding at pre-training by extending SLM's encoder-only discourse objectives to encoder-decoder models like T5, combining hierarchical sentence representations with dual objectives (sentence un-shuffling + span corruption)
- Impressive finding that DEPTH outperforms T5 on span-corruption loss despite the additional sentence un-shuffling objective, suggesting discourse tasks actually help with reconstruction and showing strong validation on DiscoEval
- Shows clear promise for scaling up and practical applications like RAG over sentence chunks, though computational constraints currently limit scale compared to original T5

### A Comparative Study of Learning Paradigms in Large Language Models via Intrinsic Dimension

_Saahith Janapati, Yangfeng Ji_

#### My thoughts

- Intrinsic dimension is a cool concept for understanding model representations
- Interesting comparison between in-context learning and SFT
- Curious about what higher ID in ICL means for generalization and model flexibility
- Connection to ARC Challenge: Could higher ID representations help with abstract reasoning tasks?

### Bonus: From Tokens to Thoughts - How LLMs and Humans Trade Compression for Meaning

_Chen Shani, Dan Jurafsky, Yann LeCun, Ravid Shwartz-Ziv_

[Placeholder from LLM]This paper asks a fundamental question: do Large Language Models strike the same trade-off between representation compression and semantic fidelity that humans do? Using Rate-Distortion Theory and the Information Bottleneck principle, the authors quantitatively compare human judgements with token embeddings across GPT-2, GPT-NeoX, Llama models, and PaLM-2.

The experimental setup is elegant: extract final-token embeddings for ~3k common words, compute similarities, apply clustering while sweeping compression levels, then compare Information Bottleneck trade-offs against human behavioral data from five cognitive datasets.

Key findings reveal a striking tension:

- **Global alignment but local mismatch** - Models form broad conceptual clusters (birds, tools) matching human categories but miss fine-grained distinctions that humans preserve
- **Compression bias** - LLM curves consistently sit below human curves, indicating they use fewer bits for the same distortion - essentially over-compressing
- **Scale helps but saturates** - Larger models (70B) get closer to human performance but still underperform on semantic nuance
- **Polysemy collapse** - Models merge multiple senses of words into single centroids while humans keep them separate

#### My thoughts

- Elegant application of Information Bottleneck theory to evaluate representation quality - this kind of principled comparison with human cognition is exactly what we need more of
- The persistent compression bias even at larger scales suggests that dense next-token objectives may intrinsically favor efficiency over nuance
- Opens intriguing questions about whether sense-disambiguated tokenizers or multi-embedding schemes could shift the curve toward human-like representation
- Connection to current debates about whether scaling alone will get us to human-level understanding

## Next Steps

## Caveats and Limitations
