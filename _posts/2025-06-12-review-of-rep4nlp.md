---
layout: post
title: "What's Happening in Representation Learning? A Look at REP4NLP 2025"
date: 2025-01-27 00:00:00 +0000
categories: nlp
# Optional: add or remove tags as you prefer
tags: [Research, NLP]
hidden: true
toc:
  beginning: true
---

## Introduction: Why I Care About Representation Learning

Representation Learning is one of the primitives of intelligence. In a broad sense, it's the foundation of all abstractions and compressions, necessary precursors for solving complex problems in math and science. More narrowly, learning complex representations by changing weights through gradient descent, has been at the heart of the effectiveness of deep neural nets since their inception and I've found it a compelling part of ML and NLP for years. More specifically, although there have been many different iterations of the "learn meaningful representations of language" problem I've always been quite fond of is Word2Vec. One of the first ML for NLP techniques I learned about, and one that always deserves a mention when talking about representation learning, for its elegance and ability to reveal the underlying "geometry of language" even back in 2012. This first encounter with representation learning for NLP led to an enduring interest in the field and its developments, of which there were plenty in the 2010s. The story of NLP in the 2010s is essentially the story of representation learning for language driving massive improvements across downstream tasks, a story I followed with interest.

Nevertheless, as the NLP community at large has moved more and more towards applied work on agents, prompting and the like, I've also paid less attention to developments in representation learning, despite there being many. Working at a question-answering-from-data company, I've been drawn more toward the practical applications too.
However, in the last few weeks I've decided to take a closer look at the current state of representation learning for NLP by surveying the papers accepted to the REP4NLP 2025 workshop held this past May at ACL in Albuquerque, New Mexico. Here's what I found interesting.

Before we begin, some caveats. First and foremost, the papers in this workshop will only provide a limited snapshot of the field and by their very nature will tend to be a lagging indicator of what people have been working on and talking about. Second, I don't claim to be the most up-to-date member of the NLP community, so some references or methods might be lost on me, but I do have a strong interest in the subfield and have followed it for many years. That said, let's start!

## REP4NLP 2025: What the Community is Working On

I've talked about representation learning more broadly above, but the call for papers for the workshop asked for work on several key themes: **efficient learning and inference** as models scale up (with respect to training data, computing time, and energy consumption), investigating **representation dynamics during training**, **evaluating existing representations for generalization** and robustness, understanding the **relationship between representations and model behaviors**, exploring beyond English textual representations (cross-modal, cross-lingual, knowledge-informed approaches), and **developing new representations using various methods** from language model objectives to neuro-symbolic approaches. The accepted papers reflect this broad scope and can be split into different categories. We'll take a general look at these broad categories and then focus on some of the papers I found most interesting.

### 🔬 Interpretability and Understanding Model Representations/Behavior

**Tracking Universal Features Through Fine-Tuning and Model Merging**
📊 **OpenReview:** N/A | **Suggestion:** [Analyze (Standout)](#tracking-universal-features-through-fine-tuning-and-model-merging) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.1/)
<small>🏷️ **Tags:** #feature-analysis #model-merging #sparse-autoencoders #transfer-learning</small>

**A Comparative Study of Learning Paradigms in Large Language Models via Intrinsic Dimension**
📊 **OpenReview:** N/A | **Suggestion:** [Analyze (Standout)](#a-comparative-study-of-learning-paradigms-in-large-language-models-via-intrinsic-dimension) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.2/)
<small>🏷️ **Tags:** #intrinsic-dimension #in-context-learning #supervised-fine-tuning #representation-analysis</small>

**Reverse Probing: Evaluating Knowledge Transfer via Finetuned Task Embeddings for Coreference Resolution**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.3/)
<small>🏷️ **Tags:** #probing #knowledge-transfer #coreference-resolution #evaluation-methodology</small>

**Notes:** Like the methodological flip of typical probing. Instead of probing complex task representations on simple tasks, they probe simple task embeddings on complex tasks. Neat finding that semantic similarity tasks (paraphrase detection) transfer best to coreference resolution and in general they talked about how to solve some interesting problems like where to take embeddings from LLMs and how to combine them.

### 📝 Text Embeddings

**Prompt Tuning Can Simply Adapt Large Language Models to Text Encoders**
📊 **OpenReview:** N/A | **Suggestion:** Read (If you like embeddings) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.12/)
<small>🏷️ **Tags:** #prompt-tuning #text-encoders #parameter-efficiency #llm-adaptation</small>

**Notes:** Interesting comparison between bidirectional attention and unidirectional one. Cool that it is on taking meaningful embeddings from LLMs. Would be interesting to combine with diffusion LLMs see how the results would differ there.

**Large Language Models Are Overparameterized Text Encoders**
📊 **OpenReview:** N/A | **Suggestion:** Read (If you like embeddings) | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.7/)
<small>🏷️ **Tags:** #model-pruning #overparameterization #text-encoders #efficiency</small>

**Notes:** Super cool finding: can prune 30% of layers with negligible impact, 80% with modest drop. Big question: if 30% of parameters do nothing semantically, what ARE they doing? Regularization? optimization dynamics? Generation-specific computation not needed for encoding? Their method is very simple (3 lines of code) yet effective. Raises some questions about parameter efficiency and what different model components actually contribute.

### 🏗️ Alternative Architectures & Pre-training Objectives

**DEPTH: Discourse Education through Pre-Training Hierarchically**
📊 **OpenReview:** N/A | **Suggestion:** Skim | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.10/)
<small>🏷️ **Tags:** #discourse-learning #hierarchical-pretraining #educational-nlp</small>

**Notes:** Always very cool to see different training objectives. Part of a long line of attempts of inserting sentence-level tasks in LLM pre-training. Smells of bitter lesson though, seems a bit too complex to me. Unclear if the discourse-level issues for GPT-style autoregressive models brought up here are real. Incompatibility of flash attention makes it hard to compare efficiency gains.

**State Space Models are Strong Text Rerankers**
📊 **OpenReview:** N/A | **Suggestion:** Skim | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.13/)
<small>🏷️ **Tags:** #state-space-models #mamba #text-reranking #information-retrieval</small>

**Notes:** Main thing here is that there are a lot of experiments, on different SSMs and different LLMs. Very thorough empirical study on the models + tasks combination, gold for the right person. Conclusions are that "(1) Mamba architectures achieve competitive text ranking performance, comparable to transformer-based models of similar size; (2) they are less efficient in training and inference compared to transformers with flash attention"

**Punctuation Restoration Improves Structure Understanding without Supervision**
📊 **OpenReview:** N/A | **Suggestion:** Skim | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.14/)
<small>🏷️ **Tags:** #punctuation-restoration #structural-understanding #unsupervised-learning #linguistic-structure</small>
**Notes:** The core idea is quite cool. The concept of finding increasingly complex objectives to learn better representations is fun. Shows that punctuation restoration improves structure-related tasks (NER, chunking, POS tagging) by ≥2% in 16/18 experiments. Suggests current pretraining objectives (MLM, autoregressive) might miss important structural knowledge.

### ⚡ Efficiency Gains

**Choose Your Words Wisely: Domain-adaptive Masking Makes Language Models Learn Faster**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.5/)
<small>🏷️ **Tags:** #domain-adaptation #efficient-training #masked-language-modeling #biomedical-nlp</small>

**Amuro & Char: Analyzing the Relationship between Pre-Training and Fine-Tuning of Large Language Models**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.4/)
<small>🏷️ **Tags:** #pre-training #fine-tuning #continual-learning #model-analysis</small>

**Vocabulary-level Memory Efficiency for Language Model Fine-tuning**
📊 **OpenReview:** N/A | **Suggestion:** Open | 🔗 [ACL Anthology](https://aclanthology.org/2025.repl4nlp-1.8/)
<small>🏷️ **Tags:** #memory-efficiency #vocabulary-optimization #fine-tuning #resource-optimization</small>

### 🧠 Multi-Modal or Task-specific

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

#### Summary

**Intro:** This paper offers an excellent window into how Sparse Autoencoders (SAEs) are being used in interpretability research for NLP. Although we might be past the peak of interest that Anthropic's detailed reports generated in late 2023, SAEs remain our best tools for peering directly into transformer weights and getting qualitative accounts of what they represent.

**Setup:** Building on this notion and prior work, Horn and Elliott provide a concise and easy-to-follow analysis of SAE feature persistence after fine-tuning and model merging for a 1-layer Mistral-like transformer model. More specifically they start from a base model trained on an equal split of general english tokens and Python code. Then they finetune separately on two different datasets, one of Lua code and one of english children stories. Finally, a third model is subsequently created as a the result of merging the two finetuned models using Spherical Linear Interpolation, a fancy, more geometrically sound form of weight averaging.

**Results:** For this 1-layer, ---M parameters model the authors find that:

1. **Features learned on the base model persist after fine-tuning**
   63 % of the top-100 base features (by activation frequency) remain detectable in both the finetuned models, these features are mostly "universal" low-level patterns: whitespace, brackets, word-pieces. Higher-level features (e.g., "Python try/except") often do disappear.
2. **Merging has a positive but limited effect on recovering lost features**
   Merge recovers ~11 % of base features that had vanished in one branch but stayed alive in the other. Only ~4 % of features that were present in both branches are corrupted by merging.
3. **Are "robust" features also useful?**
   Features that survive both fine-tunes and the merge contribute ~45 % of total log-prob improvement on a mixed validation set, despite being <10 % of all discovered features.

#### My thoughts

- Very interesting to see SAEs in action
- Did not really buy the "robust features" argument tbh
- Interesting to see how many of the top-100 features would be in models only trained on the finetuned datasets (maybe 50%?) connection to feature universality, how many for models with the same dataset but different training objective
- Interesting connection to LoRA or Federated Learning or model merging in general
- Does it contradict good old Nanda? (He says SAEs are trash now)

### A Comparative Study of Learning Paradigms in Large Language Models via Intrinsic Dimension

_Saahith Janapati, Yangfeng Ji_

#### Summary

**Intro:** Deciding between Supervised Finetuning and In Context Learning is a complex decision from many NLP practitioners. The authors compare the two mechanisms through the lens of a metric called Intrinsic Dimension to give us more insights into these two tuning techniques.

**Setup:** They analyze Llama-3-8B, Llama-2-13B/7B, and Mistral-7B-v0.3 across 8 English benchmarks (AG News, SST-2, CoLA, CommonsenseQA, MMLU, QQP, QNLI, MNLI). For SFT, they use LoRA adapters on Q/K/V/O projection matrices with 1k training examples over 15 epochs, logging checkpoints to track ID dynamics. For ICL, they test k-shot prompts with k ∈ {0,1,2,5,10,12,14,16,18,20}. They measure layer-wise ID via the TwoNN estimator, which entails taking a summary statistic of the distribution of the ratio between the first and second neighbor of the points in the training dataset for the layer at hand.

**Results:**

1. **Fine-tuning dynamics** - ID may decrease initially but then increases steadily, somewhat unintuitively.
2. **ICL vs k** - ID rises from 0-shot up to ~5-10 shots, then plateaus or declines; the k where AUC peaks usually matches where accuracy saturates
3. **Paradigm comparison** - For k ≥ 5, ICL induces consistently higher IDs than SFT across all (model, dataset) pairs—even though SFT reaches better accuracy
4. **Cool finding** - ID can be used as a heuristic to pick SFT checkpoints before overfitting and choose optimal k for ICL performance

#### My thoughts

- Intrinsic dimension is a cool concept for understanding model representations, really like their definition for it. "Intrinsic dimension (ID) is a useful metric for assessing the geometric complexity of a model's representations. It quantifies the number of degrees of freedom in the representation space, serving as a measure of the complexity of the underlying manifolds where the embeddings reside."
- This very cool too. Yin et al. (2024) explore the use of Local Intrinsic Dimension (LID) to detect untruthful outputs from LLMs. Their study reveals that truthful outputs typically exhibit lower LIDs compared to hallucinated ones, suggesting that LID can serve as a signal for truthfulness in LLM generations. They also identify a positive relationship between the ID of data representations and validation performance during fine-tuning.
- Unclear why SFT would have continuosly increasing ID, maybe overfitting maybe overfitting it is unclear
- Interesting comparison between in-context learning and SFT
- Connection to ARC Challenge: Could higher ID representations help with abstract reasoning tasks?

### Bonus: From Tokens to Thoughts - How LLMs and Humans Trade Compression for Meaning

_Chen Shani, Dan Jurafsky, Yann LeCun, Ravid Shwartz-Ziv_

#### Summary

**Intro:** Lecun, Jurafsky and co attempt to answer a very interesting question, how do human representations different from the ones formed by LLMs. Their analysis focuses on compression vs richer abstractions and "Rate-Distortion Theory and the Information Bottleneck principle, to quantitatively compare" the different representations. Specifically, they investigate three research questions: "**[RQ1]:** To what extent do concepts emergent in LLMs align with human-defined conceptual categories? **[RQ2]:** Do LLMs and humans exhibit similar internal geometric structures within these concepts, especially concerning item typicality? **[RQ3]:** How do humans and LLMs differ in their strategies for balancing representational compression with the preservation of semantic fidelity when forming concepts?"

**Setup:** The authors develop an information-theoretic framework drawing from Rate-Distortion Theory and the Information Bottleneck principle to quantitatively compare LLM and human conceptual representations. They analyze token embeddings from a diverse suite of LLMs totaling around 30 different models. For human baselines, they use cognitive psychology datasets: Rosch (1973, 1975) categorization studies and McCloskey & Glucksberg (1978) typicality judgments covering ~3k common words across various conceptual categories. They measure how well different systems balance compression (grouping similar concepts together) versus meaning preservation (keeping important distinctions). They compare how humans and LLMs organize concepts, measuring both how efficiently they compress information and how much semantic detail they retain in the process.

**Results:**

**"LLM-derived clusters significantly align with human-defined conceptual categories**, suggesting they capture key aspects of human conceptual organization. Notably, certain encoder models exhibit surprisingly strong alignment, sometimes outperforming much larger models, highlighting that factors beyond sheer scale influence human-like categorical abstraction."

**"Limited Capture of Semantic Nuance:** While LLMs effectively form broad conceptual categories, their internal representations
demonstrate only modest alignment with human-perceived fine-grained semantic distinctions, such as item typicality or psychological distance to category prototypes. This suggests a divergence in how LLMs and humans structure information within concepts."

**"LLMs demonstrate markedly superior information-theoretic efficiency in their conceptual representations compared to human conceptual structures**. Evaluated via our L-objective, LLM-derived clusters consistently achieve a more "optimal" balance (by this measure) between representational complexity (compression) and semantic distortion. Human
conceptualizations, while richer, appear less statistically compact, suggesting optimization
for pressures beyond pure statistical compressibility"

#### My thoughts

- Amazing question, very cool formulation
- Cool concept of cognitive heritage, geography of the human mind
- this paper deserves a deeper dive, I've yet to fully understand this.
- Cool L-objective worth follow up work on.

## Final thoughts and Next Steps

- All papers super cool building on previous work
- Alternative objectives are fun, would love to do some work on diffusion models connected to this
- ID and SAEs are incredibly cool and seem to be relevant for understanding something about the representations of these models
- Would like to compare the ID SAE features of different architectures or different training data, diffusion reps vs BERT vs GPT-2 reps comparison?
- Universal representation hypothesis is this true? Stay tuned for the next unireps workshop at neurips
- universal representation + L-objective?
