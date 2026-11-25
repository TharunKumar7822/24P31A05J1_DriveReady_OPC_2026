# Day 3 – LangChain Basics & Clinic Assistant

Rebuilt the Sweet Crumbs assistant using LangChain (`ChatPromptTemplate`, `MessagesPlaceholder`, and `|` chains), created a custom front-desk assistant for **Surya Homoeo Clinic** (Kakinada & Pithapuram branches), evaluated responses against a CSV test suite, and prepared typed Python functions for Day 4 agent tools.

## What's Inside

- **LangChain Chain & Memory:** Built multi-turn conversation chains using `ChatGroq` (`openai/gpt-oss-20b`), `ChatPromptTemplate`, `MessagesPlaceholder`, and `StrOutputParser`.
- **Automated Evaluation:** Tested both the Sweet Crumbs chain (`4/5` passed, 80%) and Surya Homoeo Clinic chain against CSV test suites (`tests.csv` and `surya_tests.csv`), comparing `temperature=0.3` vs `temperature=1.0`.
- **Agent Sneak Peek & Day 4 Prep:** Tested `create_agent` with an empty tool list and wrote two typed, documented helper functions (`estimate_clinic_cost` and `get_branch_timings`) for Day 4 tool calling.
