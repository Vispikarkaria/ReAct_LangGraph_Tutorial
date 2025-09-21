# ReAct with LangGraph + OpenAI

This repository contains a **Jupyter Notebook** tutorial that demonstrates how to implement the **ReAct paradigm** (Reason + Act) using [LangGraph](https://python.langchain.com/docs/langgraph) and the [OpenAI API](https://platform.openai.com/).

---

## 📖 What is ReAct?

**ReAct** (Yao et al., 2022) is a prompting and agent framework where a language model alternates between:

1. **Thought (Reasoning)** — the model plans next steps in natural language.
2. **Action (Tool Call)** — the model decides to call an external tool (e.g., calculator, search).
3. **Observation** — the tool's result is fed back to the model.
4. **Repeat** until the model provides a **Final Answer**.

This approach combines reasoning transparency with reliable grounding through tool use, and it underpins many **AI agent frameworks** today.

---

## 📂 Repository Contents

- `ReAct_LangGraph_OpenAI_Tutorial.ipynb`  
  Main tutorial notebook with code, explanations, and examples.

- `README.md`  
  This file.

---

## ⚙️ Setup

### 1. Clone this repository

```bash
git clone https://github.com/your-username/react-langgraph-openai.git
cd react-langgraph-openai
```

### 2. Create and activate a Python environment

```bash
conda create -n react_env python=3.10 -y
conda activate react_env
```

Or with `venv`:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -U openai langgraph pydantic jupyter matplotlib
```

### 4. Set your OpenAI API key

```bash
export OPENAI_API_KEY="sk-yourkey"   # macOS/Linux
setx OPENAI_API_KEY "sk-yourkey"     # Windows (PowerShell)
```

---

## 🚀 Running the Notebook

1. Start Jupyter:

```bash
jupyter notebook
```

2. Open `ReAct_LangGraph_OpenAI_Tutorial.ipynb`.

3. Run cells step by step. You will learn:

   - How to define tools (`calculator`, `search`)
   - How to expose tools via OpenAI **function-calling**
   - How to wire a **LangGraph StateGraph** with nodes:
     - `model`: calls the OpenAI LLM
     - `tools`: executes tool calls and feeds back results
   - How to loop `Model → Tools → Model → ... → Final Answer`
   - How to run examples (math, retrieval, multi-hop reasoning)

---

## 🧩 Example Usage

### Math with Calculator

**Input:**  
`"What is 23 * 47? Please compute it."`

**Agent steps:**  
- Thought → decide to use calculator  
- Action → `calculator{"query": "23 * 47"}`  
- Observation → `1081`  
- Final Answer → `"1081"`

---

### Retrieval with Search

**Input:**  
`"What is ReAct in language models?"`

**Agent steps:**  
- Thought → need definition  
- Action → `search{"query": "ReAct"}`  
- Observation → `"ReAct combines reasoning traces with tool use in a loop (Yao et al., 2022)."`  
- Final Answer → `"ReAct combines reasoning traces with tool use in a loop (Yao et al., 2022)."`

---

### Multi-hop Query

**Input:**  
`"What is the population of the capital of Canada?"`

**Agent steps:**  
- Thought → identify capital → `"Ottawa"`  
- Action → `search{"query": "Ottawa population"}`  
- Observation → `"Ottawa metro population is ~1,000,000 (approx.)."`  
- Final Answer → `"Ottawa metro population is ~1,000,000 (approx.)."`

---

## 🛡️ Safeguards & Extensions

- **Step limits** (`max_steps`) to prevent infinite loops
- **Input validation** for tools
- **Error handling** when a tool fails
- **New tools** can be added (e.g., unit converter, weather API, web retriever)
- **Streamlit/FastAPI integration** for a UI

---

## 📚 References

- Yao, Shunyu, et al. “ReAct: Synergizing Reasoning and Acting in Language Models.” arXiv preprint arXiv:2210.03629 (2022).  
- [LangGraph Documentation](https://python.langchain.com/docs/langgraph)  
- [OpenAI Function Calling](https://platform.openai.com/docs/guides/function-calling)

---

## 📝 License

MIT License — feel free to use, modify, and share.
