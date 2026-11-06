# LLM-WebAutomation-Tests

Validate GPT-4-Turbo, GitHub Copilot, GPT-4o with prompt techniques for optimal output

## Overview

This project evaluates and optimizes Large Language Models (LLMs) for generating Cypress test automation code from BDD (Behavior-Driven Development) scenarios. It leverages prompt engineering techniques including zero-shot and few-shot prompting to generate high-quality Cypress test implementations following industry best practices.

## Project Structure

### Files

- **Configuration** file containing:
  - Dataset paths for Cypress BDD scenarios
  - LLM model configurations (GPT-3.5-turbo, GPT-4o)
  - System prompts and examples for Cypress code generation
  - LLM parameters (temperature, top_p, max_tokens)
  - Zero-shot and few-shot prompt templates
  - Examples of:
    - Feature files (BDD scenarios)
    - Step definitions (Cypress step implementations)
    - Page Object classes (UI element locators and methods)

- **Google Colab Jupyter notebook** that:
  - Loads BDD scenarios from a CSV dataset
  - Configures OpenAI API with settings from `configure.json`
  - Tests multiple LLM models with different prompt techniques
  - Generates Cypress test automation code (step definitions and page objects)
  - Evaluates and compares zero-shot vs few-shot prompting approaches
  - Logs and stores generated code for analysis
  - Outputs results back to CSV format

## Key Features

- **Multiple Prompt Techniques**: Evaluates zero-shot and few-shot prompting strategies
- **Model Comparison**: Tests GPT-3.5-turbo and GPT-4o models
- **Best Practices Integration**: Generates code following Cypress and Cucumber best practices
- **BDD Framework Support**: Uses @badeball/cypress-cucumber-preprocessor library
- **Scalable Processing**: Batch processes BDD scenarios and generates corresponding test implementations
- **Result Tracking**: Logs all API responses and generated code for analysis

## Configuration Details

The `configure.json` file includes:

```json
{
  "cypress_input_csv_path": "path/to/cypress-dataset.csv",
  "gpt_3.5_model": "gpt-3.5-turbo-0125",
  "gpt_4_model": "gpt-4o-2024-08-06",
  "gpt_temperature": 0,
  "gpt_top_p": 1,
  "gpt_max_tokens": 3000,
  "system_prompt_code": "You are an expert Cypress Test Automation Engineer...",
  "zero_shot_code": "write step definition and page object class implementation...",
  "few_shot_assistant_feature_code": [...],
  "few_shot_assistant_step_code": [...],
  "few_shot_assistant_page_code": [...]
}
```

## Usage

1. Set up Google Colab environment with the notebook
2. Configure OpenAI API key using Google Colab userdata
3. Update paths in `configure.json` to point to your dataset
4. Run the notebook to generate Cypress test implementations from BDD scenarios
5. Analyze the generated code and output CSV for quality and consistency

## Prerequisites

- Python 3.x
- OpenAI API key
- Google Colab (or local Python environment with similar setup)
- Libraries: openai, pandas, csv

## Output

The notebook generates:
- Cypress test implementations for each BDD scenario
- CSV output with generated code
- Log files with API responses for analysis
