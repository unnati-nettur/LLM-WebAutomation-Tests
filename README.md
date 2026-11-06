# LLM-WebAutomation-Tests

Built and maintained by [Unnati Nettur](https://github.com/unnati-nettur)

A chained few-shot prompting pipeline that generates complete Cypress test
automation code — step definition files and Page Object Model classes — from BDD
scenarios, and compares it against single-prompt baselines.

Implementation supporting the study:

> "Cypress Copilot: Development of an AI Assistant for Boosting Productivity and
> Transforming Web Application Testing."
> *IEEE Access*, vol. 13, pp. 3215–3229, 2024.
> https://doi.org/10.1109/ACCESS.2024.3521407

## The approach

Rather than asking a model to produce an entire test suite in one call, the pipeline
builds it in two conditioned steps:

1. **Step definitions** — the model is given an example feature file with its
   corresponding step definition code, then generates step definitions for the
   requested BDD scenarios.
2. **Page Object Model classes** — the model is given an example step definition
   paired with its POM class, plus the step definitions produced in step 1, then
   generates the matching POM classes.

Each step conditions on the output of the previous one, which yields more complete
code and fewer syntax errors than requesting everything at once.

## What it evaluates

The notebook reads BDD scenarios from a CSV, runs them through each
model-and-prompt combination, and writes the generated code to CSV for analysis.
Generated code is assessed on:

- **Completeness** — how many generated step and POM methods contain real
  implementations rather than empty stubs
- **Quality** — syntax and runtime errors encountered when the generated code is
  executed with Cypress

Models compared: GPT-4-Turbo, GPT-4o and GitHub Copilot with zero-shot prompting,
against GPT-4o with the chained few-shot technique.

## Repository contents

| File | Purpose |
| --- | --- |
| `cypress_BDD_LLM_Prompt_optimization.ipynb` | Generation, prompt comparison and evaluation |
| `configure.json` | Dataset paths, model settings, LLM parameters and prompt templates |

## Running it

1. Open the notebook in Google Colab or a local Jupyter environment.
2. Set your OpenAI API key.
3. Point `configure.json` at your BDD scenario CSV and set model parameters and
   prompt templates.
4. Run the notebook. Generated step definitions and POM classes are written to CSV,
   alongside API logs for inspection.

### Prerequisites

Python 3, `openai`, `pandas`, and an OpenAI API key. To execute the generated tests
you will also need Node.js, Cypress and `@badeball/cypress-cucumber-preprocessor`.

## Note on language models

Avoid entering personal or sensitive data. Generated test code should be reviewed and
executed in a non-production environment before use.
