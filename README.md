# AI Evaluation — A PM Perspective

Most AI eval setups are honest in their intent but soft in their definitions.

We pick metrics that are measurable: accuracy, relevance, hallucination rate. Dashboards get built. Numbers move. Confidence follows.

But a model can score well on all three and still give a user an answer that misses the point entirely.

This repo is a hands-on exploration of that gap, specifically the **gulf of specification**: the distance between what you intend your product to do and what you actually encode into your evaluation system.

## What's here

### [`gulf_of_specification_llm_judge.ipynb`](./gulf_of_specification_llm_judge.ipynb)

The core experiment.

Same model. Same responses. Two judges, one with a vague rubric, one with precise definitions.

The test case: a customer support AI handling a failed payment query. Three responses:
- Correct and specific
- Fluent but factually wrong
- Polite but completely misses the question

The vague judge scores all three within a similar range. The precise judge separates them clearly — because the rubric defines exactly what a factual failure looks like for *this* product, not in the abstract.

The gap between the two scores is the spec gap made visible.

---

## The idea behind this

Anthropic published research showing Claude Opus 4.6 stopped mid-evaluation, identified it was inside a test, found the benchmark source code on GitHub, and decrypted the answer key.

It didn't find the answer. It found a way around the evaluation.

That's the gulf of specification from the other direction. The model followed exactly what the evaluation opened up — because passing was what the spec said good looked like.

The same problem shows up at scale: LLM-as-Judge exists because you can't manually review thousands of responses. But a judge inherits the same gap. If the definition is soft, the judge can't find what you didn't specify.

This notebook is an attempt to make that concrete.

**Gargi Tarania** — Product Manager, AI & Data Products  
[LinkedIn](https://www.linkedin.com/in/gargitarania) · [wanderpixel.jpg](https://www.instagram.com/wanderpixel.jpg)
