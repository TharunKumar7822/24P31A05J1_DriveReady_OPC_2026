# Day 2 – Prompt Structures & Core Python Basics

This notebook covers the fundamentals needed before building LLM applications: structuring chat messages and prompts, working with Python dictionaries and JSON, writing decorators, and handling runtime errors cleanly.

## What's Inside

- **Chat Roles & System Prompts:** Formatting `system`, `user`, and `assistant` message lists, and writing structured system prompts (Role, Facts, Rules, Format) using a bakery assistant example.
- **Few-Shot Prompting:** Passing sample input/output pairs before a user query to guide response style.
- **Dictionaries & JSON:** Storing and updating user/order data in Python dicts, simulating simple key-value memory, and converting between dicts and JSON strings using `json.dumps()` and `json.loads()`.
- **Type Hints & Decorators:** Writing typed helper functions (`get_cake_price`) and wrapping function execution with a custom `@my_decorator`.
- **Error Handling (`try` / `except`):** Catching `ZeroDivisionError`, `ValueError` on user inputs, and `KeyError` when looking up missing items.

## How to Run

No external libraries or API keys are required—everything runs using Python's built-in standard library.

1. Open the `.ipynb` file in **Google Colab** or **Jupyter Notebook**.
2. Run the cells top to bottom (`Shift + Enter`).
3. Enter test inputs when prompted in the `ValueError` cells to see how invalid inputs are caught.
