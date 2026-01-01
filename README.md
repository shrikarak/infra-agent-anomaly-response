# AI Agent for IT Infrastructure: Automated Anomaly Response

**Copyright (c) 2026 Shrikara Kaudambady**

This project provides a Jupyter notebook that simulates an AI Agent for IT Operations (AIOps). The agent demonstrates how an automated system can detect, diagnose, and suggest a resolution for a common infrastructure problem, following a classic decision-making framework. This moves beyond simple prediction into the realm of automated reasoning and action.

## The Agent's Workflow: OODA Loop

The agent is designed to follow the **Observe-Orient-Decide-Act (OODA)** loop, a framework for rational decision-making in dynamic environments.

1.  **Observe:** The process starts when the agent detects an anomalous event. In our simulation, this is a sudden, sustained spike in a server's CPU utilization that breaches a predefined threshold.
2.  **Orient:** Once triggered, the agent gathers contextual data to understand the situation. It runs a series of (simulated) diagnostic checks to orient itself:
    - It checks for high-CPU processes (`ps aux`).
    - It searches application logs for recent critical errors (`grep ERROR ...`).
    - It verifies if a recent code deployment could be the cause.
3.  **Decide:** The agent's "brain" consists of a simple, rule-based decision engine. It analyzes the evidence gathered during the orientation phase to determine the most probable root cause. For example: `IF` a Java process has high CPU `AND` a Java `OutOfMemoryError` is in the logs, `THEN` the cause is likely an application memory leak.
4.  **Act:** Based on its decision, the agent takes action. In this simulation, the action is to generate a clear, concise report that includes its findings, the probable cause, and a specific, actionable recommendation for remediation.

## Solution Explanation

The entire simulation is contained within the `anomaly_response_agent.ipynb` Jupyter notebook.

-   **The Trigger:** The notebook begins by programmatically generating a time-series dataset of CPU usage and injecting an anomaly to create the event that the agent will "observe".
-   **Simulated Diagnostics:** A series of Python functions are defined to mimic real-world diagnostic commands. For instance, `check_top_processes()` returns a mock DataFrame of processes, and `check_app_logs()` returns a mock string of log file entries. This allows the notebook to be fully self-contained without needing a live server environment.
-   **The Decision Engine:** The core logic is encapsulated in the `run_anomaly_diagnostics()` function. This function orchestrates the OODA loop, calling the diagnostic functions, applying the decision rules, and compiling a final report.
-   **The Report:** The final output is a human-readable summary of the agent's entire process, demonstrating how it arrived at its conclusion and what it recommends doing next.

This approach provides a powerful demonstration of how AIOps can dramatically reduce the Mean Time to Resolution (MTTR) for common incidents, automating the initial triage and investigation that human operators would otherwise perform manually.

## How to Use

Follow these steps to run the AI agent simulation.

### 1. Clone the Repository
If this project is on a Git repository, clone it to your local machine:
```bash
git clone <repository-url>
cd gemini-cli-projects/infra-agent-anomaly-response
```

### 2. Create a Virtual Environment
It's best practice to use a virtual environment for Python projects.
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
Install the required Python libraries from the `requirements.txt` file.
```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter
Start the Jupyter Notebook server from your terminal.
```bash
jupyter notebook
```
This will open a new tab in your web browser.

### 5. Run the Notebook
Click on the `anomaly_response_agent.ipynb` file to open it. You can execute the cells sequentially to follow the agent's workflow from detection to recommendation.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for full details.
