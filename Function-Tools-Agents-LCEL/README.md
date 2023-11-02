# Learnings

- OpoenAI Function Calling ( overview )
- LangChain Expression Language ( chain pipe syntax )
- OpenAi Function Calling in Langchain ( use of Pydantic, forced/ flexible call etc.)
- Getting Structured Output : 
    - Simple Use case (NER) : Tagging (Sentiment analysis) & Extraction (Names, Place)
    - Use of    
        1.  RunnableMap
        2.  Bind() OpenAI funcitons to model in a chain
        3.  Fallback : handling error, use of smaller model else bigger one
        4.  Interface : invoke, stream, batch
        5.  Output Parsers e.g. ```JsonOutputFuntionParser```, ```JsonKeyOutputFuntionParser```
- Tools & Routing 
    - LLM helps decide 
        1. What action to take ( which tool to use)
        2. Which parameter to use ( extract params from user input prompt)
    - Construct Chain pipe e.g. 
    ```prompt | model | openAIFunctionsAgentOutputParser() | route```
        * OpenAI function are binded to ```model``` 
            - Decide which function to use, extract params and pass to it

### When result of chain execution is *"AgentActionMessageLog"* i.e. OpenaAI functions (or tools) are executed else when it is *"AgentFinish"* then it means no OpenAI Funcitons (or tools) were used to answer.

- Conversational Agents
    - Use of MessagePlaceholder ( langchain.prompts )
        1. For Chat History
        2. For Agent Scratchpad