[← Back to README](../README.md)

## Rise of LLM
There's one research paper comes out from Google, it's the subfield of Machine Learning, which introduce the artificial neural network architecture, the **Transformer**. 

After, it's widely used to train LLM, in which text is converted to numerical representations called **tokens**, and each token is converted into a vector via lookup from a word embedding table. 

![images](/images/13.jpg)

---
THOSE are job for top 0.1% of global researcher, I don't think you need to go too deep on that. 

LLM is trained by transformer architecture. The reason why training a LLM is expensive, due to the cost of high-performance GPU, *LLM training requires processing billions of parameters through massive matrix multiplications in parallel*.

Also, it needs high-speed short-term memory as well, it must load billions of parameters simultaneously to generate text.

At the end, as the evolution of LLM, more test input with advance GPU computing ability, it emerges 'intelligence'. 

`*It can answer your complex question, it can even pass your school test*`.

NOW, AGENT SHOWS UP

![images](/images/11.jpg)


## Agent & Automation
Automation is focus on predefining code, it's a fixed process. For example, write down letter 'A', then letter 'B', nothing can change the first and second. 

`
1-> 2 -> 3 -> ..
`

However, AI agent is different. It use LLM model as the brain of processing, tool calling, etc. 

![image](/images/12.jpg)

The reason why you use AI agent is for flexibility and better model-driven decision-making result. 

The trade-off is, AI agent is consuming more money than automation. IF your goal is to solve simple problem, *DO NOT use AI for the sake of using AI*. 

`
Start simple, add complexity only when it pays
`

## Agentic System
If you want to build agentic system, the more important thing is to make is easy to be implemented and scalable. 

Under the Anthropic article [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents), the augmented LLM is the building block of each workflow. 

The workflow being introduced from this article:

- Prompt chaining
- Routing
- Parallelization
- Orchestrator worker
- evaluator optimizer

Agent will widely used in production as LLM become powerful and mature. 

- understanding complex inputs
- reasoning and planing
- using tool
- recover from error

## The API format
Unlike the conventional API request and return, LLM can not generate all token return at one time. THAT why openai completion API format come out. 

As the first marker leader, 

## LLM Evaluation
- benchmarks
- human preference
- YOUR OWN PROMPT   

**Answer-key method**. The most straight forward is rate of correctness (%) of given questions. For example, how many `1+1=2` LLM can answer correctly. 

**Human judgement**. blind test is giving to human being to judge each model's result. For example such benchmarking platform like `Chatbot Arena`. 

Some benchmarks:

- `Context Windows`. The maximum number of tokens the model can hold in one pass, including cache hit data in each loop. 
- `Pricing`. Usually the input token (user prompt/cache hit) is most cheapest. While output token is most expensive. And price of repeat token (cache miss) is a little chapter then output token. 
- `Speed`. Output token being generated per second. 
-  `Latency`. Total latency = latency time of each loop X number of loops. 

![images](/images/14.jpg)

## Cache MISS and Cache HIT 
They all applies to INPUT token. 

Cache MISS = input tokens DeepSeek's server has never seen before in this exact position at the start of a request. (The new token being generated in each loop, and ready to sent back to the next loop as new input)

Cache HIT = input tokens that match a prefix DeepSeek already processed in a recent earlier request. (for cache HIT, model hasn't seen it before, then it's much more expensive in cost)

## RAG
With 1 million context windows, is it mean that we don't need RAG?

- 1 million context windows is not enough for large database. If the database is over 100gb, it can not fit into the each context windows. 
- Token spending. Your key info will be cache hit of each loop, as long as it feed the LLM each time, the cost of token fee is massive. 
- more context, illusion arise of LLM. 

The core principle is to let your embedding model to find your related info in database, to combine to your prompt, sending them to LLM altogether. 


## LLM

The **Wire Format**, which is specific structured data protocol, to regulate the input to LLM. The market is following those two conventions:

- OpenAI Chat completion wire format
- Anthropic message wire format



