# TAPI 2024 course: Text Classification with LLMs

This repo contains the notebooks I used to teach a 2024 [Text Analysis Pedagogy Institute](https://www.ithaka.org/constellate/text-analysis-pedagogy-institute/) course on text classification with LLMs.

## Description

In this course, you will learn the basics of using a large language model (specifically, ChatGPT) for text classification. Using the ChatGPT application programming interface (API), we will explore how LLMs can assist humanists with various text classification tasks (e.g., binary, labeling, applying confidence intervals to judgments, etc.). We will get to know the API, create validation data, engineer model prompts, and automate API calls for large data sets.

## Course Content

Each numbered notebook corresponds with one 90-minute class session. Sessions presume that participants are already familiar with Python and Jupyter Notebooks.

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

- Why classify texts?
- Good and bad of using LLMs for classification
- Advantages of using the API (computational traction, model parameters, etc.)

### Texts to classify

- Overview of sample data: one year of *Jeopardy!* questions somebody scraped from[J!-Archive](https://j-archive.com) and posted on GitHub ([source](https://github.com/amwagner19/jarchive-clues))
- Difficulty of classifying these questions using non-LLM methods: Short, dense, allusive, etc.
- Wide range of possible classification and extraction tasks possible
- We're going to do three classifications over the next two days:
  - Is this question about Topic A? `True` or `False`
  - Which of the following topics is this question about? Topics: History, Science, Literature, and Other
  - Bonus: If the question is about Topic Y, extract the following data from the question.
- If we're going to have an LLM classify these, we have to evaluate how the model performs.
  - To do that, we need testing data.

### Evaluating classifications

- An LLM hasn't failed if it isn't perfect. Human classifiers aren't perfect, either.
- Can the LLM approximate human classification?
  - If so, you can spend the time/money you would have spent labeling the data on correcting the LLM.
- Inter-annotator agreement: How much do we agree on these classifications?
- Creating human classification data as a class
  - Each get 50 random questions from the same set of 500ish. (You may look stuff up.)
  - Use Python user input to collect classification data and confidence intervals (e.g., "put `1` for `True` or `0` for `False`; express confidence as an integer between 50 and 100)
  - Then include a little script that `json` dumps  their classifications to their Desktop
  - They will receive a [Dropbox File Request](https://help.dropbox.com/share/create-file-request) email from me, where they can upload their classifications.
  - Load results as they come in, merge, and check for inter-annotator agreement
  - Look at high agreement questions and confidence
  - Look at low agreement questions and confidence
- Democratic evaluation of results: Classifications are votes
- Share created data

### Use the training data to identify the best prompt

- Intuitive metric: Total percentage of agreement
- Better metric: F-scores for binary classifications
  - Precision vs. recall
- Iterating the prompt; outputting F-score data
  - Save scores and prompts in a data frame or similar to freely sort by scores as you tweak
- Don't forget that tests have costs: A high-performing prompt may not be worth it if it runs on an expensive model. Classification tasks can often be accomplished on cheaper models (e.g., `gpt-3.5-turbo`)
- Once you have identified your best-performing prompt, it's time to run that prompt against the rest of the data, which we'll do on the final day.

## Day 3
