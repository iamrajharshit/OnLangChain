# LangChain Expression Language (LCEL)
A new syntax which makes things more eaiser to construct and work with chains and agents.

## What is LCEL?
LangChain Expression Language (LCEL) is a framework within LangChain designed to facilitate the composition and chaining of various components for processing language tasks. It allows developers to build complex workflows by defining how different components interact with each other and how parameters can be modified at runtime.

## Components of LCEL

<img src="https://github.com/iamrajharshit/OnLangChain/blob/main/02_LCEL/img/01_LCEL_a.png">
<br>

- **Prompt**: This component takes an initial input and structures it into a form that can be processed by the language model (LLM). It serves as the starting point of the chain.

- It ensures the input adheres to the allowed set of input types required by the LLM.

- **LLM (Language MOdel)**:  This is the core component that processes the structured input from the prompt. It represents the language model used for generating or transforming text.

    - **Required methods**: 
        - `invoke`:Executes the language model to process the input.
        - `stream`:Streams the output if the model supports streaming responses.
        - `batch`:Processes multiple inputs in a batch for efficiency.

- Parameters of the LLM can be modified at runtime using methods such as `bind`.

- **Parser**: This component processes the output from the LLM. It parses or transfroms the model's output into the desired format or structure.

- It handles the final output types, ensuring the output is in the required form for the next stage of processing or for user consumption.

## Composition Syntax
LCEL allows the composition of these components using a syntax similar to the Linux pipe (`|`) operator, making it intuitive to chain multiple components together.

<img src ="https://github.com/iamrajharshit/OnLangChain/blob/main/02_LCEL/img/01_LCEL_b.png"><br>

```
Chain = prompt | llm | OutputParser
```
This syntax indicates that the input will flow through the prompt, then be processed by the LLM and finally be handled by the OutputParser.

### Key Concepts

- LCEL supports modifying component parameters dynamically at runtime, providing flexibility in how the chain is executed.

- Ensures that each component in the chain receives and processes the appropriate type of input.

- Defines the type of output each component produces, ensuring compatibility and correct dat flow through the chain.

## Interface 
The interface components in LangChain that implement the "Runnable" protocol are designed to standardize how different parts of a language processing chain interact with each other. 

### Runnable Protocol

Common Methods:

- `invoke`: This method executes the primary function of the component, such as processing input data to generate output.

- `stream`: This method supports streaming output, which is useful for handling large outputs or real-time data processing.

- `abatch`: This method supports streaming output, which is useful for handling large outputs or real-time data processing.

Common Properties:
- input_schema: Defines the structure and type of input data that the component expects.

- output_schema: Specifies the structure and type of output data that the component produces.

### Common I/O
|Component|Input Type|Output Type|
|--|--|--|
|Prompt|Dictionary|Prompt Value|
|Retriever|Single String|List of Documents|
|LLM|String,list of messages or Prompt Value|String|
|ChatModel|String, list of messages or Prompt Value|ChatMessage|
|Tool|String/Dictionary|Tool dependent|
|Output Parser|Output of LLm or ChatModel|Parser dependent|


## Why use LCEL?
LangChain Expression Language (LCEL) provides a powerful framework for building and managing complex language processing workflows. Its key features and capabilities make it an attractive choice for developers working with language models and related components.

**Key Features and Benefits of LCEL:**

- Async, Batch and Streaming Support
    - Asynchronous Support: LCEL allows components to run asynchronously, enabling tasks to execute concurrently without blocking each other. This is particularly useful for I/O-bound operations, as it improves efficiency and responsiveness.

    - Batch support: LCEL supports batch processing, which allows multiple inputs to be processed simultaneously. This can significantly reduce processing time and improve throughput.

    - Streaming support: Streaming capabilities enable the handling of large outputs or real-time data processing, which is crucial for applications that require continuous data flow and immediate processing.

- Fallbacks: LCEL supports fallback mechanisms, which means that if a component fails or produces an error, an alternative component or method can be used. This enhances the robustness and reliability of the system by ensuring that it can continue functioning even in the presence of errors.

- Parallelism
    - Time-Consuming LLM Calls: Language model (LLM) calls can be computationally intensive and time-consuming. LCEL's parallelism capabilities allow these calls to be distributed across multiple processors or threads, reducing the overall processing time.

    - Parallel Execution of Components: Any components that can be run in parallel are executed simultaneously. This parallelism maximizes resource utilization and improves the performance of the entire workflow.

- Built-in Logging: LCEL includes built-in logging features that provide detailed insights into the execution of components. This logging helps in monitoring the workflow, debugging issues, and optimization.