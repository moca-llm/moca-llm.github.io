---
# Page settings
layout: homepage
keywords:

# Hero section
title: "MoCa: Measuring Human-Language Model Alignment on Causal and Moral Judgment Tasks"
description: NeurIPS 2023
buttons:
    - content: Paper
      url: '#'
      external_url: true
    - icon: github
      content: Code
      url: '#'
      external_url: true

# Author box
# author:
#     title: Allen Nie
#     title_url: "https://anie.me/"
#     external_url: true
#     indicator: 1
    
authors:
  - title: Allen Nie
    title_url: "https://anie.me/"
    indicator: 1
    column: 2
  - title: Yuhui Zhang
    title_url: "https://cs.stanford.edu/~yuhuiz/"
    indicator: 1
    column: 2
  - title: Atharva Amdekar
    title_url: ""
    indicator: 2
    column: 3

senior_authors:
  - title: Chris Piech
    title_url: "https://stanford.edu/~cpiech/bio/index.html"
    indicator: 1
    column: 1.5
  - title: Tatsu H. Hashimoto
    title_url: "https://thashim.github.io/"
    indicator: 1
    column: 3
  - title: Tobias Gerstenberg
    title_url: "https://cicl.stanford.edu/member/tobias_gerstenberg/"
    indicator: 3
    column: 3

# Grid navigation
grid_navigation:
    - title: Abstract/Task
      excerpt: Overview of task and stories in the dataset
      cta: Read more
      url: '#abstract'
    - title: Main Result
      excerpt: Aggregate-level alignment of LLM models with Human
      cta: Read more
      url: '#main-result'
    - title: Implicit Alignment
      excerpt: The analysis over the implicit tendencies of LLMs and their alignment with human tendencies
      cta: Read more
      url: '#implicit-alignment'
---

## Abstract

Human commonsense understanding of the physical and social world is organized around intuitive theories. These theories support making causal and moral judgments. When something bad happens, we naturally ask: who did what, and why? A rich literature in cognitive science has studied people's causal and moral intuitions. This work has revealed a number of factors that systematically influence people's judgments, such as the violation of norms and whether the harm is avoidable or inevitable. We collected a dataset of stories from 24 cognitive science papers and developed a system to annotate each story with the factors they investigated. Using this dataset, we test whether large language models (LLMs) make causal and moral judgments about text-based scenarios that align with those of human participants. On the aggregate level, alignment has improved with more recent LLMs. However, using statistical analyses, we find that LLMs weigh the different factors quite differently from human participants. These results show how curated, challenge datasets combined with insights from cognitive science can help us go beyond comparisons based merely on aggregate metrics: we uncover LLMs implicit tendencies and show to what extent these align with human intuitions.

## Task

![](./images/data_example.png)
**Two examples from our collected dataset.** (a) shows a causal judgment story, and (b) shows a moral judgment story. In (a), a conjunction of two events was required, an abnormal event occurred, and Jane violated a prescriptive norm (scenario taken from Knobe & Fraser, 2008). In (b), the teenager’s death was inevitable; his death is a necessary means to save others, and bringing about his death requires the use of personal force (scenario taken from Christensen et al., 2014).

![](./images/data_dist.png)
**Dataset:** We report dataset statistics on the label distribution, average length of each story, and inter-rater agreement between two annotators on the factors and the sentences they highlight. Additionally, we collect a binary response for each story from 25 people.

Each story is annotated with latent factors that can help us detect implicit tendencies from humans and LLMs.

![](./images/factor.png)
**Factors:** Factors that influence causal selection judgments (top) and moral permissibility judgments (bottom). We provide definitions for each factor in Appendix A.1 and Appendix A.2. See the full version in Table A1.

## Main Result

|  Causal Judgment Task<br>Model | Agg (&uarr;)| AUC(&uarr;) | MAE(&darr;) | CE(&darr;) |
|---------------------------|----|----|----|----|
|  Mistral-7B-Instruct-v0.1 |43.4|0.63|0.26|0.82|
|   Platypus2-70B-instruct  |41.3|0.59|0.45|2.03|
|    vicuna-13b-v1.5-16k    |37.8|0.53|0.46|2.09|
|         Koala-13B         |37.5|0.51|0.40|1.88|
|       starchat-alpha      |35.8|0.56|0.33|1.35|
|     chronos-hermes-13b    |35.4|0.52|0.48|2.20|
|        dolly-v2-7b        |35.4|0.53|0.37|1.59|
|    Mistral-7B-OpenOrca    |34.7|0.56|0.31|1.18|
|      vicuna-13b-v1.5      |34.7|0.50|0.46|2.16|
|        guanaco-13b        |34.4|0.52|0.42|1.82|
|         alpaca-7b         |34.0|0.50|0.49|2.37|
|    fastchat-t5-3b-v1.0    |34.0|0.52|0.46|2.11|
|      llama-2-13b-chat     |34.0|0.52|0.35|1.39|
|        dolly-v2-12b       |33.7|0.52|0.29|1.12|
|  GPT-NeoXT-Chat-Base-20B  |33.3|0.49|0.36|1.54|
|         guanaco-7b        |33.3|0.50|0.42|1.86|
| Pythia-Chat-Base-7B-v0.16 |33.0|0.48|0.49|2.46|
|     falcon-7b-instruct    |33.0|0.50|0.35|1.45|
|        guanaco-65b        |33.0|0.49|0.21|0.61|
|  RedPajama-INCITE-7B-Chat |32.3|0.50|0.35|1.47|
|        dolly-v2-3b        |32.3|0.50|0.24|0.80|
|RedPajama-INCITE-Chat-3B-v1|31.9|0.48|0.34|1.31|
|    falcon-40b-instruct    |31.9|0.49|0.20|0.50|
|      llama-2-70b-chat     |31.6|0.54|0.31|1.11|
|      llama-2-7b-chat      |31.6|0.51|0.22|0.58|
|       vicuna-7b-v1.5      |31.2|0.49|0.20|0.50|
|        mpt-7b-chat        |31.2|0.50|0.21|0.58|
|        Qwen-7B-Chat       |28.8|0.46|0.48|2.35|



## Implicit Alignment

Check out the implicit tendencies of LLMs and how they compare to human tendencies.