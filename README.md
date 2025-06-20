# awesome-hallucination-detection

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/EdinburghNLP/awesome-hallucination-detection) [![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Papers and Summaries


### [Teaching with Lies: Curriculum DPO on Synthetic Negatives for Hallucination Detection](https://arxiv.org/abs/2505.17558v1)

- **Metrics:** Accuracy, Precision, Recall, F1-score
- **Datasets:** MedHallu, HaluEval, DROP, CovidQA, PubMedQA
- **Comments:** Proposes **HaluCheck**, a family of 1B–3B parameter LLM detectors aligned via **Direct Preference Optimization (DPO)** using *synthetic hallucinated negatives* ranked by grounding difficulty (via MiniCheck). Introduces a **curriculum learning** strategy that transitions training from easier to harder negatives. Demonstrates up to **24% relative F1 gains** on MedHallu and HaluEval and strong zero-shot robustness—outperforming larger state-of-the-art models on DROP, CovidQA, and PubMedQA.


### [MultiHal: Multilingual Dataset for Knowledge-Graph Grounded Evaluation of LLM Hallucinations](https://arxiv.org/abs/2505.14101)
- **Metrics:** Semantic similarity with sentence embeddings
- **Datasets:** MultiHal
- **Comments:** Introduces a new factual language modeling benchmark **MultiHal**. Building upon past benchmarks such as Shroom2024, HaluEval, HaluBench, TruthfulQA, Felm, Defan and SimpleQA, the aforementioned benchmarks are extended by mining relevant KG paths from Wikidata. **MultiHal** can be used for comparisons of knowledge updating methods such as RAG and KG-RAG, as well as factual evaluation using the mined KG paths.

### [Similarity-Distance-Magnitude Universal Verification](https://arxiv.org/abs/2502.20167)
- **Metrics:** Index-conditional calibration (i.e., joint prediction- and class-conditional calibration at a given alpha' value)
- **Datasets:** Factcheck (Azaria and Mitchell, 2023); sentiment; MMLU; MMLU-pro (importantly these include distribution-shifted and out-of-distribution evaluations)
- **Comments:** Introduces Similarity-Distance-Magnitude (SDM) activation functions, SDM calibration, and SDM networks, which are neural networks (e.g., LLMs) with uncertainty-aware verification and interpretability-by-exemplar as intrinsic properties. An example of an SDM estimator that can be used for hallucination detection when combined with retrieval (or other applicable grounding) is available via the [open-source Reexpress MCP server](https://github.com/ReexpressAI/reexpress_mcp_server). (2025)

### [Coarse-to-Fine Memory Matching for Joint Retrieval and Classification](https://arxiv.org/abs/2012.02287)
- **Metrics:** Accuracy and FEVER score
- **Datasets:** FEVER and the 2-class analysis sets of Schuster et al. (2019)
- **Comments:** Introduces interpretability-by-exemplar for multi-stage retrieval and classification with a single model, including feature detection via alignment of bi-encoded sequences. Includes a method for beam search through the search graph of bi- and cross-encoded sequences, and an early approach for constraining the output of a retrieval system based on dense matching into the support set. (This is, in effect, an early example of test-time compute with a Transformer language model. Instead of using reinforcement learning, multi-stage search is learned end-to-end via a contrastive loss over bi- and cross-encoded sequences.) (2020)

### [Detecting Local Insights from Global Labels: Supervised & Zero-Shot Sequence Labeling via a Convolutional Decomposition](https://direct.mit.edu/coli/article/47/4/729/106772/Detecting-Local-Insights-from-Global-Labels)
- **Metrics:** F_1, F_0.5, and accuracy against the ground-truth, as well as the model-approximations against the original model's predictions
- **Datasets:** Grammatical error detection and sentiment datasets
- **Comments:** Introduces instance-based, metric-learner approximations of neural network models and hard-attention mechanisms that can be constructed with task-specific inductive biases for effective semi-supervised learning (i.e., feature detection). These mechanisms combine to yield effective methods for interpretability-by-exemplar over the representation space of neural models. Direct relevance for hallucination detection (which is a classification task): This precedes SAE and other contrastive-representation-based interpretability methods, while providing an explicit connection between a test-instance and the training (support set) and providing a pathway for controlling for the epistemic uncertainty. The latter in particular is a limiting factor for the real-world application of many subsequent interpretability methods, including for hallucination detection tasks. (This was submitted to Computational Linguistics for review in 2020 and accepted for publication in 2021, with an additional presentation at EMNLP in 2021.)

### [♟️FactCheckmate: Preemptively Detecting and Mitigating Hallucinations in LMs](https://arxiv.org/abs/2410.02899)
- **Metrics:** For detection: Acc.
- **Datasets:** QA: NQ-Open, MMLU, MedMCQA, GSM8K.
- **Comments:** This work introduces a lightweight classifier that detects hallucinations preemptively conditioning only on the input hidden states, before any text is generated. When hallucinations are predicted, it intervenes in these hidden states to steer the model toward more factual outputs.  Experiments show consistent improvements in factual accuracy across various LLMs, with minimal computational overhead.
  
### [Kernel Language Entropy: Fine-grained Uncertainty Quantification for LLMs from Semantic Similarities](https://arxiv.org/abs/2405.20003)
- **Metrics:** For detection: AUROC, AURAC.
- **Datasets:** QA: TriviaQA, SQuAD, BioASQ, NQ, SVAMP.
- **Comments:** This work presents a method for evaluating the semantic uncertainty of LLM responses. The approach generates multiple response samples and measures their semantic similarity, which is represented as a density matrix (semantic kernel). Semantic uncertainty is then quantified using the von Neumann entropy of this matrix. High uncertainty suggests potential hallucinations, alowing for their detection and mitigation.

### [Steering Knowledge Selection Behaviours in LLMs via SAE-Based Representation Engineering](https://arxiv.org/abs/2410.15999)
- **Metrics:** Exact Match
- **Datasets:** NQSwap, Macnoise
- **Comments:** The first work that uses sparse auto-encoders (SAEs) to enhance both the usage of contextual and parametric knowledge.

### [DeCoRe: Decoding by Contrasting Retrieval Heads to Mitigate Hallucinations](https://arxiv.org/abs/2410.18860)
- **Metrics:** MC1, MC2, MC3 scores for TruthfulQA multiple-choice task; %Truth, %Info, %Truth*Info for TruthfulQA open-ended generation task; subspan Exact Match for the open-domain QA tasks (NQ-Open, NQ-Swap, TriviaQA, PopQA, MuSiQue); accuracy for MemoTrap; Prompt-level and Instruction-level accuracies for IFEval.
- **Datasets:** TruthfulQA, NQ-Open, NQ-Swap, TriviaQA, PopQA, MemoTrap, IFEval, MuSiQue

### [Semantic Density: Uncertainty Quantification for Large Language Models through Confidence Measurement in Semantic Space](https://neurips.cc/virtual/2024/poster/95598)
- **Metrics:** AUROC, AUPR
- **Datasets:** CoQA, TriviaQA, SciQ, NQ
- **Comments:** Proposes a new method, namely semantic density, to provide response-wise confidence/uncertainty scores for detecting LLM hallucinations. Semantic density extracts uncertainty/confidence information for each response from a probability distribution perspective in semantic space. It has no restriction on task types and is "off-the-shelf" for new models and tasks. Significant improvement over other SOTA methods are consistently observed across different datasets and base LLMs.

### [MedHallu: A Comprehensive Benchmark for Detecting Medical Hallucinations in LLMs](https://arxiv.org/abs/2502.14302)
- **Metrics:** Binary hallucination detection (Precision, Recall, F1).
- **Datasets:** *MedHallu* – derived from PubMedQA, containing 10k QA pairs with deliberately planted plausible hallucinations.
- **Comments:** Presents a large-scale medical-focused hallucination detection benchmark. Evaluations show that, on the hardest subset, even top models like GPT-4 achieve only ~0.625 F1 in detecting subtle falsehoods, pointing to the difficulty of medical hallucination detection.

### [Smoothing Out Hallucinations: Mitigating LLM Hallucination with Smoothed Knowledge Distillation](https://arxiv.org/abs/2502.11306)
- **Metrics:** ROUGE-L, BERTScore, factual consistency rate on XSum/CNN-DM (measured via QA-based metrics like QuestEval).
- **Datasets:** CNN/DailyMail, XSum
- **Comments:** Proposes training with soft labels from a teacher LLM to reduce overconfidence and lower hallucination rates in summarization tasks. Maintains quality (ROUGE/BERTScore) while significantly decreasing factual errors.

### [Large Legal Fictions: Profiling Legal Hallucinations in LLMs](https://arxiv.org/abs/2401.01301)
- **Metrics:** Hallucination rate (% of outputs containing any unsupported legal claim).
- **Datasets:** Custom set of factual US case queries, where ground-truth outcomes can be verified.
- **Comments:** Empirical study finding that GPT-3.5 and LLaMA-2 hallucinate in 69% and 88% of legal Q&A, respectively. Highlights the risks of using off-the-shelf LLMs in legal contexts without further training or validation.

### [Hallucination-Minimized Data-to-Answer Framework for Financial Decision-Makers](https://arxiv.org/abs/2311.07592)
- **Metrics:** Custom confidence score combining factual verification (data overlap), retrieval correctness, and final QA consistency.
- **Datasets:** Proprietary financial tables and queries.
- **Comments:** Shows how grounding LLMs in relevant financial data and applying multi-metric validation can exceed 90% confident correctness. Demonstrates an effective approach to curbing hallucinations in finance.

### [Hallucination Detection: A Probabilistic Framework Using Embeddings Distance Analysis](https://arxiv.org/abs/2502.08663)
  * **Metrics**: Accuracy, F1-score (hallucination detection performance).
  * **Datasets**: Synthetic Q&A dataset (generated with Llama2-7B and Llama3-8B) labeled for hallucinated vs. non-hallucinated responses.
  * **Comments**: Proposes analyzing the embedding space of LLM outputs to detect hallucinations. By measuring Minkowski distance between embedded keywords in genuine vs. hallucinated answers, it uncovers structural differences and achieves competitive hallucination detection accuracy (~66%) without external fact-checking.

### [Detecting and Mitigating Hallucination in Large Vision-Language Models via Fine-Grained AI Feedback](https://arxiv.org/abs/2404.14233)
  * **Metrics**: Accuracy, Precision/Recall, F1 (hallucination detection on benchmarks like MHaluBench, MFHaluBench); Hallucination Rate and metrics such as CHAIR, Cover, Hal, Cog (for generation benchmarks like Object HalBench and AMBER).
  * **Datasets**: MHaluBench, MFHaluBench (vision-language hallucination detection datasets); Object HalBench, AMBER, MMHal-Bench, POPE (hallucination mitigation benchmarks for LVLMs).
  * **Comments**: Introduces *HSA-DPO*, a severity-aware direct preference optimization method that uses fine-grained AI feedback to label hallucination severity and prioritize critical errors in training. This approach achieves state-of-the-art performance in detecting visual hallucinations (outperforming GPT-4V and other models) and significantly lowers hallucination occurrence in generated outputs (e.g., 36% reduction on AMBER, 76% on Object HalBench versus the base model).

### [Pelican: Correcting Hallucination in Vision-LLMs via Claim Decomposition and Program of Thought Verification](https://aclanthology.org/2024.emnlp-main.470/)
  * **Metrics**: Hallucination rate reduction (%) and factual accuracy improvements on multiple vision–language instruction benchmarks (e.g., MMHal-Bench, GAVIE, MME).
  * **Datasets**: MMHal-Bench, GAVIE (hallucination evaluation benchmarks for LVLMs); MME (general vision-language understanding benchmark).
  * **Comments**: Proposes a framework (*Pelican*) that detects and mitigates visual hallucinations through claim verification. It decomposes an image-grounded claim into sub-claims and uses *program-of-thought* (code execution with external tools) to verify each sub-claim’s truth. An LLM then assesses overall consistency. Pelican significantly reduces hallucination rates (approx. 8–32% drop across various LVLMs, and 27% lower than prior mitigation methods) while maintaining or improving the models’ factual accuracy in following visual instructions.

### [Distinguishing Ignorance from Error in LLM Hallucinations](https://arxiv.org/abs/2410.22071)
  * **Metrics**: Hallucination type distribution (prevalence of hallucinations despite knowledge vs. due to lack of knowledge); classification accuracy distinguishing HK+ vs. HK- cases; improvements in detection/mitigation when handling these types separately.
  * **Datasets**: *WACK* (Wrong Answers despite Correct Knowledge) – a constructed dataset based on TriviaQA and NaturalQuestions, containing QA instances labeled as HK- (hallucination caused by missing knowledge) or HK+ (hallucination even though the model knows the answer) for specific LLMs.
  * **Comments**: Investigates two distinct causes of hallucination: when the model truly doesn’t know the answer (ignorance) vs. when it knows the answer but still responds incorrectly (error). Introduces an automated approach to generate model-specific labeled examples (the WACK dataset) by testing the model under various prompted scenarios. Shows that a simple classifier on the LLM’s internal representations can differentiate these cases, and that tailoring detection/mitigation to a model’s HK+ (knowledgeable error) cases yields better results than a one-size-fits-all approach.

### [A Genetic Approach to Mitigate Hallucination in Generative IR](https://arxiv.org/abs/2409.00085)
  * **Metrics**: Factuality verification accuracy (FEVER-style support/refute classification of answers), and answer relevance metrics (n-gram overlap, ROUGE/NDCG) in open-domain QA.
  * **Datasets**: TREC Deep Learning 2019 & 2020 (passage ranking QA tasks) and a subset of MS MARCO Dev (for open-domain answer generation).
  * **Comments**: Models the generative information retrieval process as a genetic algorithm (called *GAuGE*: Genetic Approach using Grounded Evolution) to reduce hallucinations in answers. Candidate answers evolve through iterative “mutation” and selection, guided by a simple n-gram overlap fitness score to ensure consistency with retrieved documents. Experiments across several IR datasets show that GAuGE produces highly relevant answers with significantly fewer hallucinated statements (substantially higher fact verification scores) compared to standard RAG-style generation, all without sacrificing answer relevance.

### [MIND: Unsupervised Modeling of Internal States for Hallucination Detection of Large Language Models](https://arxiv.org/abs/2311.09398)
  * **Metrics**: Hallucination detection accuracy and F1-score (token-level and response-level) on the new HELM benchmark; detection latency and throughput.
  * **Datasets**: Wikipedia (used to extract pseudo training data); **HELM** (Hallucination Evaluation for multiple LLMs) – a benchmark with outputs from six different LLMs on Wikipedia-derived prompts, annotated with human labels for hallucinated content along with each model’s internal states.
  * **Comments**: Introduces an *unsupervised, real-time* hallucination detection framework that taps into an LLM’s own hidden states. MIND leverages unannotated Wikipedia text to auto-generate training pairs (prompt, LLM output with hallucination label inferred) and trains a lightweight MLP to predict hallucinations from the model’s activations during inference. This approach avoids heavy external fact-checkers, greatly speeds up detection, and remains model-agnostic. On the HELM benchmark, MIND demonstrates strong hallucination detection performance while significantly reducing computational overhead compared to prior post-processing methods.





### [MARS: Meaning-Aware Response Scoring for Uncertainty Estimation in Generative LLMs](https://aclanthology.org/2024.acl-long.419.pdf)
- **Metrics:** AUROC
- **Datasets:** TriviaQA, NaturalQA, WebQA
- **Comments:** The LLM uncertainty estimation technique called MARS replaces length-normalized probability scoring by assigning greater weights to tokens that contribute more significantly to correctness. 

### [Do Not Design, Learn: A Trainable Scoring Function for Uncertainty Estimation in Generative LLMs](https://arxiv.org/pdf/2406.11278)
- **Metrics:** AUROC, PRR
- **Datasets:** TriviaQA, GSM8k, NaturalQA, WebQA
- **Comments:** The LLM uncertainty estimation technique called LARS trains an encoder-based transformer that takes a query, generation, and token probabilities as input and returns an uncertainty score as output

### [Quantifying Uncertainty in Answers from any Language Model and Enhancing their Trustworthiness](https://aclanthology.org/2024.acl-long.283/)
- **Metrics:** Accuracy, Precision/Recall/Auroc
- **Datasets:** TriviaQA, GSM8k, SVAMP, Common-sense QA
- **Comments:** LLM uncertainty estimation technique called BSDetector that combines self-reflection certainty and observed consistency into a single confidence score. Detects incorrect/hallucinated LLM responses with high precision/recall, and can also automatically boost the accuracy of LLM responses. 

### [Leveraging Hallucinations to Reduce Manual Prompt Dependency in Promptable Segmentation](https://arxiv.org/abs/2408.15205)
- **Metrics:** MAE, F_{beta}, S_{alpha}
- **Datasets:** CHAMELEON, CAMO, COD10K, CVC-ColonDB, Kvasir, ISIC
- **Comments:** The first study does not regard hallucinations as purely negative, but as a common aspect of model pre-training. Unlike previous approaches that directly eliminate hallucinations, ProMaC first stimulates hallucinations to mine the prior knowledge from model pre-training to gather task-relevant information in images. Then, it eliminates irrelevant hallucinations to mitigate their negative impact. The effectiveness of this method has been demonstrated in multiple challenging segmentation tasks.

### [GraphEval: A Knowledge-Graph Based LLM Hallucination Evaluation Framework](https://arxiv.org/abs/2407.10793)
- **Metrics:** Accuracy (detection), Rouge (correction)
- **Datasets:** SummEval, QAGS-C, QAGS-X
- **Comments:** Proposes a hallucination detection *GraphEval* and corection framework *GraphCorrect*. Hallucination detection is done by extracting KG triples from an LLM output and comparing the entailment of the triples with respect to the provided context. Correction is done by taking triples likely to contain hallucinations (entailment below 0.5) are then prompting an LLM to generate a new, factually correct triple with respect to a provided context. Afterwards in a seperate inference pass an LLM is prompted to replace the information in the non-factual LLM output based on the corrected triple. Underlying NLI models that are used for experiments are *HHEM* (DeBERTaV3), *TRUE* and *TrueTeacher* (T5-XXL). The underlying LLM used is Claude2. Final experiments are conducted by computing Rouge scores between reference text and the proposed mitigation method.

### [Lynx: An Open Source Hallucination Evaluation Model](https://arxiv.org/abs/2407.08488)
- **Metrics:** Accuracy
- **Datasets:** HaluBench (consists of ~500 random samples from CovidQA, PubMedQA, DROP, FinanceBench and another set of perturbations based on the retrieved samples)
- **Comments:** Proposes a resource HaluBench and Lynx (Llama3-70bn-instruct based model) for a reference-free metric evaluation. The focus is on instrinsic hallucination evaluation, meaning answers faithful to the given context instead of world knowledge. Hallucinated examples for HaluBench are gathered with GPT-4o. Training of Lynx is done on 2400 samples from RAGTruth, DROP, CovidQA, PubMedQA with GPT4o generated reasoning as part of the training samples. Evaluation is done by extracting a response-level binary label indicating response's faithfulness to the context.

### [LLMs hallucinate graphs too: a structural perspective](https://arxiv.org/abs/2409.00159)
- **Metrics:**  Graph edit distance, spectral distance, distance between degree distributions.
- **Datasets:** Graph Atlas Distance
- **Comments:** This benchmark presents the capability to directly prompt LLMs for known graph structures. Distances from the outputs of LLMs and of the ground truth graphs are studied. A ranking based on graph edit distance sorts LLMs in their hallucination amplitude.

### [HallusionBench: An Advanced Diagnostic Suite for Entangled Language Hallucination and Visual Illusion in Large Vision-Language Models](https://arxiv.org/pdf/2310.14566.pdf)
- **Metrics:**  Accuracy.
- **Datasets:** HallusionBench
- **Comments:** This benchmark presents significant challenges to advanced large visual-language models (LVLMs), such as GPT-4V(Vision), Gemini Pro Vision, Claude 3, and LLaVA-1.5, by emphasizing nuanced understanding and interpretation of visual data. This paper introduces a novel structure for these visual questions designed to establish control groups. This structure is able to conduct a quantitative analysis of the models' response tendencies, logical consistency, and various failure modes.

### [Unified Hallucination Detection for Multimodal Large Language Models](https://arxiv.org/pdf/2402.03190)
- **Metrics:**  Accuracy, F1/Precision/Recall.
- **Datasets:** MHaluBench
- **Framework:** UniHD
- **Comments:** This paper proposes a more unified problem setting for hallucination detection in MLLMs, unveils a meta-evaluation benchmark MHaluBench that encompasses various hallucination categories and multimodal tasks, and introduces UNIHD, a unified framework for the detection of hallucinations in content produced by MLLMs.

### [FactCHD: Benchmarking Fact-Conflicting Hallucination Detection](https://arxiv.org/pdf/2310.12086)
- **Metrics:**  F1 of detection, Match of explanation
- **Datasets:** FactCHD
- **Highlights:** This paper introduces the FACTCHD benchmark, which focuses on detecting fact-conflicting hallucinations. FACTCHD integrates factual knowledge from multiple domains, encompassing a wide range of fact patterns, including raw facts, multi-hop reasoning, comparison, and set operations. Its distinguishing feature lies in its goal to combine evidence chains rooted in factual information, enabling persuasive reasoning in predicting the factuality or non-factuality of a claim.

### [Attention Satisfies: A Constraint-Satisfaction Lens on Factual Errors of Language Models](https://arxiv.org/abs/2309.15098)
- **Metrics:** AUROC, risk-coverage curve operating points
- **Datasets:** CounterFact, factual queries generated from Wikidata
- **Comments:** This paper models factual queries as constraint-satisfaction problems and finds that attention to constraint tokens significantly correlates with factual correctness/hallucinations.

### [TRUE: Re-Evaluating Factual Consistency Evaluation](https://arxiv.org/abs/2204.04991)
- **Metrics:** AUROC, across multiple datasets and evaluation methods
- **Datasets:** PAWS, XSum, QAGS, FRANK, SummEval, BEGIN, Q^2, DialFact, FEVER, VitaminC

### [TrueTeacher: Learning Factual Consistency Evaluation with Large Language Models](https://arxiv.org/abs/2305.11171)
- **Metrics:** AUROC, across multiple datasets and evaluation methods
- **Datasets:** XSum, QAGS, FRANK, SummEval

### [SAC$`^3`$: Reliable Hallucination Detection in Black-Box Language Models via Semantic-aware Cross-check Consistency](https://arxiv.org/abs/2311.01740)
- **Metrics:** Accuracy and AUROC: classification QA and open-domain QA
- **Datasets:** Prime number and senator search from Snowball Hallucination, HotpotQA and Nq-open QA

### [Elastic Weight Removal for Faithful and Abstractive Dialogue Generation](https://arxiv.org/abs/2303.17574)
- **Metrics:** Faithfulness between predicted response and ground-truth knowledge (Tab. 1) -- Critic, Q², BERT F1, F1.
- **Datasets:** Wizard-of-Wikipedia (WoW), the DSTC9 and DSTC11 extensions of MultiWoZ 2.1, FaithDial -- a de-hallucinated subset of WoW.

### [Trusting Your Evidence: Hallucinate Less with Context-aware Decoding](https://arxiv.org/abs/2305.14739)
- **Metrics:** Factual consistency of summaries: BERT-Precision and FactKB. MemoTrap and NQ-Swap: Exact Match.
- **Datasets:** Summarisation: CNN-DM, XSUM. Knowledge Conflicts: MemoTrap, NQ-Swap.

### [When Not to Trust Language Models: Investigating Effectiveness of Parametric and Non-Parametric Memories](https://arxiv.org/abs/2212.10511)
- **Metrics:** Exact Match/Accuracy.
- **Datasets:** QA datasets with long-tail entities: PopQA, EntityQuestions; NQ.

### [Retrieval Augmentation Reduces Hallucination in Conversation](https://arxiv.org/abs/2104.07567)
- **Metrics:** Generation: Perplexity, Unigram Overlap (F1), BLEU-4, ROUGE-L. Overlap between generation and knowledge on which the human grounded during dataset collection: Knowledge F1; only consider words that are infrequent in the dataset when calculating F1: Rare F1.
- **Datasets:** Wow, CMU Document Grounded Conversations (CMU_DoG). Knowledge source: KiLT Wikipedia dump.

### [Just Ask for Calibration: Strategies for Eliciting Calibrated Confidence Scores from Language Models Fine-Tuned with Human Feedback](https://arxiv.org/abs/2305.14975)
- **Metrics:** Expected Calibration Error (ECE) with temperature scaling (ECE-t); accuracy@coverage and coverage@accuracy.
- **Datasets:** Question Answering datasets assessing factual knowledge: TriviaQA, SciQ, TruthfulQA.

### [How Language Model Hallucinations Can Snowball](https://arxiv.org/abs/2305.13534)
- **Metrics:** Percentage of Wrong Answers (Hallucinations) and cases where "the model knows it's wrong" (Snowballed Hallucinations).
- **Datasets:** Primality Testing, Senator Search, Graph Connectivity.

### [Improving Language Models with Advantage-based Offline Policy Gradients](https://arxiv.org/abs/2305.14718)
- **Metrics:** Faithfulness evaluation for Knowledge-Grounded response generation on FaithDial -- FaithCritic, CoLA (Fluency), Dialog Engagement, Length-penalised TF-IDF Diversity. 
- **Datasets:** Faithful Knowledge-Grounded Dialog: FaithDial, a more faithful subset of WoW.

### [Generating with Confidence: Uncertainty Quantification for Black-box Large Language Models](https://arxiv.org/abs/2305.19187)
- **Metrics:** AUROC, AUARC, Uncertainty and Confidence metrics (NumSet, Deg, EigV).
- **Datasets:** CoQA (Open-book Conversational QA dataset), TriviaQA and Natural Questions (Closed-book QA).

### [Contextualized Sequence Likelihood: Enhanced Confidence Scores for Natural Language Generation](https://arxiv.org/abs/2406.01806)
- **Metrics:** AUROC, AUARC; Improved sequence likelihood (log probability of generated sequence) used in Confidence or Uncertainty computation.
- **Datasets:** CoQA (Open-book Conversational QA dataset), TriviaQA and Natural Questions (Closed-book QA).

### [FaithDial: A Faithful Benchmark for Information-Seeking Dialogue](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00529/114373/FaithDial-A-Faithful-Benchmark-for-Information)
- **Metrics:** Metrics measure either the degree of hallucination of generated responses wrt to some given knowledge or their overlap with gold faithful responses: Critic, Q² (F1, NLI), BERTScore, F1, BLEU, ROUGE.
- **Datasets:** FaithDial, WoW.

### [Neural Path Hunter: Reducing Hallucination in Dialogue Systems via Path Grounding](https://arxiv.org/abs/2104.08455)
- **Metrics:** FeQA, a faithfulness metric; Critic, a hallucination critic; BLEU.
- **Datasets:** OpenDialKG, a dataset that provides open-ended dialogue responses grounded on paths from a KG.

### [HaluEval: A Large-Scale Hallucination Evaluation Benchmark](https://arxiv.org/abs/2305.11747)
- **Metrics:** Accuracy: QA, Dialogue, Summarisation.
- **Datasets:** HaluEval, a collection of generated and human-annotated hallucinated samples for evaluating the performance of LLMs in recognising hallucinations.

### [Self-contradictory Hallucinations of Large Language Models: Evaluation, Detection and Mitigation](https://arxiv.org/abs/2305.15852)
- **Metrics:** After generating sentence pairs, it measures precision, recall, and F1 score in detection tasks.
- **Datasets:** 12 selected topics from Wikipedia.

### [Mitigating Language Model Hallucination with Interactive Question-Knowledge Alignment](https://arxiv.org/abs/2305.13669)
- **Metrics:** *Coverage*: a binary metric that determines whether all the correct gold answer values are included in the generated value. *Hallucination*: a binary indicator that assesses the presence of generated values that do not exist in the question values and gold grounding values. *User Simulator*: user simulator as an "oracle" language model with access to attribution information about the target answer.
- **Datasets:** FuzzyQA, a dataset based on HybridDialogue and MuSiQue where complex questions were simplified using ChatGPT.

### [Check Your Facts and Try Again: Improving Large Language Models with External Knowledge and Automated Feedback](https://arxiv.org/abs/2302.12813)
- **Metrics:** KF1, BLEU, ROUGE, chrF, METEOR, BERTScore, BARTScore, BLEURT, Avg length.
- **Datasets:** News Chat: DSTC7 Track 2 was repurposed as an evaluation corpus for news conversation. Customer Service: uses DSTC11 Track 5 as a showcase in a conversational customer service scenario, expanding upon DSTC9 Track 1 by incorporating subjective information.

### [SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models](https://arxiv.org/abs/2303.08896)
- **Metrics:** Sentence-level Hallucination Detection (AUC-PR), and Passage-level Hallucination Detection (Pearson and Spearman's correlation coefficients).
- **Datasets:** Generated Wikipedia articles from WikiBio, with annotated hallucinations.

### [The Internal State of an LLM Knows When it's Lying](https://arxiv.org/abs/2304.13734)
- **Metrics:** Per-topic and average accuracy.
- **Datasets:** The True-False Dataset contains true and false statements covering several topics -- Cities, Inventions, Chemical Elements, Animals, Companies, and Scientific Facts.

### [Chain of Knowledge: A Framework for Grounding Large Language Models with Structured Knowledge Bases](https://arxiv.org/abs/2305.13269)
- **Metrics:** Exact Match.
- **Datasets:** FEVER, Adversarial HotpotQA.

### [Halo: Estimation and Reduction of Hallucinations in Open-Source Weak Large Language Models](https://arxiv.org/abs/2308.11764)
- **Metrics:** HaloCheck and SelfCheckGPT scores; consistency, factuality.
- **Datasets:** Generated and reviewed questions in the NBA domain.

### [A Stitch in Time Saves Nine: Detecting and Mitigating Hallucinations of LLMs by Validating Low-Confidence Generation](https://arxiv.org/abs/2307.03987)
- **Metrics:** Precision and Recall when detecting Sentence-level and Concept-level Hallucinations.
- **Datasets:** ChatGPT-generated paragraphs spanning 150 topics from diverse domains.

### [Sources of Hallucination by Large Language Models on Inference Tasks](https://arxiv.org/abs/2305.14552)
- **Metrics:** Directional Levy/Holt precision and recall with entity insertions and replacements.
- **Datasets:** Levy/Holt dataset, containing premise-hypothesis pairs with a task formatted as *Given [premise P], is it true that [hypothesis H]?*, where the model is evaluated with random premises.

### [Hallucinations in Large Multilingual Translation Models](https://arxiv.org/abs/2303.16104)
- **Metrics:** Rate to which MT system produces hallucinations under perturbation (Language Pair fraction, rate).
- **Datasets:** Flores-101, WMT, TICO.

### [Citation: A Key to Building Responsible and Accountable Large Language Models](https://arxiv.org/abs/2307.02185)
- **Metrics:** N/A
- **Datasets:** N/A

### [Zero-Resource Hallucination Prevention for Large Language Models](https://arxiv.org/abs/2309.02654)
- **Metrics:** Hallucinatory instruction classification: AUC, ACC, F1, PEA.
- **Datasets:** Concept-7, which focuses on classifying potential hallucinatory instructions.

### [RARR: Researching and Revising What Language Models Say, Using Language Models](https://arxiv.org/abs/2210.08726)
- **Metrics:** Attributable to Identified Sources (AIS) scores before and after editing.
- **Datasets:** Generated statements by creating task inputs from three datasets and prompting different models to produce long-form outputs which may contain hallucinations -- Factoid statements, Reasoning chains, and Knowledge-intensive dialogues.

### [Q²: Evaluating Factual Consistency in Knowledge-Grounded Dialogues via Question Generation and Question Answering](https://arxiv.org/abs/2104.08202)
- **Metrics:** Q² is a metric itself, and it is compared with F1 token-level overlap, Precision and Recall, Q² w/o NLI, E2E NLI, Overlap, BERTScore, and BLEU.
- **Datasets:** WoW which contains dialogues in which a bot needs to respond to user inputs in a knowledgeable way; Topical-Chat, a human-human knowledge-grounded conversation dataset; Dialogue NLI, a dataset based on the Persona-Chat dialogue task consisting of premise-hypothesis pairs.

### [Do We Know What We Don’t Know? Studying Unanswerable Questions beyond SQuAD 2.0](https://aclanthology.org/2021.findings-emnlp.385.pdf)
- **Metrics:** EM on All, "Has answer", and "IDK"
- **Datasets:** MNLI, SQuAD 2.0, ACE-whQA.

### [Chain-of-Verification Reduces Hallucination in Large Language Models](https://arxiv.org/abs/2309.11495)
- **Metrics:** Wikidata and Wiki-Category List: test precision, average number of positive and negative (hallucination) entities for list-based questions; MultiSpanQA: F1, Precision, Recall; Longform generation of biographies: FactScore.
- **Datasets:** Wikidata, Wiki-Category List, MultiSpanQA, Longform Generation of Biographies.

### [Detecting and Mitigating Hallucinations in Multilingual Summarisation](https://arxiv.org/abs/2305.13632)
- **Metrics:** mFACT, a novel multilingual faithful metric developed from four English faithfulness metrics: DAE, QAFactEval, ENFS%, and EntFA.
- **Datasets:** XL-Sum, a multilingual summarisation dataset.

### [Hallucinated but Factual! Inspecting the Factuality of Hallucinations in Abstractive Summarization](https://aclanthology.org/2022.acl-long.236/)
- **Metrics:** XEnt: Hallucination (Accuracy, F1), Factuality (Accuracy, F1), ROUGE, % of novel n-gram, Faithfulness (%ENFS, FEQA, DAE), EntFA (% Factual Ent., % Factual Hal.)
- **Datasets:** A novel dataset, XEnt, for analysing entity hallucination and factuality in abstractive summarisation, consisting of 800 summaries generated by BART and annotated. MEnt, a set of factuality and hallucination annotations for XSum.
- **Comments:** Tab. 2 outlines several types of hallucinations (e.g., factual, non-factual, intrinsic).

### [Enabling Large Language Models to Generate Text with Citations](https://arxiv.org/abs/2305.14627)
- **Metrics:** Fluency (MAUVE), Correctness (EM recall for ASQA, recall-5 for QAMPARI, claim recall for ELI5), Citation quality (citation recall, citation precision).
- **Datasets:** QA datasets such that 1) they contain factual questions in which references are important, 2) questions require long-text answers covering multiple aspects, and 3) answering the questions requires synthesising multiple sources: ASQA, QAMPARI, ELI5.

### [A Token-level Reference-free Hallucination Detection Benchmark for Free-form Text Generation](https://arxiv.org/abs/2104.08704)
- **Metrics:** Acc, G-Mean, BSS, AUC, Not Hallucination (P, R, F1), Hallucination (P, R, F1).
- **Datasets:** HaDes (HAllucination DEtection dataSet), a novel token-level reference-free annotated hallucination detection dataset obtained by perturbing a large number of text segments extracted from the English Wikipedia and verified with crowd-sourced annotations.
- **Comments:** Fig. 3 outlines several hallucination types (domain-specific knowledge, commonsense knowledge, incoherence or improper collocation, unrelated to central topic, conflict with preceding context, conflict with succeeding context, ..)

### [Generating Benchmarks for Factuality Evaluation of Language Models](https://arxiv.org/abs/2307.06908)
- **Metrics:** Percentage of examples it assigns the highest probability to the factual completion.
- **Datasets:** Wiki-FACTOR and News-FACTOR: two novel factuality evaluation benchmarks for LLMs, based on Wikipedia and News articles. Each example consists of a prefix, a factual completion and three similar but non-factual alternatives.
- **Comments:** The paper introduces a framework for automatically generating such datasets from a given corpus, detailed in Section 3.

### [Do Language Models Know When They're Hallucinating References?](https://arxiv.org/abs/2305.18248)
- **Metrics:** Hallucination rate (H%, out of 1000 generated titles)
- **Datasets:** Generated (true and hallucinated) references on topics from the ACM Computing Classification System.

### [Why Does ChatGPT Fall Short in Providing Truthful Answers?](https://arxiv.org/abs/2304.10513)
- **Metrics:** #Correct and #Wrong answers, and different type of failure counts: Comprehension, Factualness, Specificity, Inference.
- **Datasets:** HotpotQA, BoolQ
- **Comments:** This has a nice taxonomy on different error types -- e.g., *comprehension*, *factualness*, *specifity*, *inference*.

### [LM vs LM: Detecting Factual Errors via Cross Examination](https://arxiv.org/abs/2305.13281)
- **Metrics:** Precision, Recall, F1 (under different cross-examination strategies: AYS, IDK, Confidence-Based, IC-IDK)
- **Datasets:** TriviaQA, NQ, PopQA

### [RHO (ρ): Reducing Hallucination in Open-domain Dialogues with Knowledge Grounding](https://arxiv.org/abs/2212.01588)
- **Metrics:** BLEU, ROUGE-L; FeQA, QuestEval, EntityCoverage (Precision, Recall, F1) to estimate the hallucination degree -- FrQA and QuestEval are QA-based metrics for evaluating the faithfulness of the output in the generation task.
- **Datasets:** OpenDialKG

### [FActScore: Fine-grained Atomic Evaluation of Factual Precision in Long Form Text Generation](https://arxiv.org/abs/2305.14251)
- **Metrics:** %Supported statements across varying frequency levels of human entities.
- **Datasets:** People biographies generated from LLMs, where human annotators break them into supporting facts.

### [ExpertQA: Expert-Curated Questions and Attributed Answers](https://arxiv.org/abs/2309.07852)
- **Metrics:** zero-shot (P, R, F1) and fine-tuned (P, R, F1) of AutoAIS labels; FActScore F1 scores on reference factuality labels; AutoAIS (Attributable to Identified Sources) scores.
- **Datasets:** Expert-curated questions across multiple fields (e.g., Anthropology, Architecture, Biology, Chemistry, Engineering & Technology, Healthcare/Medicine; see Tab. 1 for a sample) organised by Question Type (e.g., Directed question with single unambiguous answer, open-ended potentially ambiguous question, summarisation of information of a topic, advice or suggestion on how to approach a problem; see Tab. 2)

### [DoLa: Decoding by Contrasting Layers Improves Factuality in Large Language Models](https://arxiv.org/abs/2309.03883)
- **Metrics:** TruthffulQA: MC1, MC2, MC3 scores; FACTOR: News, Wiki; these were multiple-choice results. Open-ended generation: for TruthfulQA, they use %Truth, %Info, %Truth*Info, %Reject; for CoT tasks (StrategyQA and GSM8K) they go with accuracy.
- **Datasets:** TruthfulQA, FACTOR (news/wiki), StrategyQA, GSM8K

### [FreshLLMs: Refreshing Large Language Models with Search Engine Augmentation](https://arxiv.org/abs/2310.03214)
- **Metrics:** Accuracy (Strict, Relaxed on Fast-changing questions, Slow-changing questions, Never-changing questions, False-premise questions involve knowledge before 2022 and since 2022, 1-hop and multi-hop questions, and Overall).
- **Datasets:** FreshQA, a new QA benchmark with 600 questions covering a wide spectrum of question and answer types.

### [Beyond Factuality: A Comprehensive Evaluation of Large Language Models as Knowledge Generators](https://arxiv.org/abs/2310.07289)
- **Metrics:** Factuality, Relevance, Coherence, Informativeness, Helpfulness and Validity.
- **Datasets:** Natural Questions, Wizard of Wikipedia.

### [Complex Claim Verification with Evidence Retrieved in the Wild](https://arxiv.org/abs/2305.11859)
- **Metrics:** Accuracy, MAE, Macro-F1, soft accuracy.
- **Datasets:** ClaimDecomp, which contains 1200 complex claims from PolitiFactL each claim is labeled with one of the six veracity labels, a justification paragraph written by expect fact-checkers, and subquestions annotated by prior work.

### [FELM: Benchmarking Factuality Evaluation of Large Language Models](https://arxiv.org/abs/2310.00741)
- **Metrics:** Accuracy, F1/Precision/Recall.
- **Datasets:** Reasoning, Math, Writing/Rec, Science/Tech, World Knowledge: GSM8K, ChatGPT, MATH, TruthfulQA, Quora, MMLU/hc3.

### [Evaluating Hallucinations in Chinese Large Language Models](https://arxiv.org/abs/2310.03368)
- **Metrics:** Humand and GPT-4 evaluations.
- **Datasets:** HalluQA (which they propose), and mention TruthfulQA, ChineseFactEval, HaluEval.

### [On Faithfulness and Factuality in Abstractive Summarization](https://arxiv.org/abs/2305.11747)
- **Metrics:** ROUGE, BERTScore; human assessment (identify hallucinatory spans, and whether it's intrinsic or extrinsic) -- *intrinsic hallucinations* are manipulations of the information in the input document, while *extrinsic hallucinations* are information not directly inferable from the input document. Humans were asked to annotate intrinsic and extrinsic hallucinations.
- **Datasets:** XSum.

### [QuestEval: Summarization Asks for Fact-based Evaluation](https://arxiv.org/abs/2103.12693)
- **Metrics:** QuestEval (proposed in this work), for testing for *consistency*, *coherence*, *fluency*, and *relevance*. ROUGE, BLUE, METEOR, BERTScore. SummaQA, QAGS.
- **Datasets:** SummEval, QAGS-XSUM, SQuAD-v2.

### [QAFactEval: Improved QA-Based Factual Consistency Evaluation for Summarization](https://arxiv.org/abs/2112.08542)
- **Metrics:** QAFactEval (proposed in this work), measuring answer selection, question generation, question answering, answer overlap, and filtering/answerability.
- **Datasets:** SummaC, a collection of benchmarks for binary factual consistency evaluation; CGS, correct and incorrect sentences from CNN/DailyMail; XSF; Polytope; FactCC; SummEval; FRANK; QAGs.

### [Fast and Accurate Factual Inconsistency Detection Over Long Documents](https://arxiv.org/abs/2310.13189)
- **Metrics:** SCALE (new metric proposed in this work). Compared with Q², ANLI, SummaC, F1, BLEURT, QuestEval, BARTScore, BERTScore (Table 3). 
- **Datasets:** TRUE benchmark and ScreenEval, new dataset proposed in this work to assess the factual inconsistency in long-form dialogues (52 documents from SummScreen).

### [Understanding Factuality in Abstractive Summarization with FRANK: A Benchmark for Factuality Metrics](https://arxiv.org/abs/2104.13346)
- **Metrics:** BERTScore, FEQA, QGFS, DAE, FactCC
- **Datasets:** Proposed a new dataset FRANK: human annotated factual errors for CNN/DM and XSum dataset

### [TRUE: Re-evaluating Factual Consistency Evaluation](https://aclanthology.org/2022.dialdoc-1.19/)
- **Metrics:** Q², ANLI, SummaC, BLEURT, QuestEval, FactCC, BARTScore, BERTScore
- **Datasets:** Consolidation of 11 different human annotated datasets for fctual consistency.

### [The Curious Case of Hallucinatory (Un)answerability: Finding Truths in the Hidden States of Over-Confident Large Language Models](https://aclanthology.org/2023.emnlp-main.220/)
- **Metrics:** (classification) F-1, Exact Match, (token) F-1
- **Datasets:** SQuAD, Natural Questions, MuSiQue
- **Comments:** This paper models explores LLMs' handling of (un)answerable questions in a closed-book setting, namely answering a question based on a given passage, where the passage doesn't have the answer. The paper shows that despite LLMs' tendency to hallucinate contextual answers, rather than state that they cannot answer the question, they possess internal understanding of the question's (un)answerability.

### [Do Androids Know They're Only Dreaming of Electric Sheep?](https://arxiv.org/abs/2312.17249)
- **Metrics:** (Hallucination detection) Response-level F1, Span-level Partial Credit Match F1
- **Datasets:** Organically generated and synthetically edited CNN DailyMail, ConvFEVER, and E2E, labeled span-wise for hallucinations
- **Comments:** Language models know when they're hallucinating, and we can train probes on LLM hidden states during decoding to reliably detect them. 

### [Correction with Backtracking Reduces Hallucination in Summarization](https://arxiv.org/abs/2310.16176)
- **Metrics:** AlignScore, FactCC, BS-Fact, ROUGE-L
- **Datasets:** CNN/DM, XSum, Newsroom

### [Fine-grained Hallucination Detection and Editing for Language Models](https://arxiv.org/abs/2401.06855)
- **Metrics:** Precision, Recall, F1.
- **Datasets:** Custom fine-grained hallucination detection/editing dataset for various types of (factual) hallucinations: Entity, Relation, Contradictory, Invented, Subjective, Unverifiable.

### [LLMs as Factual Reasoners: Insights from Existing Benchmarks and Beyond](https://arxiv.org/abs/2305.14540)
- **Metrics:** Accuracy for various error types -- positive examples, date swap, entity swap, negated sentences, number swap, pronoun swap.
- **Datasets:** They propose SummEdits, a 10-domain inconsistency detection benchmark.

### [Evaluating the Factual Consistency of Abstractive Text Summarization](https://arxiv.org/abs/1910.12840)
- **Metrics:** They propose FactCC, a metric that measures the factual consistency of abstractive text summarization (intuition: a summary is factually consistent if it contains the same facts as the source document)
- **Datasets:** CNN/DM for generating training data; MNLI and FEVER for training models. Human-based experiments for evaluation on claims about CNN/DM articles.

### [SummaC: Re-Visiting NLI-based Models for Inconsistency Detection in Summarization](https://arxiv.org/abs/2111.09525)
- **Metrics:** Each dataset comes with its metrics (e.g., CoGenSumm uses a reranking-based measure; XSumFaith, SummEval, and FRANK propose several metrics and analyse how they correlate with human annotations; etc.) -- for SummaC, authors propose using balanced accuracy.
- **Datasets:** They propose SummaC (Summary Consistency), a benchmark consisting of six large inconsistency detection datasets: CoGenSumm, XSumFaith, Polytope, FactCC, SummEval, and FRANK.

### [On the Origin of Hallucinations in Conversational Models: Is it the Datasets or the Models?](https://arxiv.org/abs/2204.07931)
- **Metrics:** Expert and non-expert annotations: Partial Hallucination, Entailment, Hallucination, Uncoop, Generic (each of these categories has more fine-grained sub-classes -- see e.g., Fig. 2) -- annotations follow the BEGIN and VRM taxonomies.
- **Datasets:** Knowledge-grounded conversational benchmarks: Wizard of Wikipedia (WoW), CMU-DoG, and TopicalChat -- datasets consisting of dialogues between two speakers where the goal is to communicate information about particular topics while speakers are presented with a knowledge snippet relevant to the current turn.

### [Teaching Language Models to Hallucinate Less with Synthetic Tasks](https://arxiv.org/abs/2310.06827)
- **Metrics:** Hallucination rate in several settings (original, with optimised system message, with full LLM weights, with synthetic data, or with mixtures of synthetic and reference data); BLEU, ROUGE-1, ROUGE-2, ROUGE-L.
- **Datasets:** Search-and-retrieve (MS MARCO), meeting summarisation (QMSum), automated clinical report generation (ACI-Bench).

### [Faithfulness-Aware Decoding Strategies for Abstractive Summarization](https://arxiv.org/abs/2303.03278)
- **Metrics:** ROUGE-L, BERTScore, BS-Fact, FactCC, DAE, QuestEval
- **Datasets:** CNN/DM, XSum

### [KL-Divergence Guided Temperature Sampling](https://arxiv.org/abs/2306.01286)
- **Metrics:** Conversational QA: models fine-tuned on MNLI, SNLI, FEVER, PAWS, ScTail, and VitaminC. Summarisation: models fine-tuned on ANLI and XNLI.
- **Datasets:** Question Rewriting in Conversational Context (QReCC), XLSum.

### [Investigating Hallucinations in Pruned Large Language Models for Abstractive Summarization](https://arxiv.org/abs/2311.09335)
- **Metrics:** Hallucination Risk Metrics (HaRiM+), SummaC, SummaCzs, SummaCconv, Hallucination Risk Ratio (HRR)
- **Datasets:** FactCC, Polytope, SummEval, Legal Contracts, RCT

### [Entity-Based Knowledge Conflicts in Question Answering](https://arxiv.org/abs/2109.05052)
- **Metrics:** EM, Memorisation ratio.
- **Datasets:** NQ Dev with Answer Overlap (AO) and No Answer Overlap (NAO), NewsQA.

### [TruthX: Alleviating Hallucinations by Editing Large Language Models in Truthful Space](https://arxiv.org/abs/2402.17811)
- **Metrics:** MC1/MC2/MC3 scores for TruthffulQA multiple-choice task; %Truth, %Info, %Truth*Info for TruthffulQA open-ended generation task; Choice accuracy for Natural Questions, TriviaQA and FACTOR (news, expert, wiki).
- **Datasets:** TruthfulQA, Natural Questions, TriviaQA, FACTOR (news, expert, wiki)

### [Question Decomposition Improves the Faithfulness of Model-Generated Reasoning](https://arxiv.org/abs/2307.11768)
- **Metrics:** Accuracy, Final Answer Truncation Sensitivity, Final Answer Corruption Sensitivity, Biased-Context Accuracy Change.
- **Datasets:** HotpotQA, OpenbookQA, StrategyQA, TruthfulQA.

### [Self-contradictory Hallucinations of Large Language Models: Evaluation, Detection and Mitigation](https://arxiv.org/abs/2305.15852)
- **Metrics:** For detection: Precision, Recall, F1. For Mitigation: Ratio of self-contradiction removed, Ratio of informative facts retained, perplexity increased.
- **Datasets:** Custom Open-domain Text Generation dataset, LLM-generated encyclopedic text descriptions for Wikipedia entities, PopQA.

### [Detecting hallucinations in large language models using semantic entropy](https://www.nature.com/articles/s41586-024-07421-0)
- **Metrics:** For detection: AUROC, AURAC.
- **Datasets:** QA: TriviaQA, SQuAD, BioASQ, NQ-Open, SVAMP. FactualBio, a biography-generation dataset, accompanying this paper.

### [CAST: Cross-modal Alignment Similarity Test for Vision Language Models](https://arxiv.org/abs/2409.11007)
- **Metrics:** Propose CAST, a simple self-consistency metric that seeks to evaluate whether multimodal models are consistent across modalities. This works in two stage, in the first stage the models generate similarities/true statements comparing two inputs, and in the second stage the model judges its own output for truthfulness. A consistent model should therefore always evaluate its own outputs as true.

### [Uncertainty Quantification for Language Models: A Suite of Black-Box, White-Box, LLM Judge, and Ensemble Scorers](https://arxiv.org/abs/2504.19254)
- **Metrics:** Black-box (consistency-based scorers): non-contradiction probability, normalized semantic negentropy, normalized cosine similarity, BERTSCore, BLEURT, and exact match rate. White-box (token-probability-based) scorers: minimum token probability, length-normalized token probability. LLM-as-a-Judge scorers: categorical (incorrect/uncertain/correct). Proposed novel, tunable ensemble scorer that is a weighted average of any combination of black-box, white-box, and LLM-as-a-Judge scorers, where weights can be tuned using a user-provided set of graded LLM responses. 

## Domain-specific Entries

### [Med-HALT: Medical Domain Hallucination Test for Large Language Models](https://arxiv.org/abs/2307.15343)
- **Metrics:** Reasoning Hallucination Tests (False Confidence Tests, None of the Above Tests, Fake Questions Tests), Memory Hallucination Tests (Abstract-to-Link Tests, PMID-to-Title Tests, Title-to-Link Tests, Link-to-Title Tests); Accuracy, Pointwise Score.
- **Datasets:** Med-HALT: MEDMCQA, Headqa, Medqa USMILE, Medqa (Taiwan), Pubmed.

### [Retrieval-Based Prompt Selection for Code-Related Few-Shot Learning](https://people.ece.ubc.ca/amesbah/resources/papers/cedar-icse23.pdf)
- **Metrics:** Accuracy, Accuracy plausible match
- **Datasets:** ATLAS dataset, TFix dataset
- **Comments:**: Published at ICSE 2023



## Overviews, Surveys, and Shared Tasks

- [Mitigating LLM Hallucinations: a multifaceted approach](https://amatriain.net/blog/hallucinations)
- [Siren’s Song in the AI Ocean: A Survey on Hallucination in Large Language Models](https://arxiv.org/abs/2309.01219)
- [Survey of Hallucination in Natural Language Generation](https://arxiv.org/abs/2202.03629)
- [A Survey of Hallucination in Large Foundation Models](https://arxiv.org/abs/2309.05922)
- [A Survey on Hallucination in Large Language Models: Principles, Taxonomy, Challenges, and Open Questions](https://github.com/LuckyyySTA/Awesome-LLM-hallucination)
    - Paper available [here](https://arxiv.org/abs/2311.05232)
    - Two main categories: *factuality hallucinations* and *faithfulness hallucinations*. Factuality hallucinations emphasise the discrepancy between generated content and verifiable real-world facts, typically manifesting as factual inconsistencies or fabrications. Faithfulness hallucinations refer to the divergence of generated content from user instructions or the context provided by the input, as well as self-consistency within generated content.
- [LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/)
- [SemEval-2024 Task-6 - SHROOM, a Shared-task on Hallucinations and Related Observable Overgeneration Mistakes](https://helsinki-nlp.github.io/shroom/)
- [llm-hallucination-survey](https://github.com/HillZhang1999/llm-hallucination-survey)
- [How Do Large Language Models Capture the Ever-changing World Knowledge? A Review of Recent Advances](https://arxiv.org/abs/2310.07343)
- [The Dawn After the Dark: An Empirical Study on Factuality Hallucination in Large Language Models](https://arxiv.org/abs/2401.03205)

![Taxonomy from Huang et al.](figures/huang_taxonomy.png "Taxonomy")

## Taxonomies

[Survey of Hallucination in Natural Language Generation](https://arxiv.org/abs/2202.03629) classifies metrics in *Statistical* (ROUGE, BLEU, PARENT, Knowledge F1, ..) and *Model-based* metrics. The latter are further structured in the following classes:
- **Information-Extraction (IE)-based**: retrieve an answer from a knowledge source and compare it with the generated answer -- there might be problems due to the error propagation from the IE model.
- **QA-based**: measure the overlap/consistency between generation and source reference, based on the intuition that similar answers will be generated from the same question if the generation is factually consistent with the source reference. Used to evaluate hallucinations in summarisation, dialogue, and data2text generation. Composed of a *question generation* model and a *question answering* model.
- **Natural Language Inference (NLI)-based**: based on the idea that only the source knowledge reference should entail the entirety of the information in faithful and hallucination-free generation.

[A Survey of Hallucination in “Large” Foundation Models](https://arxiv.org/abs/2309.05922) surveys papers flagging them for *detection*, *mitigation*, *tasks*, *datasets*, and *evaluation metrics*. Regarding hallucinations in text, it categorises papers by *LLMs*, *Multilingual LLMs*, and *Domain-specific LLMs*.

[The Dawn After the Dark: An Empirical Study on Factuality Hallucination in Large Language Models](https://arxiv.org/abs/2401.03205) proposed a taxonomy of different types of hallucinations: Entity-error Hallucination, Relation-error Hallucination, Incompleteness Hallucination, Outdatedness Hallucination, Overclaim Hallucination, Unverifiability Hallucination.

[Internal Consistency and Self-Feedback in Large Language Models: A Survey](https://arxiv.org/abs/2407.14507) proposed a new perspective, **Internal Consistency**, to approach "enhancing reasoning" and ""alleviating hallucinations". This perspective allowed us to unify many seemingly unrelated works into a single framework. To improve internal consistency (which in turn enhances reasoning ability and mitigates hallucinations), this paper identified common elements across various works and summarized them into a Self-Feedback framework.

This framework consists of three components: Self-Evaluation, Internal Consistency Signal, and Self-Update.

- **Self-Evaluation**: Responsible for evaluating the model's internal consistency based on its language expressions, decoding layer probability distributions, and hidden states.
- **Internal Consistency Signal**: Through Self-Evaluation, we can obtain numerical, textual, external, and even comparative signals.
- **Self-Update**: Using these signals, we can update the model's expressions or even the model itself to improve internal consistency.

## Measuring Hallucinations in LLMs
- [AnyScale - Llama 2 is about as factually accurate as GPT-4 for summaries and is 30X cheaper](https://www.anyscale.com/blog/llama-2-is-about-as-factually-accurate-as-gpt-4-for-summaries-and-is-30x-cheaper)
- [Arthur.ai - Hallucination Experiment](https://www.arthur.ai/gap-articles/hallucination-experiment)
- [Vectara - Cut the Bull…. Detecting Hallucinations in Large Language Models](https://vectara.com/cut-the-bull-detecting-hallucinations-in-large-language-models/)
- [Vectara LLM Hallucination Leaderboard](https://github.com/vectara/hallucination-leaderboard)
- [TofuEval: Evaluating Hallucinations of LLMs on Topic-Focused Dialogue Summarization](https://arxiv.org/abs/2402.13249)
- [UQLM: Uncertainty Quantification for Language Models](https://github.com/cvs-health/uqlm)


## Open Source Models for Measuring Hallucinations
- [MiniCheck Code and Model - GitHub](https://github.com/Liyan06/MiniCheck)
- [AlignScore Code and Model - GitHub](https://github.com/yuh-zha/AlignScore)
- [Google True Teacher Model - HuggingFace](https://huggingface.co/google/t5_11b_trueteacher_and_anli)
- [Hallucination Evaluation Model - HuggingFace](https://huggingface.co/vectara/hallucination_evaluation_model)
- [Summac Code and Model - GitHub](https://github.com/tingofurro/summac)
- [SCALE Code and Model - GitHub](https://github.com/asappresearch/scale-score)

## Definitions and Notes

### Extrinsic and Intrinsic Hallucinations

[Neural Path Hunter](https://arxiv.org/abs/2104.08455) defines as *extrinsic hallucination* as an utterance that brings a new span of text that does not correspond
to a valid triple in a KG, and as *intrinsic hallucination* as an utterance that misuses either the subject or object in a KG triple such that there is no direct path between the two entities. [Survey of Hallucination in Natural Language Generation](https://arxiv.org/abs/2202.03629) defines as *extrinsic hallucination* a case where  the generated output that cannot be verified from the source content, and as an *intrinsic hallucination* a case where the generated output contradicts the source content.

## Citing this repository

```
@misc{MinerviniAHD2024,
  author = {Pasquale Minervini and Aryo Pradipta Gema and others},
  title = {awesome-hallucination-detection},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/EdinburghNLP/awesome-hallucination-detection}}
}
```
