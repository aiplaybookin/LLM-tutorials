# LLM-tutorials

# Types of Tasks
- Q&A : 1 to 1
- Chat : With history in session


# Architecture



## 1. Data preprocessing / embedding
- Chunks size
- Vector db
- Model changes, increases context size - would you change chunk size? : tradeoff throughput and cost ofcourse! a very long context, loss of info?
- data-freshness problems

* CONTEXTUAL DATA : formats, loaders, 
* EMBEDDINGS : text-embedding-ada-002, cohere, opensource - Sentence Transformers from Huggingface
* CHOICE of DB : 
    - opensource - Weaviate, Vespa, and Qdrant
    - Local vector management libraries - Chroma and Faiss
    - OLTP extensions - pgvector (Postgres)
    - AWS -  S3 with AWS Kendra or AWS OpenSearch


## 2. Prompt construction / retrieval
Challenge in 
- specific prompt text (domain/task driven)
- few shot examples
- any external api (e.g. web search, maths calculation etc)
- corresponding context (internal organisational data, code base)


## 3. Prompt execution / inference
- additional logging
- caching, and 
- validation of response

* Few shots no less than 12 examples
* Prmpt strategies : chain-of-thought, self-consistency, generated knowledge, tree of thoughts, directional stimulus
* ORCHESTRATIONS :
    - Langchain / Llamaindex
* Chioce of Model
    - Proprietary Models - e.g. **Claude** offers fast inference, GPT-3.5-level accuracy
    - open source models - API interfaces from Hugging Face and Replicate, LLaMa model from Meta
* Operational tooling
    - Cache - redis
    - Tools like **Weights & Biases** and **MLflow** (ported from traditional machine learning) or **PromptLayer** and **Helicone** (purpose-built for LLMs)
    - Validate LLM outputs - e.g., Guardrails 
    - Detect prompt injection attacks - e.g., Rebuff
    - Hosting - cloud providers, Vercel
        - **Steamship** provide end-to-end hosting for LLM apps, including orchestration (LangChain), multi-tenant data contexts, async tasks, vector storage, and key management
        - **Anyscale** and **Modal** allow developers to host models and Python code in one place


## Agents
Combination of 
- reasoning/planning
- tool usage, and 
- memory / recursion / self-reflection


## Various Prompt techniques -
- “Chain of Thought” (CoT) (Huang et al., 2022; Wei et al., 2022), 
- "Describe, Explain, Plan, and Select” (DEPS) (Wang et al., 2023), 
- “Reason+Act” (ReAct) (Yao et al., 2023) and 
- self-reflection (Reflexon) (Shinn et al., 2023)

1) require the creation of task-specific prompt templates, and 
2) are limited to a single train of thought within the LLM which precludes the use of multiple attack angles for creative problem solving

**Ask the “right questions”**


### Socratic dialogues

This removes the need for fixed-format task-specific prompts and enables multiple instantiations of LLMs to engage in free-form, self-proposed inquiry, thereby fostering the self-discovery of knowledge.



**Questions**
What vector DB are you using? What is the data structure that you're vectorizing? What is your chunk size? Have you implemented memory? What prompt or technique are you using (ReACT, CoT, few-shot, etc)? Are you only using vector DBs? Do you use sequential chains? Does it need tools? Depending on your data, business case and what output you expect from the agent, there is no one-size-fits-them-all.


Innovations in embedding models ( as we context grows ) rather than choice of vector db, embeddings specific to llm?

**Ref :**
1. https://a16z.com/2023/06/20/emerging-architectures-for-llm-applications/