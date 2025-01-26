# BrowserGym and AgentLab: Enhancing Web Agent Research ✅
[arxiv link](https://arxiv.org/abs/2412.05467)

## Utilities Provided by the Framework
The **BrowserGym framework** provides powerful utilities to simplify the development and evaluation of web agents:
- **Comprehensive Observations**:
  - Access to **DOM** and **AXTree** for structural and accessibility insights.
  - Enriches elements with **bounding box (bbox)** coordinates and unique **BrowserGym IDs (bid)** for precise interaction.
  - Supplies **screenshots** of web pages mapped to element positions for visual understanding.
- **Error Feedback**:
  - Captures and relays errors (e.g., hidden element interactions) to agents for self-correction.
- **Task Setup and Validation**:
  - Simplifies task creation with predefined methods for environment setup and goal validation.
- **Ease of Use with AgentLab**:
  - Supports **parallel execution** of experiments and retries failed tasks automatically.
  - Includes **Dynamic Prompting** to manage token limits efficiently for LLM inputs.
  - Provides **AgentXRay**, a visual debugging tool for analyzing agent decisions.
- **Reproducibility Tools**:
  - Tracks software versions, timestamps, and configurations to ensure consistent experiment results.
  - Allows re-execution of experiments for validation.

## Benchmarks Unified Under BrowserGym
BrowserGym integrates a diverse range of benchmarks under a single framework, enabling standardized evaluations:
1. **MiniWoB(++)**: Simple web interaction tasks like form filling and button clicking.
2. **WebArena**: Tasks on replicas of real-world websites.
3. **VisualWebArena**: Focused on visually complex web interfaces.
4. **WorkArena (L1, L2, L3)**: Enterprise-level workflows with increasing difficulty.
5. **AssistantBench**: Open-web search and synthesis tasks.
6. **WebLINX**: Dataset of over 100,000 human interaction traces.


## Generic Agent for Experiment
The **GenericAgent** is a modular, configurable agent designed for efficient interaction with the BrowserGym framework:
1. **Initialization**:
   - Configurable to use features like chain-of-thought reasoning, screenshots, and observation history.
2. **Task Setup**:
   - Processes observations (e.g., DOM, AXTree, screenshots) and task goals provided by the environment.
3. **Action Selection**:
   - Constructs a dynamic **prompt** for the LLM using task goals, observations, and reasoning mechanisms.
   - Ensures the prompt fits within token limits using **Dynamic Prompting**.
   - Sends the prompt to the LLM for the next action.
4. **Action Execution**:
   - Executes the action using BrowserGym APIs (e.g., clicking buttons, filling forms).
   - Adapts to errors and retries invalid actions up to 4 times.
5. **Result Evaluation**:
   - Evaluates task completion, assigns rewards, and tracks outcomes.
6. **Logging**:
   - Logs detailed information for debugging and reproducibility through **AgentXRay**.


## Experiments with LLMs and Results
The authors conducted large-scale evaluations of several state-of-the-art LLMs using BrowserGym and AgentLab:
- **LLMs Tested**:
  - Proprietary: **GPT-4o** (OpenAI), **Claude-3.5-Sonnet** (Anthropic).
  - Open-source: **Llama-3.1** (70B and 405B parameters).
- **Experiment Details**:
  - Benchmarks: MiniWoB, WorkArena (L1, L2, L3), WebArena, VisualWebArena, WebLINX, AssistantBench.
  - Metrics: Task success rate and standard error.
- **Key Results**:
  - **Claude-3.5-Sonnet** achieved the highest performance, with 39.1% success on WorkArena L2.
  - **GPT-4o** excelled in vision-related tasks like VisualWebArena.
  - Open-source models like **Llama-3.1-405B** showed competitive results, sometimes surpassing GPT-4o-Mini.

This unified framework and experimental setup demonstrate the potential of BrowserGym and AgentLab to advance LLM-driven web automation and benchmarking.


# Mind2Web
[arxiv link](https://arxiv.org/abs/2306.06070)

## Abstract
We introduce Mind2Web, the first dataset for developing and evaluating generalist agents for the web that can follow language instructions to complete complex tasks on any website. Existing datasets for web agents either use simulated websites or only cover a limited set of websites and tasks, thus not suitable for generalist web agents. With over 2,000 open-ended tasks collected from 137 websites spanning 31 domains and crowdsourced action sequences for the tasks, Mind2Web provides three necessary ingredients for building generalist web agents: 1. diverse domains, websites, and tasks, 2. use of real-world websites instead of simulated and simplified ones, and 3. a broad spectrum of user interaction patterns. Based on Mind2Web, we conduct an initial exploration of using large language models (LLMs) for building generalist web agents. While the raw HTML of real-world websites are often too large to be fed to LLMs, we show that first filtering it with a small LM significantly improves the effectiveness and efficiency of LLMs. Our solution demonstrates a decent level of performance, even on websites or entire domains the model has never seen before, but there is still a substantial room to improve towards truly generalizable agents.

