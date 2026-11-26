# Day 4 – Tools, Structured Output & Google Sheets Integration

Upgraded our LangChain assistants with custom Python `@tool` functions, Pydantic schema validation (`with_structured_output`), and live Google Sheets logging via `gspread` in Google Colab—covering both the **Sweet Crumbs Home Bakery** guided build and the **Surya Homoeo Clinic** front-desk booking agent.

## What's Inside (`task_4.ipynb`)

### 1. Sweet Crumbs Home Bakery (Guided Build)
- **Tools (`@tool`):** Built `get_price`, `is_open`, and `log_order` so the agent looks up live prices/timings instead of guessing and logs confirmed orders to Google Sheets.
- **Pydantic Validation (`Order`):** Enforced strict types (`Literal` menu items, `qty >= 1`, `bool` eggless flag) before saving rows.
- **Trace & Edge-Case Testing:** Inspected full execution traces with `pretty_print()` and verified graceful handling of off-menu items (`donut`), missing dates, and invalid quantities (`0`).

### 2. Surya Homoeo Clinic Assistant (Custom Build)
- **Clinic Tools:**
  - `get_branch_timings`: Returns operating hours for **Kakinada** and **Pithapuram** branches (including Sunday closures).
  - `estimate_clinic_cost`: Calculates consultation fees (`Rs 200–300` for new-month visits, `Rs 0` for same-month follow-ups) plus monthly medicine estimates (`Rs 700–800/month`, varying by the patient's health problem).
  - `log_appointment`: Validates booking details with Pydantic and appends confirmed rows to the **Surya Homoeo Appointments** Google Sheet.
- **Structured Output (`Appointment`):** Tested `llm.with_structured_output(Appointment)` across 5 messy patient messages to extract `patient_name`, `branch`, `day`, `new_month`, and `medicines_for_month`.
- **Google Sheet Schema:**
  `patient_name | branch | day | new_month | medicines_for_month | estimated_cost`

## Tech Stack
- **LLM & Framework:** LangChain (`create_agent`, `@tool`, `with_structured_output`), Groq (`ChatGroq` with `openai/gpt-oss-20b`), Pydantic
- **Storage & Environment:** Google Colab, Google Sheets (`gspread`)
