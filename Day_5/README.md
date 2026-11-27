# Day 5 – Memory, Vector Search (RAG) & Single-Agent Sign-Off

Completed the single-agent architecture by adding **thread-based short-term memory** (`InMemorySaver` + `thread_id`) and **Retrieval-Augmented Generation (RAG)** via **ChromaDB** across both the **Sweet Crumbs Home Bakery** guided build and the **Surya Homoeo Clinic** front-desk assistant.

## What's Inside (`task_5.ipynb`)

### 1. Sweet Crumbs Home Bakery (Guided Build)
- **Knowledge Base (ChromaDB):** Stored 12 bakery policy and FAQ chunks (`delivery`, `payment`, `cancellation`, `photo_cake`, `allergens`, `storage`, `candles`, etc.) inside `sweet_crumbs_faq`.
- **RAG Retrieval Tool (`search_faq`):** Built a semantic search tool that queries ChromaDB (`n_results=3`) so the agent answers policy questions strictly from retrieved documents.
- **Multi-Thread Conversation Memory:** Configured `InMemorySaver()` with `thread_id` (`"ravi"` vs `"sravani"`) so concurrent customer chats stay isolated without mixing up orders or preferences.
- **Updated Evaluation (`tests.csv`):** Added 5 RAG policy and out-of-scope test cases (including allergen checks and `"Do you sell biryani?"` fallback verification).

### 2. Surya Homoeo Clinic Assistant (Custom Build)
- **Clinic Knowledge Base (`surya_clinic_faq`):** Indexed 15 clinic facts covering branch locations, Sunday closures, consultation/follow-up rules, monthly medicine cost ranges, dietary restrictions (avoiding coffee/onion/garlic/mint 30 minutes around doses), pill storage, UPI payments, online follow-ups, and emergency care.
- **Clinic RAG Tool (`search_clinic_faq`):** Built a dedicated semantic lookup tool integrated alongside `get_branch_timings`, `estimate_clinic_cost`, and `log_appointment`.
- **Isolated Multi-Patient Memory:** Tested simultaneous patient threads (`"tharun"` and `"anitha"`) using `InMemorySaver()` to verify accurate context recall per patient.
- **Hallucination & Sign-Off Testing:**
  - Verified graceful refusal (`"I'll check with the doctor."`) on out-of-scope medical equipment queries (e.g., dental X-rays, MRI scans).
  - Executed the complete Single-Agent Sign-Off suite covering fees, timings, dietary rules, storage, payments, and fallback behavior.

## Tech Stack
- **Agent & Memory:** LangChain (`create_agent`, `@tool`), LangGraph (`InMemorySaver`), Groq (`ChatGroq` with `openai/gpt-oss-20b`)
- **Vector Store & Validation:** ChromaDB, Pydantic, Google Sheets (`gspread`)
