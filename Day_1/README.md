Sweet Crumbs Bakery Assistant & Prompt Guard Test

A quick Google Colab notebook testing basic system prompts with langchain_groq and checking prompt injection detection using Llama Prompt Guard.

What's Inside

Bakery Customer Assistant (openai/gpt-oss-120b)

Sets up a simple system prompt for a fictional home bakery ("Sweet Crumbs").

Enforces a few basic constraints: 24-hour order notice, eggless options available, no guaranteed delivery times, and keeping replies under 60 words.

Tested with a sample customer query ("can i get my order tommorrow.").

Prompt Injection Check (meta-llama/llama-prompt-guard-2-22m)

Uses the Groq client directly to score a sample jailbreak/injection attempt.

Outputs a confidence score (~0.998 for the test prompt) indicating whether the input is trying to override system instructions.

Setup & Running in Colab

Open the notebook in Google Colab.

Go to the Secrets tab (the key icon on the left sidebar) and add a new secret named GROQ_API_KEY with your Groq API key.

Toggle Notebook access on for the secret.

Run the cells from top to bottom.

Requirements

langchain_groq

groq

A valid Groq API key
