# Day 6 – Workflows, Planning & LangGraph Routers

Transitioned from a single all-in-one agent to a structured **LangGraph routing workflow** (`StateGraph`, `TypedDict` state, and `add_conditional_edges`) that classifies incoming messages first and delegates them to specialized sub-agents—implemented for both **Sweet Crumbs Home Bakery** and **Surya Homoeo Clinic**.

## What's Inside (`task_6.ipynb`)

### 1. Sweet Crumbs Home Bakery Router (Guided Build)
- **State & Structured Classifier:** Defined `BakeryState` (`message`, `intent`, `reply`) and `Intent` (`Literal["order", "faq", "other"]`) using `llm.with_structured_output(Intent)`.
- **Specialized Sub-Agents:**
  - `faq_agent`: Equipped strictly with `search_faq`, `get_price`, and `is_open` (preventing accidental order creation during policy inquiries).
  - `order_agent`: Equipped strictly with `get_price` and `log_order` to validate and log confirmed cake orders to Google Sheets.
- **Graph Visualization & Streaming:** Built `StateGraph(BakeryState)` with conditional routing, rendered the Mermaid workflow diagram (`draw_mermaid_png()`), and traced node-by-node execution via `graph.stream(..., stream_mode="updates")`.

### 2. Surya Homoeo Clinic Router (Custom Build)
- **Clinic State & Intent Routing:** Defined `ClinicState` and `ClinicIntent` (`Literal["appointment", "faq", "other"]`) to separate patient scheduling from general inquiries.
- **Specialized Clinic Sub-Agents:**
  - `clinic_faq_agent`: Equipped with `get_branch_timings`, `estimate_clinic_cost`, and `search_clinic_faq` to answer questions on branch hours (Kakinada/Pithapuram), consultation/monthly medicine costs, dietary rules, and storage policies without diagnosing symptoms.
  - `clinic_booking_agent`: Equipped with `get_branch_timings`, `estimate_clinic_cost`, and `log_appointment` to validate booking details and append rows to the **Surya Homoeo Appointments** Google Sheet.
- **End-to-End Stream Verification:** Rendered the clinic workflow diagram and verified live node updates across `faq`, `appointment`, and `other` branches.

## Tech Stack
- **Workflow & Agents:** LangGraph (`StateGraph`, `START`, `END`, `add_conditional_edges`), LangChain (`create_agent`, `@tool`, `with_structured_output`), Groq (`ChatGroq` with `openai/gpt-oss-20b`)
- **Vector Store & Storage:** LangChain `InMemoryVectorStore` (`HuggingFaceEmbeddings` with `all-MiniLM-L6-v2`), Pydantic, Google Sheets (`gspread`)
