# TAPI 2024 course: Text Classification with LLMs

This repo contains the notebooks I used to teach a 2024 [Text Analysis Pedagogy Institute](https://www.ithaka.org/constellate/text-analysis-pedagogy-institute/) course on text classification with LLMs.

## Description

In this course, you will learn the basics of using a large language model (specifically, ChatGPT) for text classification. Using the ChatGPT application programming interface (API), we will explore how LLMs can assist humans (and humanists) with various text classification tasks (e.g., binary, labeling, applying confidence intervals to judgments, etc.). We will get to know the API, create validation data, engineer prompts, and automate API calls for large data sets.

## Course Content

Each numbered notebook corresponds with one 90-minute class session.

Sessions presume that participants are already familiar with [Python](https://www.python.org), [Jupyter Notebooks](https://jupyter.org), and [`pandas`](https://pandas.pydata.org).

## Lesson 1

### Why classify texts?

- What is text classification?
- Why is text classification useful?
- LLMs: The good, the bad, and the ugly

### Technical introduction

- Overview of LLMs in general
- Distinction between ChatGPT on the website and the API
- Overview of APIs generally and ChatGPT's API specifically
- Overview of JSON and `response_format={ "type": "json_object" }`

### API Costs

- How to calculate the cost of a job
- [How to get an API key](https://help.openai.com/en/articles/7039783-how-can-i-access-the-chatgpt-api)
- [Pricing](https://openai.com/api/pricing/) by model, input, and output
- [Batch API](https://platform.openai.com/docs/guides/batch/batch-api) reduces costs by **50%**

## Lesson 2

### Review Lesson 1

- Why classify texts?
- LLMs: The good, the bad, and the ugly
- Advantages of the API: automation, hidden options, structured output

### Texts to classify

- Sample data: 500 random *Jeopardy!* questions somebody scraped from [J!-Archive](https://j-archive.com) and [posted on GitHub](https://github.com/amwagner19/jarchive-clues)

### Overview of text classification types

- binary, multi-class, multi-label, hierarchical, ordinal

### Evaluating LLM classifications

- How well can the LLM approximate human classification?
- Gold-standard data
- [Inter-rater reliability](https://en.wikipedia.org/wiki/Inter-rater_reliability)
- Measuring Human-LLM agreement
- Precision, recall, and F-score

### Quantifying model uncertainty

- Outputting confidence intervals via JSON
- Using `logprobs` to output classification token probabilities

## Lesson 3

### Dealing with limits and estimating total cost

- Before doing a bigger run, you should calculate how much it will cost.
- And you can estimate how long it will take based on rate limits.
- If the cost is high and you can wait 24 hours for results, use the [Batch API](https://platform.openai.com/docs/guides/batch/batch-api).
- Both have [limits](https://platform.openai.com/docs/guides/rate-limits/usage-tiers), which change based on how much you spend on the API
- Limit factors include total number of requests per minute, tokens per minute, requests per day, and how many tokens you can have queued to be processed in batches.
- Use `tiktoken` to count tokens in prompts, and estimate total input and output tokens.

### Running classifications

- Iterate through quetsions
- Extract data from JSON
- Count results in data frame
- Look at random sample of positive associations
- Bear in mind the expected error rate as compared to the testing data

### Check result vs. predicted result

- Based on the sample data, what percentage of questions would we expect to be about literature (~18%)?
- What do the model run results show?
- Sanity check some high confidence and low confidence results
- Check for correspondence between model confidence and accuracy

### What do we do with classifications once we have them?

- Read them!
- Use the classification results as evidence
- Use that subset of data to extract additional data
- Perform additional classification or labeling steps (e.g., sub-classifications)
- Extrude data (e.g., authors and texts from questions about literature)
