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
### File structure
```bash
task_management_agent/                     # Root directory for the project
├── ai_ml_logic/                           # Core AI/ML logic for task management
│   ├── __init__.py                        # Makes the directory a Python package
│   ├── task_prioritization.py             # Logic for auto-assigning task weights
│   ├── scheduling.py                      # Logic for scheduling tasks
│   └── visualization.py                   # Logic for visualizing task dependencies
├── utils/                                 # Utility functions and helpers
├── tests/                                 # Directory for unit and integration tests
│   ├── __init__.py                        # Makes the directory a Python package
│   ├── test_task_prioritization.py        # Tests for task prioritization logic
│   ├── test_scheduling.py                 # Tests for scheduling logic
│   ├── test_visualization.py              # Tests for visualization logic
│   ├── test_dependencies.py               # Tests for task dependency resolution
│   └── integration/                       # Directory for integration tests
│       ├── test_integration.py            # Tests for end-to-end functionality
│       └── test_circular_dependencies.py  # Tests for handling circular dependencies
├── config/                                # Directory for configuration files
│   ├── settings.yaml                      # General settings (e.g., default weights, paths)
│   └── api_keys.yaml                      # API keys for external integrations
├── htmlcov/                               # Directory for generated coverage reports
│   ├── index.html                         # Main HTML file for viewing the coverage report
│   ├── coverage.css                       # CSS file for styling the coverage report
│   ├── coverage.js                        # JavaScript file for the coverage report
│   └── ...                                # Other files generated by the coverage tool
├── scripts/                               # Directory for utility scripts
├── requirements.txt                       # Lists Python dependencies for the project
├── README.md                              # Project documentation and usage instructions
└── main.py                                # Entry point for the application
```