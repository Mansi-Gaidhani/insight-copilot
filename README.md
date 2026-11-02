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


📝 Design Decisions & Trade-Offs
Design Decisions
LangGraph State Graph Architecture: Selected a structured multi-node state graph (Reasoning ➔ Tools ➔ Synthesis) rather than an opaque single LLM call. This ensures explicit control over intent recognition and makes intermediate steps completely transparent and inspectable.

Pandas-Powered Tool Layer: Implemented precise local Python functions leveraging Pandas vectorization for data filtering, aggregation, and financial metric computations (Revenue, Profit, Cost), guaranteeing deterministic numeric accuracy.

Gradio Web Interface: Chose Gradio for rapid deployment to bypass local tunneling issues and instantly generate a reliable, interactive public interface (.gradio.live) accessible without local user setup.

Trade-Offs & Limitations
Rule-Based vs. LLM Router: Used a deterministic keyword-based routing mechanism within the reasoning node for high stability and zero API key dependency, trading off open-ended semantic flexibility for strict execution reliability.

Ephemeral Hosting: The current live URL relies on an active Google Colab runtime session. For permanent production release, the application would be containerized with Docker and hosted on Hugging Face Spaces or Streamlit Community Cloud.

Future Improvements
Integrate a local open-source LLM into the reasoning node to handle complex, multi-intent natural language queries.

Add persistent chat history memory using LangGraph checkpointers to support multi-turn conversational data analysis.
