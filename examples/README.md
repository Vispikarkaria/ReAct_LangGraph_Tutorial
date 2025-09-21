# Example Transcripts

This folder contains sample transcripts of the ReAct agent in action.

---

## 🧮 Math Example

**Query:** `What is 23 * 47?`  

**Transcript:**  
- User asks: What is 23 * 47?  
- Assistant decides to call calculator tool.  
- Tool returns: `1081`  
- Assistant answers: `The result is 1081.`

---

## 📖 Retrieval Example

**Query:** `What is ReAct in language models?`  

**Transcript:**  
- User asks: What is ReAct in language models?  
- Assistant calls search tool with query "ReAct".  
- Tool returns: `"ReAct combines reasoning traces with tool use in a loop (Yao et al., 2022)."`  
- Assistant answers with the definition.

---

## 🔄 Multi-hop Example

**Query:** `What is the population of the capital of Canada?`  

**Transcript:**  
- User asks: What is the population of the capital of Canada?  
- Assistant reasons: Capital is Ottawa, so search Ottawa population.  
- Tool returns: `"Ottawa metro population is ~1,000,000 (approx.)."`  
- Assistant answers with the population.
