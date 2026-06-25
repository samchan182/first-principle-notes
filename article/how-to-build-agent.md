## Rise of LLM
There's one research paper comes out from Google, which introduce the artificial neural network architecture, the **Transformer**. 

After, it's widely used to train LLM, in which text is converted to numerical representations called **tokens**, and each token is converted into a vector via lookup from a word embedding table. 

![images](/images/13.jpg)

---
THOSE are job for top 0.1% of global researcher, I don't think you need to go too deep on that. 

LLM is trained by transformer architecture. The reason why training a LLM is expensive, due to the cost of high-performance GPU, *LLM training requires processing billions of parameters through massive matrix multiplications in parallel*.

Also, it needs high-speed short-term memory as well, it must load billions of parameters simultaneously to generate text.

At the end, as the evolution of LLM, more test input with advance GPU computing ability, it emerges 'intelligence'. It can answer your complex question, it can even pass your school test.

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
unlike conventional api call and return, LLM can not generate all token return at one time. THAT why openai completion API format come out. 

