# Vision-Enabled Web Browsing Agent

**Vision-Enabled Web Browsing Agent** is a Python project that implements a web automation agent driven by annotated browser screenshots and language model predictions. The agent leverages state-of-the-art browser automation and large language models (LLMs) to simulate human-like browsing behavior by controlling the mouse and keyboard.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)
- [Contact](#contact)

## Overview

This project integrates several powerful libraries and tools:
- **Playwright**: For browser automation and interaction.
- **LangChain and LangGraph**: To integrate LLMs (via OpenAI Chat models) and manage the conversation flow using a state graph.
- **PIL (Pillow)**: For processing and displaying screenshots.
- **Custom JavaScript (`mark_page.js`)**: To annotate pages with bounding boxes that highlight actionable UI elements.

The agent works by taking a screenshot of the browser, identifying interactive elements, and then deciding which action to take next (e.g., clicking, typing, scrolling) based on LLM predictions. This simulation of human behavior is designed to help avoid detection (e.g., CAPTCHAs) during web automation.

## Features

- **Vision-Enabled Navigation:**  
  The agent captures screenshots of the browser, overlays bounding boxes on UI elements, and uses these annotations to inform action decisions.

- **LLM-Powered Decision Making:**  
  Integrates ChatGPT (via OpenAI’s API) to analyze the current page state and decide on the next best action.

- **Tool Execution:**  
  Supports a variety of actions:
  - **Click:** Simulate mouse clicks on identified UI elements.
  - **Type Text:** Enter text with realistic, human-like typing delays.
  - **Scroll:** Scroll the window or specific elements.
  - **Wait:** Pause execution to mimic human reading time.
  - **Go Back:** Navigate back in browser history.
  - **Navigate to Google:** Quickly jump to `google.com`.

- **State Graph Management:**  
  Uses LangGraph to manage and transition between different agent states and actions.

- **Human-Like Typing Simulation:**  
  The `type_text` function simulates realistic typing by introducing delays between keystrokes, reducing the risk of automated detection.

## Requirements

- Python 3.8 or higher
- [Playwright](https://playwright.dev/python/)
- [LangChain](https://github.com/hwchase17/langchain) and [LangGraph](https://github.com/langgraph/langgraph)
- [Pillow](https://python-pillow.org/)
- Other dependencies as listed in `requirements.txt`

You will also need an OpenAI API key, which should be available as the environment variable `OPENAI_API_KEY`.

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/DonGuillotine/langraph_browser_agent.git
   cd langraph_browser_agent
   ```

2. **Create and activate a virtual environment:**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install the Python dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Install the Playwright browsers:**

   ```bash
   playwright install
   ```

5. **Set the OpenAI API Key:**

   You can either set the environment variable manually:
   
   ```bash
   export OPENAI_API_KEY="your-api-key"  # On Windows use set instead of export
   ```

   Or simply run the script; it will prompt you for the API key if it isn’t set.

## Usage

The main entry point is the `main()` function in your project. When executed, the agent will launch a Chromium browser window, navigate to a starting page (e.g., `google.com`), and execute actions based on the LLM’s predictions.

To run the agent:

```bash
python main.py
```

While running, the agent will display:
- Annotated browser screenshots (using PIL)
- A console log of the actions taken

Example prompt for the agent might be:  
`"Find me the latest news on CNN"`

## Project Structure

- **`main.py`**  
  The main script that sets up the agent, defines the state graph, and orchestrates the LLM-driven actions.

- **`mark_page.js`**  
  A JavaScript file used by Playwright to annotate the current page with bounding boxes for interactive elements.

- **`requirements.txt`**  
  Lists all the required Python packages for the project.

- **`README.md`**  
  This file.

## Customization

- **Typing Simulation:**  
  The `type_text` function simulates human-like typing. You can adjust the delay parameters (or use randomized delays) to further mimic natural typing speeds.

- **LLM Prompt and Output Parsing:**  
  The agent uses a prompt (pulled from `wfh/web-voyager`) and a custom parser to interpret LLM responses. Feel free to modify these to better suit your needs.

- **Tool Configuration:**  
  You can add, remove, or modify tools in the `tools` dictionary in `main.py` to change the agent’s behavior.

## Contributing

Contributions are welcome! If you have suggestions for improvements, bug fixes, or new features, please open an issue or submit a pull request.

When contributing, please ensure:
- Your code follows the existing style.
- Any new features are accompanied by relevant tests or documentation updates.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

- [Playwright](https://playwright.dev/python/)
- [OpenAI](https://openai.com/)
- [LangChain](https://github.com/hwchase17/langchain)
- [LangGraph](https://github.com/langgraph/langgraph)
- [Pillow](https://python-pillow.org/)

## Contact

For questions, suggestions, or contributions, please open an issue in this repository or contact [infect3dlab@gmail.com](mailto:infect3dlab@gmail.com).
