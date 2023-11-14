---
# Page settings
layout: homepage
keywords:

# Hero section
title: "MoCa: Measuring Human-Language Model Alignment on Causal and Moral Judgment Tasks"
description: NeurIPS 2023
buttons:
    - content: Paper
      url: 'https://arxiv.org/abs/2310.19677'
      external_url: true
    - icon: github
      content: Code
      url: 'https://github.com/cicl-stanford/moca'
      external_url: true
    - icon:
      content: Contact
      url: "mailto:moca.llm.help@gmail.com"

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
  - title: Tatsunori Hashimoto
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

## Intro

Humans rely on their intuition to understand the world. This intuition helps us to understand not only
physical events (e.g., one ball caused the other to move) but also complex social situations (e.g., the
collapse of Sam Bankman-Fried’s FTX caused unprecedented turmoil in the cryptocurrency market).
Given a complex set of events, even with a great amount of ambiguity, we can answer questions
such as “What or who caused it?” Our answers to this question reflect how we intuitively understand
events, people, and the world around us (Sloman & Lagnado, 2015; Pearl & Mackenzie, 2018). How
do humans handle this complexity?

Cognitive scientists have proposed that we do so by organizing our understanding of the world into
intuitive theories (Gerstenberg & Tenenbaum, 2017; Wellman & Gelman, 1992). Accordingly, people
have intuitive theories of the physical and social world with which we reason about how objects
and agents interact with one another (Battaglia et al., 2013; Ullman et al., 2017; Gerstenberg et al.,
2021; Baker et al., 2017; Davis & Marcus, 2015; Lake et al., 2017). Concepts related to causality and
morality form key ingredients of people’s physical and social theories. Given a story, humans can
readily make causal and moral judgments about the objects and agents involved in the story.
Studying these human **intuitions** or systematic **tendencies** when making decisions or judgments
is the central focus of psychological experimentations. What are these tendencies? How do they
influence our judgment? Over the last several decades, using text-based vignettes, psychologists
have disentangled what factors influence people’s causal and moral judgments. These factors can be
understood as the building blocks of our thought processes for making causal and moral judgments.

## Task

![](./images/data_example.png)
**Two examples from our collected dataset.** (a) shows a causal judgment story, and (b) shows a moral judgment story. In (a), a conjunction of two events was required, an abnormal event occurred, and Jane violated a prescriptive norm (scenario taken from Knobe & Fraser, 2008). In (b), the teenager’s death was inevitable; his death is a necessary means to save others, and bringing about his death requires the use of personal force (scenario taken from Christensen et al., 2014).

![](./images/data_dist.png)
**Dataset:** We report dataset statistics on the label distribution, average length of each story, and inter-rater agreement between two annotators on the factors and the sentences they highlight. Additionally, we collect a binary response for each story from **25 people**.

Each story is annotated with latent factors that can help us detect implicit tendencies from humans and LLMs.

![](./images/factor.png)
**Factors:** Factors that influence causal selection judgments (top) and moral permissibility judgments (bottom). We provide definitions for each factor in Appendix A.1 and Appendix A.2. See the full version in Table A1.

## Main Result

We conduct a 3-class comparison to compute accuracy: a response of "Yes", "No", and an additional response of "ambiguous" when the agreement between the average human responses or the probability of model output is 50% &plusmn; 10%. This gives us a discrete agreement (Agg) between the model and participants. We also report AuROC between the model's output and the distribution of human answering yes or no. Additionally, we report the absolute-mean-squared error (MAE) on the probability of the matched label.

We present both **Causal Judgment Task** (Left Table) and **Moral Permissibility Task** (Right Table), across chat-based LLMs and completion-based LLMs. We separate models into chat models and completion models. For chat models, the prompt asks the LLMs to choose one of three labels `Yes`, `No`, 

<h3>Chat Models</h3>

<table class="table-striped" style="display: inline-block;">
  <thead>
    <tr>
      <th>Causal Judgment Task<br />Model</th>
      <th>AUC(↑)</th>
      <th>Agg(↑)</th>
      <th>MAE(↓)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class='bold-text'>Mistral-7B-Instruct-v0.1</td>
      <td class="has-border">0.63</td>
      <td class="has-border">43.4</td>
      <td>0.26</td>
    </tr>
    <tr>
      <td>GPT-4</td>
      <td>0.61</td>
      <td>43.1</td>
      <td>0.44</td>
    </tr>
    <tr>
      <td>Platypus2-70B-instruct</td>
      <td>0.59</td>
      <td>41.3</td>
      <td>0.45</td>
    </tr>
    <tr>
      <td>Anthropic-claude-v1</td>
      <td>0.57</td>
      <td>36.1</td>
      <td>0.34</td>
    </tr>
    <tr>
      <td>starchat-alpha</td>
      <td>0.56</td>
      <td>35.8</td>
      <td>0.33</td>
    </tr>
    <tr>
      <td>Mistral-7B-OpenOrca</td>
      <td>0.56</td>
      <td>34.7</td>
      <td>0.31</td>
    </tr>
    <tr>
      <td>llama-2-70b-chat</td>
      <td>0.54</td>
      <td>31.6</td>
      <td>0.31</td>
    </tr>
    <tr>
      <td>dolly-v2-7b</td>
      <td>0.53</td>
      <td>35.4</td>
      <td>0.37</td>
    </tr>
    <tr>
      <td>vicuna-13b-v1.5-16k</td>
      <td>0.53</td>
      <td>37.8</td>
      <td>0.46</td>
    </tr>
    <tr>
      <td>guanaco-13b</td>
      <td>0.52</td>
      <td>34.4</td>
      <td>0.42</td>
    </tr>
    <tr>
      <td>fastchat-t5-3b-v1.0</td>
      <td>0.52</td>
      <td>34.0</td>
      <td>0.46</td>
    </tr>
    <tr>
      <td>dolly-v2-12b</td>
      <td>0.52</td>
      <td>33.7</td>
      <td>0.29</td>
    </tr>
    <tr>
      <td>chronos-hermes-13b</td>
      <td>0.52</td>
      <td>35.4</td>
      <td>0.48</td>
    </tr>
    <tr>
      <td>llama-2-13b-chat</td>
      <td>0.52</td>
      <td>34.0</td>
      <td>0.35</td>
    </tr>
    <tr>
      <td>GPT3.5-turbo</td>
      <td>0.51</td>
      <td>35.4</td>
      <td>0.45</td>
    </tr>
    <tr>
      <td>Koala-13B</td>
      <td>0.51</td>
      <td>37.5</td>
      <td>0.40</td>
    </tr>
    <tr>
      <td>llama-2-7b-chat</td>
      <td>0.51</td>
      <td>31.6</td>
      <td>0.22</td>
    </tr>
    <tr>
      <td>falcon-7b-instruct</td>
      <td>0.50</td>
      <td>33.0</td>
      <td>0.35</td>
    </tr>
    <tr>
      <td>vicuna-13b-v1.5</td>
      <td>0.50</td>
      <td>34.7</td>
      <td>0.46</td>
    </tr>
    <tr>
      <td>RedPajama-7B-Chat</td>
      <td>0.50</td>
      <td>32.3</td>
      <td>0.35</td>
    </tr>
    <tr>
      <td>alpaca-7b</td>
      <td>0.50</td>
      <td>34.0</td>
      <td>0.49</td>
    </tr>
    <tr>
      <td>dolly-v2-3b</td>
      <td>0.50</td>
      <td>32.3</td>
      <td>0.24</td>
    </tr>
    <tr>
      <td>guanaco-7b</td>
      <td>0.50</td>
      <td>33.3</td>
      <td>0.42</td>
    </tr>
    <tr>
      <td>mpt-7b-chat</td>
      <td>0.50</td>
      <td>31.2</td>
      <td>0.21</td>
    </tr>
    <tr>
      <td class='bold-text'>vicuna-7b-v1.5</td>
      <td>0.49</td>
      <td>31.2</td>
      <td class="has-border">0.20</td>
    </tr>
    <tr>
      <td class='bold-text'>falcon-40b-instruct</td>
      <td>0.49</td>
      <td>31.9</td>
      <td class="has-border">0.20</td>
    </tr>
    <tr>
      <td>GPT-NeoXT-Chat-20B</td>
      <td>0.49</td>
      <td>33.3</td>
      <td>0.36</td>
    </tr>
    <tr>
      <td>guanaco-65b</td>
      <td>0.49</td>
      <td>33.0</td>
      <td>0.21</td>
    </tr>
    <tr>
      <td>RedPajama-Chat-3B-v1</td>
      <td>0.48</td>
      <td>31.9</td>
      <td>0.34</td>
    </tr>
    <tr>
      <td>Pythia-Chat-7B-v0.16</td>
      <td>0.48</td>
      <td>33.0</td>
      <td>0.49</td>
    </tr>
    <tr>
      <td>Qwen-7B-Chat</td>
      <td>0.46</td>
      <td>28.8</td>
      <td>0.48</td>
    </tr>
  </tbody>
</table>

<table class="table-striped" style="display: inline-block; margin-left: 50px;">
  <thead>
    <tr>
      <th>Moral Permissibility Task<br />Model</th>
      <th>AUC(↑)</th>
      <th>Agg(↑)</th>
      <th>MAE(↓)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class='bold-text'>GPT-4</td>
      <td class="has-border">0.74</td>
      <td>41.9</td>
      <td>0.31</td>
    </tr>
    <tr>
      <td>GPT3.5-turbo</td>
      <td>0.65</td>
      <td>40.3</td>
      <td>0.33</td>
    </tr>
    <tr>
      <td>falcon-7b-instruct</td>
      <td>0.64</td>
      <td>43.5</td>
      <td>0.29</td>
    </tr>
    <tr>
      <td>fastchat-t5-3b-v1.0</td>
      <td>0.62</td>
      <td>25.0</td>
      <td>0.48</td>
    </tr>
    <tr>
      <td>GPT-NeoXT-Chat-20B</td>
      <td>0.61</td>
      <td>36.3</td>
      <td>0.37</td>
    </tr>
    <tr>
      <td>Anthropic-claude-v1</td>
      <td>0.59</td>
      <td>37.1</td>
      <td>0.29</td>
    </tr>
    <tr>
      <td>Platypus2-70B-instruct</td>
      <td>0.57</td>
      <td>26.6</td>
      <td>0.41</td>
    </tr>
    <tr>
      <td>Mistral-7B-OpenOrca</td>
      <td>0.56</td>
      <td>46.0</td>
      <td>0.26</td>
    </tr>
    <tr>
      <td>dolly-v2-3b</td>
      <td>0.53</td>
      <td>44.4</td>
      <td>0.18</td>
    </tr>
    <tr>
      <td>RedPajama-7B-Chat</td>
      <td>0.53</td>
      <td>42.7</td>
      <td>0.21</td>
    </tr>
    <tr>
      <td class='bold-text'>llama-2-7b-chat</td>
      <td>0.53</td>
      <td>47.6</td>
      <td class="has-border">0.16</td>
    </tr>
    <tr>
      <td>RedPajama-Chat-3B-v1</td>
      <td>0.52</td>
      <td>39.5</td>
      <td>0.28</td>
    </tr>
    <tr>
      <td>guanaco-13b</td>
      <td>0.52</td>
      <td>34.7</td>
      <td>0.28</td>
    </tr>
    <tr>
      <td>dolly-v2-7b</td>
      <td>0.52</td>
      <td>33.9</td>
      <td>0.39</td>
    </tr>
    <tr>
      <td>starchat-alpha</td>
      <td>0.52</td>
      <td>37.9</td>
      <td>0.31</td>
    </tr>
    <tr>
      <td>vicuna-13b-v1.5</td>
      <td>0.52</td>
      <td>38.7</td>
      <td>0.36</td>
    </tr>
    <tr>
      <td>Mistral-7B-Instruct-v0.1</td>
      <td>0.52</td>
      <td>37.1</td>
      <td>0.27</td>
    </tr>
    <tr>
      <td>llama-2-70b-chat</td>
      <td>0.51</td>
      <td>46.8</td>
      <td>0.17</td>
    </tr>
    <tr>
      <td>Koala-13B</td>
      <td>0.51</td>
      <td>38.7</td>
      <td>0.35</td>
    </tr>
    <tr>
      <td>vicuna-13b-v1.5-16k</td>
      <td>0.51</td>
      <td>20.2</td>
      <td>0.52</td>
    </tr>
    <tr>
      <td>guanaco-7b</td>
      <td>0.51</td>
      <td>41.1</td>
      <td>0.26</td>
    </tr>
    <tr>
      <td>alpaca-7b</td>
      <td>0.50</td>
      <td>30.6</td>
      <td>0.48</td>
    </tr>
    <tr>
      <td class='bold-text'>mpt-7b-chat</td>
      <td>0.50</td>
      <td class="has-border">46.8</td>
      <td class="has-border">0.16</td>
    </tr>
    <tr>
      <td class='bold-text'>vicuna-7b-v1.5</td>
      <td>0.50</td>
      <td>45.2</td>
      <td class="has-border">0.16</td>
    </tr>
    <tr>
      <td class='bold-text'>falcon-40b-instruct</td>
      <td>0.50</td>
      <td class="has-border">46.8</td>
      <td class="has-border">0.16</td>
    </tr>
    <tr>
      <td>Qwen-7B-Chat</td>
      <td>0.50</td>
      <td>25.0</td>
      <td>0.45</td>
    </tr>
    <tr>
      <td>dolly-v2-12b</td>
      <td>0.48</td>
      <td>38.7</td>
      <td>0.26</td>
    </tr>
    <tr>
      <td>guanaco-65b</td>
      <td>0.48</td>
      <td>42.7</td>
      <td>0.20</td>
    </tr>
    <tr>
      <td>chronos-hermes-13b</td>
      <td>0.47</td>
      <td>25.8</td>
      <td>0.48</td>
    </tr>
    <tr>
      <td>Pythia-Chat-7B-v0.16</td>
      <td>0.45</td>
      <td>24.2</td>
      <td>0.52</td>
    </tr>
    <tr>
      <td>llama-2-13b-chat</td>
      <td>0.42</td>
      <td>39.5</td>
      <td>0.25</td>
    </tr>
  </tbody>
</table>

<h3>Completion Models</h3>

<table class="table-striped" style="display: inline-block;">
  <thead>
    <tr>
      <th>Causal Judgment Task<br />Model</th>
      <th>AUC(↑)</th>
      <th>Agg(↑)</th>
      <th>MAE(↓)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class='bold-text'>GPT3.5-davinci-v3</td>
      <td class="has-border">0.67</td>
      <td class="has-border">41.3</td>
      <td>0.41</td>
    </tr>
    <tr>
      <td>WizardLM-70B-V1.0</td>
      <td>0.62</td>
      <td>40.3</td>
      <td>0.43</td>
    </tr>
    <tr>
      <td>GPT3.5-davinci-v2</td>
      <td>0.61</td>
      <td>37.8</td>
      <td>0.31</td>
    </tr>
    <tr>
      <td>mpt-30b-instruct</td>
      <td>0.56</td>
      <td>35.1</td>
      <td>0.34</td>
    </tr>
    <tr>
      <td>LLaMA-2-7B-32K</td>
      <td>0.52</td>
      <td>36.1</td>
      <td>0.49</td>
    </tr>
    <tr>
      <td>pythia-12b-v0</td>
      <td>0.52</td>
      <td>34.7</td>
      <td>0.37</td>
    </tr>
    <tr>
      <td>GPT3-curie-v1</td>
      <td>0.51</td>
      <td>36.8</td>
      <td>0.37</td>
    </tr>
    <tr>
      <td>pythia-2.8b-v0</td>
      <td>0.51</td>
      <td>31.9</td>
      <td>0.40</td>
    </tr>
    <tr>
      <td>pythia-6.9b</td>
      <td>0.51</td>
      <td>34.4</td>
      <td>0.36</td>
    </tr>
    <tr>
      <td>falcon-7b</td>
      <td>0.49</td>
      <td>31.6</td>
      <td>0.47</td>
    </tr>
    <tr>
      <td>Qwen-7B</td>
      <td>0.48</td>
      <td>33.0</td>
      <td>0.51</td>
    </tr>
    <tr>
      <td>Mistral-7B-v0.1</td>
      <td>0.48</td>
      <td>30.2</td>
      <td>0.30</td>
    </tr>
    <tr>
      <td>falcon-40b</td>
      <td>0.48</td>
      <td>33.0</td>
      <td>0.45</td>
    </tr>
    <tr>
      <td>GPT3-babbage-v1</td>
      <td>0.47</td>
      <td>31.2</td>
      <td>0.33</td>
    </tr>
    <tr>
      <td class='bold-text'>mpt-30b</td>
      <td>0.45</td>
      <td>31.6</td>
      <td class="has-border">0.26</td>
    </tr>
  </tbody>
</table>

<table class="table-striped" style="display: inline-block; margin-left: 50px;">
  <thead>
    <tr>
      <th>Moral Permissibility Task<br />Model</th>
      <th>AUC(↑)</th>
      <th>Agg(↑)</th>
      <th>MAE(↓)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class='bold-text'>GPT3.5-davinci-v2</td>
      <td class="has-border">0.67</td>
      <td>32.3</td>
      <td>0.30</td>
    </tr>
    <tr>
      <td>GPT3.5-davinci-v3</td>
      <td>0.61</td>
      <td>20.2</td>
      <td>0.51</td>
    </tr>
    <tr>
      <td>mpt-30b-instruct</td>
      <td>0.60</td>
      <td>39.5</td>
      <td>0.31</td>
    </tr>
    <tr>
      <td>pythia-2.8b-v0</td>
      <td>0.58</td>
      <td>37.1</td>
      <td>0.35</td>
    </tr>
    <tr>
      <td>pythia-12b-v0</td>
      <td>0.57</td>
      <td>28.2</td>
      <td>0.36</td>
    </tr>
    <tr>
      <td>falcon-40b</td>
      <td>0.55</td>
      <td>35.5</td>
      <td>0.35</td>
    </tr>
    <tr>
      <td>WizardLM-70B-V1.0</td>
      <td>0.55</td>
      <td>36.3</td>
      <td>0.35</td>
    </tr>
    <tr>
      <td class='bold-text'>mpt-30b</td>
      <td>0.55</td>
      <td class="has-border">46.0</td>
      <td class="has-border">0.19</td>
    </tr>
    <tr>
      <td>LLaMA-2-7B-32K</td>
      <td>0.52</td>
      <td>25.0</td>
      <td>0.50</td>
    </tr>
    <tr>
      <td>pythia-6.9b</td>
      <td>0.51</td>
      <td>34.7</td>
      <td>0.33</td>
    </tr>
    <tr>
      <td>Qwen-7B</td>
      <td>0.49</td>
      <td>27.4</td>
      <td>0.47</td>
    </tr>
    <tr>
      <td>falcon-7b</td>
      <td>0.48</td>
      <td>32.3</td>
      <td>0.35</td>
    </tr>
    <tr>
      <td>Mistral-7B-v0.1</td>
      <td>0.47</td>
      <td>45.2</td>
      <td>0.23</td>
    </tr>
    <tr>
      <td>GPT3-curie-v1</td>
      <td>0.45</td>
      <td>26.6</td>
      <td>0.39</td>
    </tr>
    <tr>
      <td>GPT3-babbage-v1</td>
      <td>0.43</td>
      <td>18.5</td>
      <td>0.41</td>
    </tr>
  </tbody>
</table>

## Implicit Alignment

In the previous section, we focus on analyzing aggregate metrics such as agreement over all stories. Such analysis often provides no information beyond comparing highly complicated systems with a single number. 
Since each of our stories is a combination of factors with corresponding attributes, we can leverage conjoint analysis and compute the Average Marginal Component Effect (AMCE) for each factor attribute, where AMCE reveals the implicit tendency of the underlying system when a particular attribute is present.

AMCE computes a score that indicates an **implicit preference**. We put the attributes of the same factor (e.g., Abnormal and Normal are the two attributes under factor "Event Normality") on opposite sides -- since the preference is over one attribute or the other. Each concentric circle is marked with a probability (e.g., 0.1), which represents the change in `P(Yes)` if the factor attribute had been present in the story. The implicit tendency is defined as the expected change in the probability of the system outputting `Yes` if this attribute had been present in the story.  Intuitively, we can say a model has an implicit tendency for one attribute when it’s more likely to judge an event to be the cause, or the impending harm to be more morally permissible, if this attribute is present.

The radar plot shows not just the mean AMCE score, but the 95% confidence interval of the AMCE score. Since AMCE score is the difference in probability change, if the upper/lower bound of confidence interval crosses 0, it means we are not able to determine the tendency given the current data. The confidence interval is computed through Bootstrap.