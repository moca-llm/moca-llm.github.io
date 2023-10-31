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
    - icon:
      content: Contact
      url: "mailto:moca.llm.help@gmail.com"

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

<h3>Chatd Models</h3>

<table style="display: inline-block;">
  <thead>
    <tr>
      <th>Organization</th>
      <th>Causal Judgment Task<br />Model</th>
      <th>AUC(↑)</th>
      <th>Agg(↑)</th>
      <th>MAE(↓)</th>
      <th>CE(↓)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class='has-border'>mistralai</td>
      <td class='has-border'>Mistral-7B-Instruct-v0.1</td>
      <td class='has-border'><b>0.63</b></td>
      <td>43.4</td>
      <td>0.26</td>
      <td>0.82</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT-4</td>
      <td>0.61</td>
      <td>43.1</td>
      <td>0.44</td>
      <td>1.89</td>
    </tr>
    <tr>
      <td>garage-bAInd</td>
      <td>Platypus2-70B-instruct</td>
      <td>0.59</td>
      <td>41.3</td>
      <td>0.45</td>
      <td>2.03</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>Anthropic-claude-v1</td>
      <td>0.57</td>
      <td>36.1</td>
      <td>0.34</td>
      <td>1.37</td>
    </tr>
    <tr>
      <td>HuggingFace</td>
      <td>starchat-alpha</td>
      <td>0.56</td>
      <td>35.8</td>
      <td>0.33</td>
      <td>1.35</td>
    </tr>
    <tr>
      <td>OpenOrca</td>
      <td>Mistral-7B-OpenOrca</td>
      <td>0.56</td>
      <td>34.7</td>
      <td>0.31</td>
      <td>1.18</td>
    </tr>
    <tr>
      <td>Meta</td>
      <td>llama-2-70b-chat</td>
      <td>0.54</td>
      <td>31.6</td>
      <td>0.31</td>
      <td>1.11</td>
    </tr>
    <tr>
      <td>Databricks</td>
      <td>dolly-v2-7b</td>
      <td>0.53</td>
      <td>35.4</td>
      <td>0.37</td>
      <td>1.59</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>vicuna-13b-v1.5-16k</td>
      <td>0.53</td>
      <td>37.8</td>
      <td>0.46</td>
      <td>2.09</td>
    </tr>
    <tr>
      <td>Tim Dettmers</td>
      <td>guanaco-13b</td>
      <td>0.52</td>
      <td>34.4</td>
      <td>0.42</td>
      <td>1.82</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>fastchat-t5-3b-v1.0</td>
      <td>0.52</td>
      <td>34.0</td>
      <td>0.46</td>
      <td>2.11</td>
    </tr>
    <tr>
      <td>Databricks</td>
      <td>dolly-v2-12b</td>
      <td>0.52</td>
      <td>33.7</td>
      <td>0.29</td>
      <td>1.12</td>
    </tr>
    <tr>
      <td>Austism</td>
      <td>chronos-hermes-13b</td>
      <td>0.52</td>
      <td>35.4</td>
      <td>0.48</td>
      <td>2.20</td>
    </tr>
    <tr>
      <td>Meta</td>
      <td>llama-2-13b-chat</td>
      <td>0.52</td>
      <td>34.0</td>
      <td>0.35</td>
      <td>1.39</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT3.5-turbo</td>
      <td>0.51</td>
      <td>35.4</td>
      <td>0.45</td>
      <td>2.11</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>Koala-13B</td>
      <td>0.51</td>
      <td>37.5</td>
      <td>0.40</td>
      <td>1.88</td>
    </tr>
    <tr>
      <td>Meta</td>
      <td>llama-2-7b-chat</td>
      <td>0.51</td>
      <td>31.6</td>
      <td>0.22</td>
      <td>0.58</td>
    </tr>
    <tr>
      <td>TII UAE</td>
      <td>falcon-7b-instruct</td>
      <td>0.50</td>
      <td>33.0</td>
      <td>0.35</td>
      <td>1.45</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>vicuna-13b-v1.5</td>
      <td>0.50</td>
      <td>34.7</td>
      <td>0.46</td>
      <td>2.16</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>RedPajama-7B-Chat</td>
      <td>0.50</td>
      <td>32.3</td>
      <td>0.35</td>
      <td>1.47</td>
    </tr>
    <tr>
      <td>Stanford</td>
      <td>alpaca-7b</td>
      <td>0.50</td>
      <td>34.0</td>
      <td>0.49</td>
      <td>2.37</td>
    </tr>
    <tr>
      <td>Databricks</td>
      <td>dolly-v2-3b</td>
      <td>0.50</td>
      <td>32.3</td>
      <td>0.24</td>
      <td>0.80</td>
    </tr>
    <tr>
      <td>Tim Dettmers</td>
      <td>guanaco-7b</td>
      <td>0.50</td>
      <td>33.3</td>
      <td>0.42</td>
      <td>1.86</td>
    </tr>
    <tr>
      <td>Mosaic ML</td>
      <td>mpt-7b-chat</td>
      <td>0.50</td>
      <td>31.2</td>
      <td>0.21</td>
      <td>0.58</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>vicuna-7b-v1.5</td>
      <td>0.49</td>
      <td>31.2</td>
      <td>0.20</td>
      <td>0.50</td>
    </tr>
    <tr>
      <td>TII UAE</td>
      <td>falcon-40b-instruct</td>
      <td>0.49</td>
      <td>31.9</td>
      <td>0.20</td>
      <td>0.50</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>GPT-NeoXT-Chat-20B</td>
      <td>0.49</td>
      <td>33.3</td>
      <td>0.36</td>
      <td>1.54</td>
    </tr>
    <tr>
      <td>Tim Dettmers</td>
      <td>guanaco-65b</td>
      <td>0.49</td>
      <td>33.0</td>
      <td>0.21</td>
      <td>0.61</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>RedPajama-Chat-3B-v1</td>
      <td>0.48</td>
      <td>31.9</td>
      <td>0.34</td>
      <td>1.31</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>Pythia-Chat-7B-v0.16</td>
      <td>0.48</td>
      <td>33.0</td>
      <td>0.49</td>
      <td>2.46</td>
    </tr>
    <tr>
      <td>Qwen</td>
      <td>Qwen-7B-Chat</td>
      <td>0.46</td>
      <td>28.8</td>
      <td>0.48</td>
      <td>2.35</td>
    </tr>
  </tbody>
</table>

<table style="display: inline-block; margin-left: 5px;">
  <thead>
    <tr>
      <th>Organization</th>
      <th>Moral Permissibility Task<br />Model</th>
      <th>AUC(↑)</th>
      <th>Agg(↑)</th>
      <th>MAE(↓)</th>
      <th>CE(↓)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class='has-border'>OpenAI</td>
      <td class='has-border'>GPT-4</td>
      <td class='has-border'><b>0.74</b></td>
      <td>41.9</td>
      <td>0.31</td>
      <td>1.28</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT3.5-turbo</td>
      <td>0.65</td>
      <td>40.3</td>
      <td>0.33</td>
      <td>1.49</td>
    </tr>
    <tr>
      <td>TII UAE</td>
      <td>falcon-7b-instruct</td>
      <td>0.64</td>
      <td>43.5</td>
      <td>0.29</td>
      <td>0.95</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>fastchat-t5-3b-v1.0</td>
      <td>0.62</td>
      <td>25.0</td>
      <td>0.48</td>
      <td>2.38</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>GPT-NeoXT-Chat-20B</td>
      <td>0.61</td>
      <td>36.3</td>
      <td>0.37</td>
      <td>1.45</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>Anthropic-claude-v1</td>
      <td>0.59</td>
      <td>37.1</td>
      <td>0.29</td>
      <td>1.29</td>
    </tr>
    <tr>
      <td>garage-bAInd</td>
      <td>Platypus2-70B-instruct</td>
      <td>0.57</td>
      <td>26.6</td>
      <td>0.41</td>
      <td>1.87</td>
    </tr>
    <tr>
      <td>OpenOrca</td>
      <td>Mistral-7B-OpenOrca</td>
      <td>0.56</td>
      <td>46.0</td>
      <td>0.26</td>
      <td>0.92</td>
    </tr>
    <tr>
      <td>Databricks</td>
      <td>dolly-v2-3b</td>
      <td>0.53</td>
      <td>44.4</td>
      <td>0.18</td>
      <td>0.49</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>RedPajama-7B-Chat</td>
      <td>0.53</td>
      <td>42.7</td>
      <td>0.21</td>
      <td>0.73</td>
    </tr>
    <tr>
      <td>Meta</td>
      <td>llama-2-7b-chat</td>
      <td>0.53</td>
      <td>47.6</td>
      <td>0.16</td>
      <td>0.45</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>RedPajama-Chat-3B-v1</td>
      <td>0.52</td>
      <td>39.5</td>
      <td>0.28</td>
      <td>0.96</td>
    </tr>
    <tr>
      <td>Tim Dettmers</td>
      <td>guanaco-13b</td>
      <td>0.52</td>
      <td>34.7</td>
      <td>0.28</td>
      <td>1.09</td>
    </tr>
    <tr>
      <td>Databricks</td>
      <td>dolly-v2-7b</td>
      <td>0.52</td>
      <td>33.9</td>
      <td>0.39</td>
      <td>1.49</td>
    </tr>
    <tr>
      <td>HuggingFace</td>
      <td>starchat-alpha</td>
      <td>0.52</td>
      <td>37.9</td>
      <td>0.31</td>
      <td>1.28</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>vicuna-13b-v1.5</td>
      <td>0.52</td>
      <td>38.7</td>
      <td>0.36</td>
      <td>1.53</td>
    </tr>
    <tr>
      <td>mistralai</td>
      <td>Mistral-7B-Instruct-v0.1</td>
      <td>0.52</td>
      <td>37.1</td>
      <td>0.27</td>
      <td>1.12</td>
    </tr>
    <tr>
      <td>Meta</td>
      <td>llama-2-70b-chat</td>
      <td>0.51</td>
      <td>46.8</td>
      <td>0.17</td>
      <td>0.51</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>Koala-13B</td>
      <td>0.51</td>
      <td>38.7</td>
      <td>0.35</td>
      <td>1.46</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>vicuna-13b-v1.5-16k</td>
      <td>0.51</td>
      <td>20.2</td>
      <td>0.52</td>
      <td>2.80</td>
    </tr>
    <tr>
      <td>Tim Dettmers</td>
      <td>guanaco-7b</td>
      <td>0.51</td>
      <td>41.1</td>
      <td>0.26</td>
      <td>1.11</td>
    </tr>
    <tr>
      <td>Stanford</td>
      <td>alpaca-7b</td>
      <td>0.50</td>
      <td>30.6</td>
      <td>0.48</td>
      <td>1.99</td>
    </tr>
    <tr>
      <td>Mosaic ML</td>
      <td>mpt-7b-chat</td>
      <td>0.50</td>
      <td>46.8</td>
      <td>0.16</td>
      <td>0.45</td>
    </tr>
    <tr>
      <td>LM Sys</td>
      <td>vicuna-7b-v1.5</td>
      <td>0.50</td>
      <td>45.2</td>
      <td>0.16</td>
      <td>0.48</td>
    </tr>
    <tr>
      <td>TII UAE</td>
      <td>falcon-40b-instruct</td>
      <td>0.50</td>
      <td>46.8</td>
      <td>0.16</td>
      <td>0.45</td>
    </tr>
    <tr>
      <td>Qwen</td>
      <td>Qwen-7B-Chat</td>
      <td>0.50</td>
      <td>25.0</td>
      <td>0.45</td>
      <td>2.37</td>
    </tr>
    <tr>
      <td>Databricks</td>
      <td>dolly-v2-12b</td>
      <td>0.48</td>
      <td>38.7</td>
      <td>0.26</td>
      <td>1.02</td>
    </tr>
    <tr>
      <td>Tim Dettmers</td>
      <td>guanaco-65b</td>
      <td>0.48</td>
      <td>42.7</td>
      <td>0.20</td>
      <td>0.77</td>
    </tr>
    <tr>
      <td>Austism</td>
      <td>chronos-hermes-13b</td>
      <td>0.47</td>
      <td>25.8</td>
      <td>0.48</td>
      <td>2.51</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>Pythia-Chat-7B-v0.16</td>
      <td>0.45</td>
      <td>24.2</td>
      <td>0.52</td>
      <td>2.54</td>
    </tr>
    <tr>
      <td>Meta</td>
      <td>llama-2-13b-chat</td>
      <td>0.42</td>
      <td>39.5</td>
      <td>0.25</td>
      <td>1.05</td>
    </tr>
  </tbody>
</table>

<h3>Completion-based Models</h3>

<table style="display: inline-block;">
  <thead>
    <tr>
      <th>Organization</th>
      <th>Causal Judgment Task<br />Model</th>
      <th>AUC(↑)</th>
      <th>Agg(↑)</th>
      <th>MAE(↓)</th>
      <th>CE(↓)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class='has-border'>OpenAI</td>
      <td class='has-border'>GPT3.5-davinci-v3</td>
      <td class='has-border'><b>0.67</b></td>
      <td>41.3</td>
      <td>0.41</td>
      <td>1.39</td>
    </tr>
    <tr>
      <td>WizardLM</td>
      <td>WizardLM-70B-V1.0</td>
      <td>0.62</td>
      <td>40.3</td>
      <td>0.43</td>
      <td>1.94</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT3.5-davinci-v2</td>
      <td>0.61</td>
      <td>37.8</td>
      <td>0.31</td>
      <td>0.72</td>
    </tr>
    <tr>
      <td>Mosaic ML</td>
      <td>mpt-30b-instruct</td>
      <td>0.56</td>
      <td>35.1</td>
      <td>0.34</td>
      <td>1.37</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>LLaMA-2-7B-32K</td>
      <td>0.52</td>
      <td>36.1</td>
      <td>0.49</td>
      <td>2.28</td>
    </tr>
    <tr>
      <td>EleutherAI</td>
      <td>pythia-12b-v0</td>
      <td>0.52</td>
      <td>34.7</td>
      <td>0.37</td>
      <td>1.53</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT3-curie-v1</td>
      <td>0.51</td>
      <td>36.8</td>
      <td>0.37</td>
      <td>1.14</td>
    </tr>
    <tr>
      <td>EleutherAI</td>
      <td>pythia-2.8b-v0</td>
      <td>0.51</td>
      <td>31.9</td>
      <td>0.40</td>
      <td>1.73</td>
    </tr>
    <tr>
      <td>EleutherAI</td>
      <td>pythia-6.9b</td>
      <td>0.51</td>
      <td>34.4</td>
      <td>0.36</td>
      <td>1.49</td>
    </tr>
    <tr>
      <td>TII UAE</td>
      <td>falcon-7b</td>
      <td>0.49</td>
      <td>31.6</td>
      <td>0.47</td>
      <td>2.20</td>
    </tr>
    <tr>
      <td>Qwen</td>
      <td>Qwen-7B</td>
      <td>0.48</td>
      <td>33.0</td>
      <td>0.51</td>
      <td>2.46</td>
    </tr>
    <tr>
      <td>mistralai</td>
      <td>Mistral-7B-v0.1</td>
      <td>0.48</td>
      <td>30.2</td>
      <td>0.30</td>
      <td>1.12</td>
    </tr>
    <tr>
      <td>TII UAE</td>
      <td>falcon-40b</td>
      <td>0.48</td>
      <td>33.0</td>
      <td>0.45</td>
      <td>2.17</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT3-babbage-v1</td>
      <td>0.47</td>
      <td>31.2</td>
      <td>0.33</td>
      <td>0.74</td>
    </tr>
    <tr>
      <td>Mosaic ML</td>
      <td>mpt-30b</td>
      <td>0.45</td>
      <td>31.6</td>
      <td>0.26</td>
      <td>0.90</td>
    </tr>
  </tbody>
</table>

<table style="display: inline-block; margin-left: 5px;">
  <thead>
    <tr>
      <th>Organization</th>
      <th>Moral Permissibility Task<br />Model</th>
      <th>AUC(↑)</th>
      <th>Agg(↑)</th>
      <th>MAE(↓)</th>
      <th>CE(↓)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class='has-border'>OpenAI</td>
      <td class='has-border'>GPT3.5-davinci-v2</td>
      <td class='has-border'><b>0.67</b></td>
      <td>32.3</td>
      <td>0.30</td>
      <td>0.74</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT3.5-davinci-v3</td>
      <td>0.61</td>
      <td>20.2</td>
      <td>0.51</td>
      <td>2.61</td>
    </tr>
    <tr>
      <td>Mosaic ML</td>
      <td>mpt-30b-instruct</td>
      <td>0.60</td>
      <td>39.5</td>
      <td>0.31</td>
      <td>1.26</td>
    </tr>
    <tr>
      <td>EleutherAI</td>
      <td>pythia-2.8b-v0</td>
      <td>0.58</td>
      <td>37.1</td>
      <td>0.35</td>
      <td>1.25</td>
    </tr>
    <tr>
      <td>EleutherAI</td>
      <td>pythia-12b-v0</td>
      <td>0.57</td>
      <td>28.2</td>
      <td>0.36</td>
      <td>1.53</td>
    </tr>
    <tr>
      <td>TII UAE</td>
      <td>falcon-40b</td>
      <td>0.55</td>
      <td>35.5</td>
      <td>0.35</td>
      <td>1.31</td>
    </tr>
    <tr>
      <td>WizardLM</td>
      <td>WizardLM-70B-V1.0</td>
      <td>0.55</td>
      <td>36.3</td>
      <td>0.35</td>
      <td>1.69</td>
    </tr>
    <tr>
      <td>Mosaic ML</td>
      <td>mpt-30b</td>
      <td>0.55</td>
      <td>46.0</td>
      <td>0.19</td>
      <td>0.57</td>
    </tr>
    <tr>
      <td>Together</td>
      <td>LLaMA-2-7B-32K</td>
      <td>0.52</td>
      <td>25.0</td>
      <td>0.50</td>
      <td>2.25</td>
    </tr>
    <tr>
      <td>EleutherAI</td>
      <td>pythia-6.9b</td>
      <td>0.51</td>
      <td>34.7</td>
      <td>0.33</td>
      <td>1.63</td>
    </tr>
    <tr>
      <td>Qwen</td>
      <td>Qwen-7B</td>
      <td>0.49</td>
      <td>27.4</td>
      <td>0.47</td>
      <td>2.17</td>
    </tr>
    <tr>
      <td>TII UAE</td>
      <td>falcon-7b</td>
      <td>0.48</td>
      <td>32.3</td>
      <td>0.35</td>
      <td>1.29</td>
    </tr>
    <tr>
      <td>mistralai</td>
      <td>Mistral-7B-v0.1</td>
      <td>0.47</td>
      <td>45.2</td>
      <td>0.23</td>
      <td>0.75</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT3-curie-v1</td>
      <td>0.45</td>
      <td>26.6</td>
      <td>0.39</td>
      <td>1.32</td>
    </tr>
    <tr>
      <td>OpenAI</td>
      <td>GPT3-babbage-v1</td>
      <td>0.43</td>
      <td>18.5</td>
      <td>0.41</td>
      <td>1.03</td>
    </tr>
  </tbody>
</table>

## Implicit Alignment

Check out the implicit tendencies of LLMs and how they compare to human tendencies.