# LangChain for LLM Application Development

## Content

|SLno:|Content|Description|
|--|--|--|
|1|[01_Models-Prompts-Parsers]()||
|2|[]()||
|3|[]()||
|4|[]()||
|5|[]()||
|6|[]()||

## Overview

### LangChain
LangChain started as open source framework for building LLM apps.

- An open source dev framework for building LLM apps.
    - We have two different pacakges Python and TypeScript.
    - Focused on composition and modularity
    - Modular components
    - Use cases: Chains and ways of combining these modular components into more end-to-end applications.

### Components

#### Models
- LLMs
- Chat Models
- Text Embedding Models

#### Prompts
- Prompt Templates
- Output Parsers: Retry/fixing logic
- Example Selectors

#### Indexes
Ways of ingesting data so that we combine it with models.
- Documents Loaders
- Text Splitters
- Vector stores
- Retrivers

#### Chains
- Prompt + LLM + Output parsing
- Used as building blocks for longer chains
- More application specific chains

#### Agents
- Agent Types
    - Algorithums for getting LLMs to use tools 
- Agent toolkits
    - Agents armed with specific tools for a specific appS
