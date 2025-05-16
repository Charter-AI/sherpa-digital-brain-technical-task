# Overview

Your task is to implement and optimise a RAG pipeline designed to give detailed insights on a small set of consulting reports from Bain, McKinsey & Company, and BCG. Each document will be complex and unstructured, containing a variety of text, charts and images. At the bottom of this page you will find some example queries with the data we expect to be returned by your system. (It may be the case that your solution easily handles the required queries, so we have added some optional queries designed to test more advanced submissions).

The overall goal is to improve retrieval and response accuracy using a search + retrieval + response pipeline.

Some technologies you may consider utilising for this are:

- LlamaIndex, CrewAI, AutoGen, or framework of choice
- Byaldi (ColPali)
- LangGraph
- OpenAI, Claude, or local models (optional)
- Anything else you can justify using

> Note: We recommend using a collab notebook with GPUs if possible, as this will reduce time spent waiting for embeddings to be calculated.
> 

# Requirements

## Necessary

PDF Parsing

- Extract text and structure
- Table and Chart parsing is optional but encouraged

Indexing

- Documents should be indexed and stored in some form of vector store
- Feel free to leverage custom metadata where necessary

Retrieval

- Given the set of queries provided, can you pull the expected top K chunks?

## Optional

Tool-calling

- Appropriate use of tool-calling / agents for query routing or other tasks

Multi-Modal RAG

- OCR + Layout Parsing for image extraction
- Vision Models

Evaluation Pipelines

- Which metrics could you use to evaluate model outputs?

Chat-like Interaction

- Does your solution support answering of user queries and follow-up questions without needing to re-fetch data?

# Deliverables

A GitHub repository or zipfile containing the following:

- Python source code `src/`
- `README.md` - README with setup/execution instructions
- `explanation.md` - Explanation of engineering choices
- Results file (CSV, JSON, txt, md are all acceptable)
    - The documents returned for each of the user queries with, ideally, a relevance score for each
    - If you added a response component, please include the model-generated response

# Assessment Criteria

| Area | Criteria |
| --- | --- |
| Data Ingestion | How effectively can your system extract data from the documents? |
| Indexing | What were you storing in your index, and why? |
| Retrieval Accuracy | How relevant were returned documents to the provided query? |
| Code Quality | Was the code well structured and clean? Could anyone run it easily? |
| Explanation | Can you justify your choices? |
| Time Management | What were you able to achieve in 4 hours? |

# Appendix

## Documents

We have provided a folder called `documents` with 3 consulting reports in pdf format.

1. **Bain Report** [`bain_report_luxury_and_technology_artificial_intelligence_the_quiet_revolution.pdf` ]
    1. A report by Bain & Company on the impact of AI on the luxury industry, mostly contains text but also some charts and diagrams.
2. **BCG Report** [`BCG-Executive-Perspectives-CEOs-Guide-to-Maximizing-Value-from-AI-EP0-3July2024.pdf` ]
    1. A slide deck by BCG on how executives should think about AI. Lots of text, but often in a complicated layout with many diagrams.
3. **McKinsey Report** [`what-every-ceo-should-know-about-generative-ai.pdf` ]
    1. A report by McKinsey on generative AI. Majority block text with a couple of diagrams and decorative images.

## Expected Results

Below is a table comparing a set of queries against the top K most relevant pages, which have been chosen by hand. The value of K is not fixed and can vary from query to query. If you disagree with our choices for the ideal returned pages, we are more than open to hearing your arguments.

### Required
Who at Bain & Company is an expert in the luxury sector?
- Bain Report - Page 2
  
What should executives do to use AI to transform their businesses?
- BCG Report - Page 5
- BCG Report - Page 18
- McKinsey report - Page 14
- McKinsey report - Page 9
- Bain Report - Page 38
  
Summarise Bain’s view on AI in the luxury industry	Bain Report - Page 4
- Bain Report - Page 6
  
What are the expected gains, boosts, and transformations of AI? Provide a numerical answer	BCG Report - Page 10
- BCG Report - Page 11
- BCG Report - Page 12
- Bain Report - Page 18
- Bain Report - Page 21
  
Find example case studies of AI being successfully used to transform a business	Bain Report - Page 11
- Bain Report - Page 23
- Bain Report - Page 35
- BCG Report - Page 11
- BCG Report - Page 12
  
When did Salesforce release Einstein GPT?
- McKinsey Report - Page 3

### Extensions

“What is the capital of France?”

- This should return no documents
- An ideal solution would either return no relevant documents, answer the query but never search the vector store to start with, or tell the user that the query is not relevant to it’s knowledge base

“!@£$%!@£$%^&*(”

- This query should be caught as invalid / gibberish, and it should be halted as early as possible

“Fetch me all documents from Amazon”

- The ideal solution would recognise that this is beyond the scope of the vector store’s knowledge
