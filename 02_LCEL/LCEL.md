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

<img src ="https://github.com/iamrajharshit/OnLangChain/blob/main/02_LCEL/img/01_LCEL.png"><br>

```
Chain = prompt | llm | OutputParser
```
This syntax indicates that the input will flow through the prompt, then be processed by the LLM and finally be handled by the OutputParser.

### Key Concepts

- LCEL supports modifying component parameters dynamically at runtime, providing flexibility in how the chain is executed.

- Ensures that each component in the chain receives and processes the appropriate type of input.

- Defines the type of output each component produces, ensuring compatibility and correct dat flow through the chain.

