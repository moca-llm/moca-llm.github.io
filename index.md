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
    title_url: ""
    indicator: 1
    column: 2
  - title: Atharva Amdekar
    title_url: ""
    indicator: 2
    column: 3

senior_authors:
  - title: Chris Piech
    title_url: "https://anie.me/"
    indicator: 1
    column: 1.5
  - title: Tatsu H. Hashimoto
    title_url: ""
    indicator: 1
    column: 3
  - title: Tobias Gerstenberg
    title_url: ""
    indicator: 3
    column: 3

# Grid navigation
grid_navigation:
    - title: Abstract/Task
      excerpt: Overview of task and stories in the dataset
      cta: Read more
      url: '#'
    - title: Main Result
      excerpt: Aggregate-level alignment of LLM models with Human
      cta: Read more
      url: '#'
    - title: Implicit Alignment
      excerpt: The analysis over the implicit tendencies of LLMs and their alignment with human tendencies
      cta: Read more
      url: '#'
---

## Abstract

Human commonsense understanding of the physical and social world is organized around intuitive theories. These theories support making causal and moral judgments. When something bad happens, we naturally ask: who did what, and why? A rich literature in cognitive science has studied people's causal and moral intuitions. This work has revealed a number of factors that systematically influence people's judgments, such as the violation of norms and whether the harm is avoidable or inevitable. We collected a dataset of stories from 24 cognitive science papers and developed a system to annotate each story with the factors they investigated. Using this dataset, we test whether large language models (LLMs) make causal and moral judgments about text-based scenarios that align with those of human participants. On the aggregate level, alignment has improved with more recent LLMs. However, using statistical analyses, we find that LLMs weigh the different factors quite differently from human participants. These results show how curated, challenge datasets combined with insights from cognitive science can help us go beyond comparisons based merely on aggregate metrics: we uncover LLMs implicit tendencies and show to what extent these align with human intuitions.

## Task

![](./images/data_example.png)
**Two examples from our collected dataset.** (a) shows a causal judgment story, and (b) shows a moral judgment story. In (a), a conjunction of two events was required, an abnormal event occurred, and Jane violated a prescriptive norm (scenario taken from Knobe & Fraser, 2008). In (b), the teenager’s death was inevitable; his death is a necessary means to save others, and bringing about his death requires the use of personal force (scenario taken from Christensen et al., 2014).

![](./images/data_dist.png)
**Dataset:** We report dataset statistics on the label distribution, average length of each story, and inter-rater agreement between two annotators on the factors and the sentences they highlight. Additionally, we collect a binary response for each story from 25 people.


## Main Result

| ID  | Name          | Age | Occupation     |
|-----|---------------|-----|----------------|
| 1   | John Doe      | 28  | Software Engineer |
| 2   | Jane Doe      | 25  | Data Scientist |
| 3   | Sam Smith     | 32  | Product Manager |
| 4   | Emily Johnson | 29  | Graphic Designer |

## Implicit Alignment

![](./images/factor.png)
**Factors:** Factors that influence causal selection judgments (top) and moral permissibility judgments (bottom). We provide definitions for each factor in Appendix A.1 and Appendix A.2. See the full version in Table A1.