# 📊 Global Superstore Insight Copilot

An AI-powered data assistant built for the Xcaliber Infotech take-home assignment, utilizing **LangGraph**, **Pandas**, and **Gradio**.

## 🚀 Live Demo
You can test the live application here: 
👉 [Live Gradio URL](https://f134982691f6f8dfa7.gradio.live)

## 🛠️ Tech Stack
- **Python & Pandas:** For data loading, filtering, and metric aggregations.
- **LangGraph:** For state management and the agent reasoning workflow (Reasoning -> Tool Execution -> Synthesis).
- **Gradio:** For the interactive web user interface and public deployment.

## 🧠 Architecture Overview
1. **Reasoning Node:** Analyzes the user's natural language question to determine intent (ranked product queries vs. financial summary metrics).
2. **Tool Execution Node:** Dynamically calls custom Pandas data functions using exact dataset columns (`'Product'`, `'Revenue'`, `'Profit'`, `'Cost'`).
3. **Synthesis Node:** Formulates the raw calculation outputs into a clear, professional analyst response.


## 📊 Architecture Diagram
```mermaid
graph TD
    A[Human Message / User Query] --> B[Reasoning Node]
    B -->|Selects Tool & Input| C[Tool Execution Node]
    C -->|Calculations / Query Results| D[Synthesis Node]
    D -->|Plain Language Analyst Insight| E[END / UI Output]
