# How to learn every topic using first principles

Use this learning cycle for every concept, whether it is an LLM, vector database, Kubernetes, LangGraph, or a client discovery call.

- Why does this exist?
Identify the problem before learning the tool.

- What are its smallest components?
Understand inputs, outputs, state, logic, and dependencies.

- Can I build a tiny version myself?
Implement the underlying idea before adopting a framework.

- How can it fail?
Test edge cases, malformed data, timeouts, permissions and incorrect outputs.

- How do I prove its value?
Measure quality, time saved, cost, reliability and user adoption.


## Define
What is this thing, really? At the lowest level, what are the inputs, outputs, and transformations?
(Examples: “What is an LLM? It’s a function that predicts tokens, trained on text, that can be used for generation, classification, or embedding.” “What is a vector database? It’s a database optimized for similarity search over embeddings.”)

## Decompose
Break it into its fundamental components. For an LLM application: prompts, embeddings, retrieval, generation, tool use, guardrails, evaluation, deployment.

## Build and integrate
Write code that uses the thing. Connect it to other pieces. Put it in a small but complete system.
(Examples: Build a RAG pipeline with an embedding model, vector store, and LLM. Deploy it via an API and a simple UI.)

## Evaluate and break
Design tests and metrics. Try to make it fail. Understand why.
(Examples: Test retrieval with cases where the answer should be present but is missing. Test the LLM with adversarial prompts.)

## Iterate
Fix what broke. Improve what was weak. Repeat the cycle.

## The Three Rules

### Rule 1: You must be able to explain it to a smart 14-year-old
If you can’t, you don’t understand it yet.

### Rule 2: You must be able to write production-quality code for it
Not just a Jupyter notebook. Code that is tested, containerized, and can be deployed.

### Rule 3: You must be able to integrate it into a system with a real user
If the AI cannot be connected to a database, a webhook, or a frontend, it is not yet an FDE skill.

## How to use this with the FDE roadmap

When you get to the AI section:
- Define: What is RAG? What is tool use?
- Decompose: What are the parts of a RAG pipeline? (ingestion, retrieval, generation)
- Build and integrate: Build a RAG pipeline and connect it to an LLM API.
- Evaluate and break: Test with cases where the retrieval fails.
- Iterate: Improve the chunking or retrieval.

Repeat this for every topic.
This is how you ensure that by the end, you don't just know about AI concepts—you can ship working AI systems.