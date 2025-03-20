# AI Task Management Agent

The **AI Task Management Agent** is a Python-based application designed to help users manage and prioritize their tasks efficiently. It uses AI/ML logic to auto-assign task priorities, handle task dependencies, and create schedules. The agent can also visualize task dependencies and handle recurring tasks.

---

## Features

1. **Task Prioritization**:
   - Auto-assigns weights to tasks based on deadlines, task type, and urgency.
   - Supports user-defined weights for custom prioritization.

2. **Task Dependencies**:
   - Handles task dependencies using topological sorting.
   - Detects and raises errors for circular dependencies.

3. **Scheduling**:
   - Creates schedules for tasks based on their priorities and deadlines.
   - Supports recurring tasks (e.g., daily standups, weekly reviews).

4. **Visualization**:
   - Visualizes task dependencies using `networkx` and `matplotlib`.

5. **Extensibility**:
   - Modular design makes it easy to add new features (e.g., calendar integration, notifications).

---

## Getting Started

### Prerequisites

- Python 3.8 or higher
- Required Python libraries (see `requirements.txt`)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/task-management-agent.git
   cd task-management-agent

## Usage

### Task Prioritization
```python
from ai_ml_logic.task_prioritization import auto_assign_weight

task = {"description": "Prepare for exam", "deadline": "2023-11-10", "type": "work"}
weight = auto_assign_weight(task["description"], task.get("deadline"), task.get("type"))
print(f"Priority: {weight:.2f}")
```
### Task Dependencies
```python
from ai_ml_logic.task_prioritization import resolve_dependencies

tasks = [
    {"id": 1, "description": "Task 1", "dependencies": []},
    {"id": 2, "description": "Task 2", "dependencies": [1]},
]
ordered_tasks = resolve_dependencies(tasks)
```
### Scheduling
```python
from ai_ml_logic.scheduling import create_schedule

tasks = [
    {"description": "Task 1", "deadline": "2023-11-01", "type": "work"},
    {"description": "Task 2", "deadline": "2023-11-02", "type": "work"},
]
schedule = create_schedule(tasks, "2023-10-25")
```
### Visualization
```python
from ai_ml_logic.visualization import visualize_dependencies

tasks = [
    {"id": 1, "description": "Task 1", "dependencies": []},
    {"id": 2, "description": "Task 2", "dependencies": [1]},
]
visualize_dependencies(tasks)
```
###File structure
```bash
task_management_agent/
├── ai_ml_logic/                  # Core AI/ML logic
│   ├── __init__.py
│   ├── task_prioritization.py    # Auto-assign task weights
│   ├── scheduling.py             # Schedule tasks
│   ├── visualization.py          # Visualize task dependencies
├── data/                         # Data storage
│   ├── raw/                      # Raw data
│   └── processed/                # Processed data
├── utils/                        # Utility functions
│   ├── __init__.py
│   └── data_processing.py        # Data preprocessing
├── tests/                        # Unit and integration tests
│   ├── __init__.py
│   ├── test_task_prioritization.py
│   └── test_scheduling.py
├── config/                       # Configuration files
│   ├── settings.yaml             # General settings
│   └── api_keys.yaml             # API keys for external integrations
├── requirements.txt              # Python dependencies
├── README.md                     # Project documentation
└── main.py                       # Entry point for the application
```