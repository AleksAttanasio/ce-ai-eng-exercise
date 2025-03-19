# Client Engineering: Development Exercise
This interview exercise focuses on building and evaluating a Retrieval-Augmented Generation (RAG) system using a company knowledge base dataset. The dataset can be found in `/data/rag_samples.csv` and contains IT support documentation covering topics such as setting up email on mobile devices, configuring VPN access, troubleshooting Microsoft Office issues, and other technical support scenarios.
The dataset is in csv format has 10 lines and 4 columns:
- **ki_topic** – The topic of the knowledge item (e.g., "Setting Up a Mobile Device for Company Email").
- **ki_text** – The full text of the knowledge item, usually providing instructions or explanations.
- **sample_question** – A sample user question related to the topic (e.g., "How do I set up my company email on my mobile?").
- **sample_ground_truth** – The expected response or answer to the sample question, often a concise summary or guidance.

You can use the AI models and provider that you are most confortable with or IBM watsonx.ai models (credentials are provided via e-mail).

Useful watsonx.ai documentation:
- [watsonx.ai Python Library](https://ibm.github.io/watsonx-ai-python-sdk/)
- [watsonx.ai Langchain integration](https://python.langchain.com/docs/integrations/llms/ibm_watsonx/)

## Exercise 1 - Data Cleaning
The provided knowledge base dataset contains several issues that need to be addressed to create an effective RAG system:
- Remove URL from the text samples
- Remove alphanumeric words from the text (e.g. `"Hello Maria whatsup123"`)
- Remove hashtags starting with the '#' character: (e.g.`"Mado is very good with last ball six #dhoni #six"`)
- Remove HTML Tags

Example of poisoned text to identify and remove:
```
Step 4: Verify Email Account**
http://example.com/886
#IT #http://example.com/503 #on #device #set #a
```

## Exercise 2 - RAG System Creation
Using the cleaned dataset, develop a simple RAG system that can effectively:
- Index and store the knowledge base articles appropriately
- Implement a retrieval mechanism that fetches relevant context based on user queries
- Create a generation component that produces helpful responses using the retrieved context
- Demonstrate how your system handles ambiguous queries that might match multiple knowledge base articles
- Implement a citation mechanism to indicate which parts of the knowledge base were used to generate the response

Provide your implementation and explain your design choices.

## Exercise 3 - Agent Development
Enhance your RAG system by implementing an agent-based approach. You can use the framework you prefer (Crew.ai, Langgraph, Langflow)

## Exercise 4 - Performance Evaluation
In the dataset you can find the golden response to the sample question. Evaluate the performance of your RAG system using:
- **ROUGE** scores comparing your system's responses to the sample ground truth answers provided
- **BLEU** scores for measuring text generation quality
- A custom relevance metric that assesses how well your system's responses address the specific user questions
