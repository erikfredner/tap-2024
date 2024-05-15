# TAPI 2024 course: Text Classification with LLMs

This repo contains the notebooks I used to teach a 2024 [Text Analysis Pedagogy Institute](https://www.ithaka.org/constellate/text-analysis-pedagogy-institute/) course on text classification with LLMs.

## Description

In this course, you will learn the basics of using a large language model (specifically, ChatGPT) for text classification. Using the ChatGPT application programming interface (API), we will explore how LLMs can assist humanists with various text classification tasks (e.g., binary, labeling, applying confidence intervals to judgments, etc.). We will get to know the API, create validation data, engineer model prompts, and automate API calls for large data sets.

## Content

Each numbered notebook corresponds with one 90-minute class session. Sessions presume that participants are already familiar with Python.

## Day 1

### Why bother with text classification?

- What is text classification?
- Why is text classification useful?
  - Sentiment analysis and high-frequency trading
  - Bayesian analysis of token probabilities in spam vs. non-spam email
- Why might text classification be useful for scholarship?
  - Sifting unreadably large corpora
  - Identify candidates for data extraction
  - Determining relative frequencies of text classes in a corpus
  - Prioritize research tasks for human labor vs. automation
- Why are LLMs useful for text classification?
- What are the limitations of LLMs for text classification?

### Technical introduction

- Overview of LLMs generally and ChatGPT specifically
- Distinction between ChatGPT on the website and the API
- Overview of APIs generally and ChatGPT's specifically
- Overview of JSON
  - Similarity to Python dictionaries
  - Demonstration of [`json`](https://docs.python.org/3/library/json.html#module-json) module
- [Prompt engineering](https://platform.openai.com/docs/guides/prompt-engineering/prompt-engineering) for text classification
  - Example prompts: [Tweets and Reviews](https://platform.openai.com/examples/default-tweet-classifier)

### API Costs

- Distribution and explanation of class API key
  - [How to get own API key](https://help.openai.com/en/articles/7039783-how-can-i-access-the-chatgpt-api)
- [Pricing](https://openai.com/api/pricing/) by model, input, and output
  - Cheap models can classify well!
- [Batch API](https://platform.openai.com/docs/guides/batch/batch-api)

### Setting up

- Set up `client` and pass a test prompt
- [Chat completion](https://platform.openai.com/docs/api-reference/chat/create) structure
  - `role`: `system` vs. `user`
- Discuss selected model parameters: `model`, `n`, `response_format`, `temperature`,`top_p`, `max_tokens`
- `print` messages from dummy completion

### Play

- Write an original prompt
- Get the result
- Tweak model parameters
- Get a sense of how results change

## Day 2

### Review

### Texts to classify

- Overview of sample data: one year of *Jeopardy!* questions ([source](https://github.com/amwagner19/jarchive-clues))
