# Q&A

<br>

> [!IMPORTANT]
> Document learnings in a Q&A format.

## What's 2nm means in semiconductor industry?
The latest frontier in microchip manufacturing. 

The physical size of smallest feature. 

## Scientific way to approach AI coding?
`Optimize Problem`-->`Write down your own solution`-->`Use AI tool for help`-->`Compare solution`

## Docstrings or Comment?
Comment is for developer<br>
Docstrings is for user of this code/function <br>
Never use __(''')__, it will create unnecessary memory

PEP 257 is the baseline standand for Python docstrings, base convention.
https://peps.python.org/pep-0257/ 

## Difference between Library and Package?
Package: A directly or folder contains Python module.

Library: A collection of code provides functionality.

When you need to install, it's library (pip install transformers), when you need to import (import transformers), it's package. 

## Will Python code change by environment?
No! python code does not change the code based on environment. Different environment means the <u>availablility of packages</u> changes.<br>
The only difference is the package installation. 

## What's Agent?
An AI system that use LLM as core engine to auto-use all kinds of tool(api, search, interrupts,..etc) to achieve the goal. 

While agent is doing tool-calling loop, the environment need to be concern. 

## What's difference between Workflow and Agent?
Workflow is set of fixed steps OR predefined code

Agent is LLM directs its own actions based on tools, which's provided by environment. 

Therefore, calling tool is super important in agent (BFCL leaderboard is llm ability of calling tool in loop)

## Why use .env file to store API key?
A .env file is used to store sensitive information like API keys securely. It should be added to .gitignore so it is not included in version control.

## How to make sure your .env file is being ignored by git?
(base) samchan@chenzisnslaptop llm-hands-on-projects % git check-ignore .env

.env

## Three ways of using models:
1. Chat interface
2. Cloud APIs
3. Direct inference

## What is Ollama doing behind your local?
Ollama is like a coffee machine you buy (download), and you put it into your kitchen (local) to make coffee.

Ollama Applicaition is like put your coffee machine into active mode (turn on application). Now your local become a server. 

Your python code is like the process / steps of making coffee. To do the specific jobs for you. Ollama is a server running behind, it's the client-server agriculture.

## Why token is so important in LLM?
The model cannot see the word as human being. Each sentence need to convert into series of "TOKEN", and convert into numerical representation, to predict the next "word".

OpenAI provides a "Tokenizer" to understand how tokens is being created by human language. https://platform.openai.com/tokenizer

## How token calculate in Agent?
Total token spending is the SUM of input & output token in each loop. (cache hit and cache miss, including output)

e.g. LIke OpenClaw usage, When asking API call, the input not only your prompt, including your configuration file data, OpenClaw will keep asking again and again. 

## What's Cache MISS and Cache HIT token?
They all applies to INPUT token. 

Cache MISS = input tokens DeepSeek's server has never seen before in this exact position at the start of a request. (The new token being generated in each loop, and ready to sent back to the next loop as new input)

Cache HIT = input tokens that match a prefix DeepSeek already processed in a recent earlier request. (for cache HIT, model hasn't seen it before, then it's much more expensive in cost)

For server, main difference is whether the server still remembers data. 

## Claude code OR openclaw?
Claude Code lives inside a terminal session. Close the terminal → Claude Code dies.

OpenClaw is the Gateway runs as an independent OS service (your Windows Scheduled Task). If you put setting on VPS, it can run 24hrs, you can talk to openclaw via your phone at 3am. 

claude code is like co-pilot in your terminal, while openclaw is like your personal assistant. 

## What is context window?
It also called context length, the maximun number of tokens a LLM can process at one time. The short-term memory for the entire LLM's conversation. 

Which is including <u>current prompt</u> + <u>current ouput</u> + previous processed <u>history tokens</u>.

## What is API cost?
The price you pay for using this LLM, it is paying for the number of tokens being processed, both input tokens and output tokens. 

## What is relationship between LLM and machine learning?
Machine learning is a board field of study. In fact, LLM is a specific, advanced type of machine learning model. 

## Why OpenAI has python SDKs?
Almost every major services provides SDKs (AWS OpenAI Stripe...). For each programming language, they has an API to speak to "raw HTTP", the sending web request with specific formats.  

## what is SDKs?
Software Development Kit. To prevent to 'talk' to the system where you need to build everything from scratch. It gives you some pre-existed works from someone else.

## Why we need to setup Anaconda in advance?
Anaconda is a distribution of python, which is bundled with conda package manager, with many pre-installed packages, for ML/data science. An environment is just a simply folder contains many installed packaged. 

When you in (llms) environment, it tells your terminal to <u>use python and package in this particular folder</u>. s

While the (base) is default conda environment. It shows once you install conda. 

## What's pipeline?
A set of data processing elements connected in series. Output of one element is the input of next element. 

It's like assembly line in car factory, start wity body shop, next to plaint shop, etc...

## Why HuggingFace has pipeline?
Using machine learning models (especially transformers) involves multiple complex steps that must happen in the correct order

Hugging Face pipeline is a great way to use model for inference.You can use simple API to dedicate several tasks. Hugging Face __"pipeline()"__ is like Swiss Army Knife for AI tasks. After authentication, you get access to a huge collection of pre-trained models that handle different tasks with just one line of code

## What is HuggingFace Transformers?
HuggingFace Transformers is a python library that provides pre-trained model, easy-to-use pipelines, training tools, and model architecture. 

Hugging Face is not just a storage platform (like github), it's comprehensive AI/ML platform. There'r so many ML model that is being provided, not only Transformers. When you use transformers library, it will downloads the model to your running machine, and load into your RAM/GPU, and do the inference. 

1. Transformers - Main library for pre-trained models (what you're learning)
2. Datasets - Loading and processing datasets
3. Tokenizers - Fast tokenization
4. Diffusers - Image generation models (Stable Diffusion, etc.)
5. Accelerate - Multi-GPU training optimization

## Why HuggingFace needs API key for authorization?
Even though this platform is open-source, but it doesn't mean unlimited access. And some of the model is huge, with ID limit, the download bandwidth (maximum rate of data transfer) costs will the crash of servers. 

## What is the relationship between Tokenizer and Model?
Model and tokenizer are technically separate but functionally inseparable. Tokenizer decides what form of data can put into the neural network. Row data (user input) can be transfer into byte-pair, word piece, sentence piece, etc. 

Usually a "Model" release with three files, 
1. The model weights (the neural network)
2. The tokenizer (how to convert text to numbers)
3. The config files (architecture details)

The model can not function without it own specific tokenizer.

## What is Chinchilla Scaling Law?
It solved the problem of not knowing the training budget before training a new model

The Chinchilla Scaling Law establishes the optimal relationship between model size (number of parameters) and training data volume. 

## LLM benchmark?
It's the standardized test or dataset used to measure and compare the model performance. 

e.g.

1. Knowledge Tests - Check if the model knows facts (MMLU, TriviaQA)
2. Reasoning Tests - Evaluate logical thinking (ARC, HellaSwag)
3. Coding Tests - Verify programming ability (HumanEval, MBPP)
4. Math Tests - Test mathematical problem-solving (GSM8K, MATH)
5. Language Understanding - Measure comprehension (GLUE, SuperGLUE)
6. Safety Tests - Check for harmful outputs (TruthfulQA, BBQ)

Also, there're 6 hard-level benchmark to test a LLM. (e.g. GPQA, BBHard, Math LV5, IFEval.. ). ALl can be found in Hugging Face leaderboard.

## What is HuggingFace Depoly's Inference Endpoints?
Hugging Face Inference Endpoints is a managed service that lets you deploy models as production-ready APIs with just a few clicks. 

Think of it as "your model as a service" without setting up your own server, managing GPU, etc. You can dedicate REST API endpoint for your model. 

The paying fee is NOT directly pay to Cloud Provider. 

## What's LangChain?
It's an open-source framework, providing the common framework to interface with LLM. 

A pre-built agent architecture framework. Quickly set up your agents and applications. 

## Relationship between LangChain and RAG?
RAG is a architectural pattern, for augmenting LLMs with external knowledge.

LangChain is a tool (library), to help implement RAG (or many other LLMs patterns)

## What is RAG?
Retrieval Augmented Generation. (Retrieval means to load external material into memory, can be later injected into the prompt)

The model does NOT have the latest data, use RAG pipeline (Retrieval System) grab the up-to-date info in database, and post it into your prompt to LLM behind. 

The process: RAG pipeline = load → split → embed → index → retrieve → augment prompt → generate.

The vector database is knowledge database, RAG uses an encoder (embedding model) to map all your documents into vectors, and store in vector database.

The user query will be encoded into query vectors, At query time, only the most relevant chunks are retrieved and passed to the LLM. This way the model has access to potentially millions of documents without exceeding the context limit. 

So the “augmenting” behind the scenes solves two problems:

1. Context window bottleneck
2. Semantic search accuracy

## What's difference between Auto-Regressive and Auto-Encoding LLMs?
Autoregressive: "What comes next?" - Built for generation, processes sequentially (ChatGPT, Claude)

Autoencoding: "What fits here?" - Built for understanding, processes holistically (Google Bert)

When in encoding llms, the vectors has thousands of direction. 



## In what case you need RAG?
1. Knowledge is too large. Cannot fit all documents into the LLM's content windows
2. Knowledge changes often.
3. Privacy concern. You don't want to fine-tune an LLM on sensitive company data
4. Domain specific. RAG ensures answers are grounded in your docs, not model guesses, in some cases like customer support, law, finance. 

## What is Chroma?
It's a open-source vector database often use in RAG.

It stores data as embeddings, support similarity search, lightweight and easy to run locally. 

## How final answer is being produced after RAG?
The LLM then generates the final answer based on both its pretrained knowledge and the retrieved context by RAG on knowledge_based file. 

tech stack: LangChain + Chroma

## What is the callback in RAG?s
A callback is a function or hook to execute automatically during the retrieve. 

It let you track, log, or modify what happened inside the RAG process without rewriting the whole pipeline. 

## What is fine-tuning?
Fine-tuning means to adjust the pre-trained LLM on new data, to fit specific problem

## 5 steps to solve business question by LLMs?
1. Understand.
2. Prepare.
3. Select.
4. Customize.
5. Productionize.

## What is LoRA?
Low-rank adaptation in LLMs.

The problem like Llama 3.1 model with 8B weight, if you want to train the model, there will be need to 32 GB RAM, Too much to optimize.

1. The first step of LoRA is to freeze the weight. We're not going to optimize due to massive amount. 
2. TO pick some layers to target, which called "Target Layers"
3. Create new "adaptor" metric with lower dimension, fewer parameters. Which's called "lower rank adaptor"
4. Apply those adaptor, into Target Layers, to train

## What is QLoRA? (Quantized LoRA)
It's the extension of LoRA. Quantization, in the Q of QLoRA.

Same adapters but base loaded in 4-bit quantization of base model, to fit bigger models in limited VRAM, retaining quality and save memory. 

It's not about layers, it's about the bits. While LoRA focus on parameter-efficient adaptation. 

## What's relationship between LoRA & Fine-tuning?
Full fine-tuning updates every weight up to billions, needs huge memory and computing power. Both methos, LoRA & QLoRA are aiming to solve those problems.

If the model already fits but full fine‑tune is too costly → LoRA.

If the model does not fit in normal precision → QLoRA (or pick a smaller model).

## What's hyper-parameter used during training?
It's the setting you choose before training, to control how the model learn.

## Five important hyper-parmeters for QLoRA?
1. Target Modules. Places in transformer where LoRA adapters are inserted. 

2. R. Intermediate dimension. 

3. Alpha. scaling factor, controls how much influence LoRA adapters have. 

4. Quantization. 

5. Dropout, so much training, no longer understand the general trend. wipe out 10%, everytime you train, see 90% of mode

## Five important hyper-parmeters for training?
1. Epochs. how many times go through whole data set

2. batch size. Number of samples processed before updating wegiths

3. learning rate. Step size for weight updates.

4. gradient accumulation

5. optimizer. Algorithm to apply gradients to parameters. To update a little to shift your output.

## How training works?
1. Forward Pass. Input data flows through network.

2. Loss Calculation. Prediction is compared with true label, it uses loss function. 

3. Backward Pass. Gradients of the loss with respect to each weight are computed using backpropagation.

(PS: Cross-entropy loss measures the difference between two probability distributions: the predicted distribution from the model and the true distribution (labels).)

4. Optimization. Optimizer updates weights using gradients.

## AWS vs Modal?
AWS is the infrstructure sandbox, with heavy setup as cloud service. 
Modal, serverless clouds for running ML model apps quickly. 

serverless cloud means you don't have to manage servers. You only write functions and small services. 

## How to set other model while using Claude Code?
Go change the environment variables. 
```
1. ANTHROPIC_BASE_URL → where to send requests
2. ANTHROPIC_AUTH_TOKEN → what API key to use
```

The variable is being saved on RAM, never save outside the terminal tab. Once you delete tab, it gone. Shell environment variables works, but not specific to Claude Code. 

e.g.
```
$env:ANTHROPIC_BASE_URL = "https://api.deepseek.com/anthropic" 
$env:ANTHROPIC_AUTH_TOKEN = "your-deepseek-key"
$env:ANTHROPIC_MODEL = "deepseek-chat"
claude
```

## Difference between OpenRouter & Hugging Face?
OpenRouter = "I want to call AI models from my app"

Hugging Face = "I want to download AI models, study them, fine-tune them, or share them"

## How to set permission to claude code?
The Claude Code permission is set in `.claude/settings.json`, it contains `allow` and `deny` object  written by JSON. 

Some permission like never access files, how to open a folder, ...etc. 

## Will user prompt leaves evidence in LLM?
NO. After one open source model is being trained, the weights file is fixed. The working principle of LLM is your context(user input) is being inserted for linear calculation, it's a black box, NO ONE knows what's going on inside. INTELLIGENCE just emerged. 

The only possibility is your LLM provider knows your input and output for some reasons (training personal data, ...etc), that's how your privacy leaked. 

## What's multi-agent?
A framework where multiple autonomous agents interact within shared environment to achieve goal. 

It's a design pattern of communication. The language you choose is unimportant. 

LangGraph is low-level solution framework (LangChain is built on top of LangGraph)

## Why agent needs sandbox?
Agent will do stupid things, like deleting your PS5 saving log. 

Putting agent in sandbox is like putting a monster into an container, it can still work for you actual environment, but it only works for things you give it to him. 

Also sandbox can do state isolation. You can let your agent works simultaneously, all in one directory. 

## What is sandbox?
An isolated environment in your device, for you to test and any dangerous things. 

In Windows, sandbox is just a light-weight program, it creates a clone environment of your current computer hardware. You can understand it as mini-VM(virtual machine)

## Windows default sandbox?
Sandbox is similar to VM, but in VM setting, you need to set memory, storage, and so on, that's to complicated for user. 

Windows sandbox put all those abstract steps away from user. 

## What is LangChain & LangGraph?
LangChain is open-source framework, for building application powered by LLM. LangGraph is built on top of LangChain. 

They both exist for better solving different problem. Before LangGraph is created, LangChain is like linear-assembly factory, when it down to multi-layer, or more complicate problem, it's inefficient. That's why LangGraph come out. 

- LangChain framework holds static building block, it provides standard interface to connect to LLM. You can think it as material. 

- LangGraph framework is a control framework, it allows data move, execute, ..etc. 

## How to apply LangChain to Kotlin?
Kotlin is eventually use JVM to compile, the structure is more likely close to java. You can use `LangChain4j`, which is a open-source framework, designed to simplify to implement LLM to java application. 

## Different api call between OkHttp and LangChain4j?
OkHttp is open-source client in http request. It's a simple one-off request.

LangChain4j is abstraction layer, an operation system to provide you service back by llm. 

In android dev, the LangChain4j doesn't fit the android JVM compile. 

## What's Claude Code plugin?
A software plugin is simply a set of instructions, which is extended from main program. 

The first principle is it requires a set a reliable and standard data, to insert into core engine. 

## What's the entry point of LLM?
The first principle of `entry point` of LLM or any AI application is the decreasing cost of expressing intent. 

e.g. I want to write a doc and save to computer. Back to 1980s, I need to go to terminal line, to insert sentence after sentence. Back to 2000s, I only need to open a notepad, and start typing.

The entry point is determined by the advance of how tool is faster to meet user intent with minimum friction. 

I think due to the fact that human is so lazy, then the entry point of AI hardware must all be in audio input and output. Sounds is super-convenient for human to exchange information. 

Maybe next step is device like neuralink, human do not need to speak, to exchange info with computer. 

## How to determine the agent winner?
There're 3 indicator
- The OS becomes agent. Only Apple? it's hardware related
- The agent becomes ambient/everywhere through all the hardwares.
-  The agent become browser. 

ChatGPT chatbot only released about 2-3 years, see what's happening before 2030.

