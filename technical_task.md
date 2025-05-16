# Sherpa Technical Task

### Time Limit: ... hours

## Goal
Your goal is to build and optimise the retrieval component of a multi-modal RAG pipeline. Given a natural language query, find the top 5 most relevant *pages* from the given document store. 


## Task Description
You have been provided with 3 consulting reports. Each report is a multi-modal document with text, tables, images, diagrams, etc. A RAG pipeline uses these documents to provide additional context to an LLM answering user queries. Your goal is to build the retrieval section of this pipeline and to maximise the relevance of the retrieved documents. 

We have already built a basic 'out-the-box' version using Byaldi (link to byaldi). In appendix 2, you can see its output for a set of queries. You can use this as a baseline to improve upon. The queries that we have provided are what we would expect a user to ask the chat interface of the entire RAG system.

You may use any tools and packages that you like. Justify your choices.

You can potentially leverage tools like:
- Google Colab for GPU access
- Hugging Face for model access
- ColPali for vision model embeddings
- Byaldi for multi-modal storage and retrieval
- LlamaIndex for RAG pipeline
- ...

## Requirements
1. Parse and store the documents so that individual pages can be retrieved.
2. Build a retrieval pipeline that takes a query and returns the top 5 most relevant pages.
3. Optimise the retrieval pipeline for relevance.
4. Provide the following deliverables
    - README with setup/execution instructions
    - Source code
    - Explanation of engineering choices
    - Outputs for the queries in appendix 2


## Evaluation Criteria
You will be evaluated on the following criteria
| Criteria | Explanation |
| -------- | -------- |
| Relevance | How relevant are the retrieved documents to the query? |
| Multi-modal | How well does the retrieval pipeline handle multi-modal documents? <br> i.e. can it retrieve information from images, tables, diagrams, etc? |
| Code Quality | How well is the code written? <br> Especially modularity, readability, and maintainability |
| Explanation | Clear explanation of the engineering choices made | 



## Submission
Please submit a zip file or a github repo containing:
- `src/` - Source code
- `README.md` - README with setup/execution instructions
- `explanation.md` - Explanation of engineering choices
- `outputs.md` - Outputs for the queries in appendix 2



## Appendix
### Appendix 1: Document Store
We have provided a folder called `documents` with 3 consulting reports in pdf format. 
1. **Bain Report** - `bain_report_luxury_and_technology_artificial_intelligence_the_quiet_revolution.pdf` - A report by Bain & Company on the impact of AI on the luxury industry, mostly contains text but also some charts and diagrams.
2. **BCG Report** - `BCG-Executive-Perspectives-CEOs-Guide-to-Maximizing-Value-from-AI-EP0-3July2024.pdf` - A slidedeck by BCG on how executives should think about AI. Lots of text, but often in a complicated layout with many diagrams.
3. **McKinsey Report** - `what-every-ceo-should-know-about-generative-ai.pdf` - A report by McKinsey on generative AI. Majority block text with a couple of diagrams and decorative images.


### Appendix 2: Our baseline
The pages returned by our baseline system are listed in descending order of relevance as determined by that system. The ideal returned pages are the ones that are actually most relevant to the query and have been chosen by hand. The number of ideal pages is not fixed and can vary from query to query.

If you disagree with our choices for the ideal returned pages, we are more than open to hearing your arguments. 

| Query | Baseline Returned Pages | Ideal Returned Pages |
| -------- | :-------- | :-------- |
| *Who at Bain & Company is an expert in the luxury sector?* | Bain Report - Page 43 <br> Bain Report - Page 11 <br> Bain Report - Page 3 <br> Bain Report - Page 46 <br> Bain Report - Page 1 | Bain Report - Page 2 |
| *What should executives do to use AI to transform their businesses?* | BCG Report - Page 2 <br> Bain Report - Page 38 <br> BCG Report - Page 18 <br> Bain Report - Page 10 <br> McKinsey Report - Page 14  | BCG Report - Page 5 <br> BCG Report - Page 18 <br> McKinsey report - Page 14 <br> McKinsey report - Page 9 <br> Bain Report - Page 38 |
| *Summarise that Bain report on AI in the luxury industry* | Bain Report - Page 25 <br> Bain Report - Page 3 <br> Bain Report - Page 6 <br> Bain Report - Page 12 <br> Bain Report - Page 11 | Bain Report - Page 4 <br> Bain Report - Page 4 <br> Bain Report - Page 6 |
| *What are the expected gains, boosts, and transformations of AI? Provide a numerical answer* | BCG Report - Page 2 <br> BCG Report - Page 3 <br> Bain Report - Page 23 <br> BCG Report - Page 6 <br> McKinsey Report - Page 17 | BCG Report - Page 10 <br> BCG Report - Page 11 <br> BCG Report - Page 12 <br> Bain Report - Page 18 <br> Bain Report - Page 21 |
| *Find example case studies of AI being successfully used to transform a business* | Bain Report - Page 10 <br> Bain Report - Page 13 <br> BCG Report - Page 6 <br> McKinsey Report - Page 14 <br> McKinsey Report - Page 2 | Bain Report - Page 11 <br> Bain Report - Page 23 <br> Bain Report - Page 35 <br> BCG Report - Page 11 <br> BCG Report - Page 12 |
