# SeeAct: Gpt-4v (ision) is a generalist web agent, if grounded ✅
[arxiv link](https://arxiv.org/abs/2401.01614)

## How the Agent Works
1. **Task Input:** The agent receives a natural language task (e.g., "Rent a truck").
2. **Webpage Observation:** It uses:
   - **Visual Screenshot** of the page.
   - **HTML Document** for structure.
3. **Action Generation:** GPT-4V generates a natural language action plan, such as "Click the 'Find Your Truck' button."
4. **Action Grounding:** Converts the plan into a precise action:
   - Identifies the **target element** (e.g., button).
   - Selects the **operation** (e.g., Click, Type).
   - Determines any **additional value** (e.g., text to type).
5. **Execution:** Performs the grounded action on the website.
6. **Repeat:** Observes the updated page and repeats the cycle until the task is complete.

## Benchmarks and Performance
1. **Dataset:** MIND2WEB (2,000+ tasks, 137 websites, 12 domains):
   - Tasks involve **Click**, **Type**, and **Select** actions.
   - Split into **Cross-Domain**, **Cross-Website**, and **Cross-Task** test sets.
2. **Offline Evaluation:**
   - **Oracle Grounding:** ~62% step success rate.
   - **Automated Grounding (Best: Textual Choices):** ~40% step success rate.
3. **Online Evaluation (Live Websites):**
   - **Oracle Grounding:** 51.1% task success rate.
   - **Automated Grounding (Best: Textual Choices):** 37.8% task success rate.
4. **Comparison:**
   - GPT-4V outperformed text-only models (e.g., GPT-4, FLAN-T5) and smaller multimodal models (e.g., BLIP-2).

## Important Insights
1. **Grounding Challenges:**
   - GPT-4V struggles with fine-grained element selection, often hallucinating or mislinking visual elements.
2. **Online vs. Offline Evaluation:**
   - Online evaluation is more realistic and forgiving since multiple plans can achieve the same task.
3. **Task Complexity:**
   - Longer tasks lead to cascading errors, degrading performance.
4. **Error Correction:**
   - GPT-4V showed the ability to self-correct errors in online settings.
5. **Speculative Planning:**
   - Can predict future webpage states to plan multiple steps ahead.
6. **World Knowledge:**
   - Utilized knowledge effectively, such as identifying airport codes.
7. **Safety Concerns:**
   - Highlights privacy risks and potential harm from unintended actions, emphasizing the need for robust safeguards.


# The Impact of Element Ordering on LM Agent Performance ✅
[arxiv link](https://arxiv.org/abs/2409.12089)

## Importance of Element Ordering
- The order in which elements are presented to Language Model (LM) agents has a significant impact on their performance.
- Randomizing the order of elements degrades performance as much as removing all visible text from webpages.
- Proper semantic ordering improves context understanding and task success rates for agents.

## Testing Element Ordering
- **Ablation Studies**:
  - Attributes like element ordering, text captions, and labels were individually removed to analyze their impact on performance.
  - Dimensionality reduction techniques, like t-SNE, were used to derive an effective order for elements in pixel-only environments.
- **Evaluation Metrics**:
  - Success rate in tasks was used to measure agent performance.
  - OmniACT benchmarks employed action scores to evaluate accuracy in tasks involving GUI navigation.

## Benchmarks
- **VisualWebArena**:
  - Evaluates multimodal agents on web tasks with access to the DOM tree.
  - Agents' success rates were tested with different ordering methods, including DOM-based pre-order traversal.
- **OmniACT**:
  - Benchmarks agents in desktop and web environments where only pixel information is available.
  - Tested the proposed t-SNE ordering method, achieving a two-fold improvement in task success rates over previous methods.
 

# AnyTool: Self-Reflective, Hierarchical Agents for Large-Scale API Calls
[arxiv link](https://arxiv.org/abs/2409.12089)

# Multimodal Web Navigation with Instruction-Finetuned Foundation Models ✅
[arxiv link](https://arxiv.org/abs/2305.11854)

## How the Agent Uses ViT and T5
1. **Visual Processing with ViT**:
   - **Screenshots** of the webpage are divided into **16 × 16 patches**.
   - Each patch is encoded into a **visual token** by the Vision Transformer (ViT).
   - Tokens capture **local visual details** (e.g., buttons, text fields) and **temporal information** from the last **2 steps** of interaction.

2. **Text Processing with Flan-T5**:
   - The webpage's **HTML structure** is processed into tokens by Flan-T5's encoder.
   - Flan-T5 captures the **hierarchical relationships** in HTML, such as the dependencies between elements.

3. **Multimodal Fusion**:
   - Visual tokens from ViT and HTML tokens from Flan-T5 are combined into a **unified representation**.
   - The **Flan-T5 decoder** generates actions as free-form text (e.g., `click [button]`, `type [text]`).

---

## Step-by-Step: How the Agent Works
1. **Input**:
   - Receives a **user instruction**, webpage **HTML**, and **screenshot**.

2. **Tokenization**:
   - ViT processes the screenshot into **visual tokens**.
   - Flan-T5 processes the HTML into **text tokens**.

3. **Fusion**:
   - Combines **visual and text tokens** into a unified format.

4. **Action Prediction**:
   - Flan-T5 decoder predicts the next action as free-form text.

5. **Execution**:
   - The predicted action is executed on the webpage.

6. **Iteration**:
   - Repeats the process with updated visual and HTML states until the task is completed.

---

## Benchmarks and Results

### **1. MiniWoB++ (Simulated Web Navigation Benchmark)**
- **Environment**: Simulated web tasks (e.g., booking flights, filling forms).
- **Success Rate**:
  - Previous Offline SoTA (WebN-T5): **48.4%**
  - **WebGUM**: **94.2%** (+45.8%), surpassing humans and RL-based SoTA.

### **2. WebShop (Shopping Task Benchmark)**
- **Environment**: Multi-step product search and selection.
- **Success Rate**:
  - ReAct with PaLM-540B: **40.0%**
  - **WebGUM**: **45.0%**, despite using only 3 billion parameters.

### **3. Mind2Web (Real-World Action Prediction)**
- **Environment**: Real-world tasks on 137 websites.
- **Success Rate**:
  - GPT-4: **35.8%**
  - **WebGUM-XL**: **45.3%**, outperforming GPT-4 and other baselines.

---

## Key Contributions
- Combines **ViT** for visual inputs and **Flan-T5** for text inputs, leveraging their strengths in multimodal tasks.
- Achieves state-of-the-art performance in web navigation tasks through instruction-finetuning and robust multimodal integration.

# WEBDREAMER: Is Your LLM Secretly a World Model of the Internet? Model-Based Planning for Web Agents ✅
[arxiv link](https://arxiv.org/abs/2411.06559)

## How the Agent Works
1. **Input Task and Current State**:
   - The agent receives a task description and observes the current webpage state.

2. **Generate Candidate Actions**:
   - Identifies all possible actions based on the webpage's current elements (e.g., `click`, `type`, `scroll`).

3. **Simulate Outcomes**:
   - Uses an LLM to predict the effects of each action (e.g., "clicking a button will load a new page").

4. **Score Simulations**:
   - Evaluates the predicted outcomes, scoring them based on how well they align with the task objective.

5. **Refine Actions**:
   - Filters out irrelevant or low-scoring actions, leaving the most relevant candidates.

6. **Select and Execute**:
   - Chooses the highest-scoring action and executes it in the real or simulated environment.

7. **Iterative Loop**:
   - Repeats the process until the task is completed or the agent determines further progress is impossible.

8. **Safety and Flexibility**:
   - Simulates actions to avoid unnecessary interactions or irreversible mistakes.

## LLMs Tested
- **GPT-4o**:
  - The primary model used for simulation, scoring, and action refinement.
  - Chosen for its ability to handle multimodal inputs and complex web-based tasks.

## Benchmarks and Results

### 1. VisualWebArena (VWA)
- **Tasks**: 910 tasks across locally hosted websites (Shopping, Classifieds, Reddit).
- **Success Rate**:
  - Reactive Agent: **17.7%**
  - Tree Search: **26.4%**
  - **WEBDREAMER**: **23.6%** (+33.3% improvement over the reactive baseline).

### 2. Mind2Web-live
- **Tasks**: 104 tasks across 69 real-world websites.
- **Success Rate**:
  - Reactive Agent: **22.1%**
  - **WEBDREAMER**: **25.0%** (+13.1% improvement over the reactive baseline).
  - Tree Search: **Not feasible** due to real-world constraints.

## Key Takeaways
- **Performance Gains**: WEBDREAMER outperformed reactive agents consistently.
- **Practicality**: More efficient and safer than tree search in real-world environments.
- **Challenges**: Struggles with long planning horizons due to simulation inaccuracies.


# A Real-World WebAgent with Planning, Long Context Understanding, and Program Synthesis
[arxiv link](https://arxiv.org/abs/2307.12856)

# AGENTOCCAM: A SIMPLE YET STRONG BASELINE FOR LLM-BASED WEB AGENTS ✅

# AutoWebGLM: A Large Language Model-based Web Navigating Agent ✅

# Playwright
[link](https://playwright.dev/)