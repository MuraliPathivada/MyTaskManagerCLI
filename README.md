Task Tracker CLI

A command-line task management system that allows users to add, update, delete, and view tasks. The tasks are stored in a `tasks.json` file for persistent storage, and each task is associated with a timestamp for creation and updates.

 Features

- Add Task: Add a new task with a description. Each task is automatically assigned a unique ID, default status (`todo`), and timestamps for creation and last update.
- Update Task: Update the description or status of a task by ID.
- Delete Task: Delete a task by its ID.
- Update Task Status: Change the status of a task to one of `todo`, `in-progress`, or `done`.
- List Tasks by Status: Filter and list tasks based on their current status (`todo`, `in-progress`, `done`).
- Display All Tasks: View all tasks in the system, regardless of their status.
- Persistent Storage: Task data is saved to and loaded from a `tasks.json` file, ensuring tasks persist between sessions.
- Custom Date Formatting: The timestamps for task creation and updates are stored in ISO_LOCAL_DATE_TIME format (e.g., `"2025-01-25T14:30:00"`).

## Task Manager Class (`TaskManager.java`)

The `TaskManager` class is responsible for managing all tasks in the system. It provides the core functionality for adding, updating, deleting, and displaying tasks. Tasks are stored in a list and serialized into a JSON file for persistent storage.

### Key Methods

- addTask(String description): Adds a new task with a description. The task is given an auto-incremented ID and saved to the `tasks.json` file.
- updateTask(int id, String newDescription): Updates the description of a task identified by its ID and saves the changes.
- deleteTask(int id): Deletes a task by its ID and updates the `tasks.json` file.
- updateTaskStatus(int id, String status): Updates the status of a task (valid statuses: `todo`, `in-progress`, `done`).
- listTasksByStatus(String status): Lists tasks filtered by their status (`todo`, `in-progress`, `done`).
- displayTasks(): Displays all tasks, regardless of their status.
- saveTasksToFile(): Saves all tasks to the `tasks.json` file in a pretty-printed format using Gson.
- loadTasksFromFile(): Loads tasks from the `tasks.json` file, deserializing them into task objects.

Task Class (`Task.java`)

The `Task` class represents a task in the system. Each task has the following attributes:

- id: A unique identifier for the task.
- description: A brief description of the task.
- status: The current status of the task (default is `todo`).
- createdAt: The timestamp when the task was created (in ISO_LOCAL_DATE_TIME format).
- updatedAt: The timestamp when the task was last updated (in ISO_LOCAL_DATE_TIME format).

### Methods

- getId(): Returns the task's ID.
- getDescription(): Returns the task's description.
- getStatus(): Returns the task's status.
- getCreatedAt(): Returns the creation timestamp.
- getUpdatedAt(): Returns the last update timestamp.
- setDescription(String description): Updates the task's description and updates the `updatedAt` timestamp.
- setStatus(String status): Updates the task's status and updates the `updatedAt` timestamp.
- setUpdatedAt(LocalDateTime updatedAt): Manually sets the update timestamp.
- toString(): Returns a string representation of the task in the following format:
  ```
  Task{id=1, description='Finish homework', status='todo', createdAt=2025-01-25T14:30:00, updatedAt=2025-01-25T14:30:00}
  ```

## Task Tracker CLI Class (`TaskTracker.java`)

The `TaskTracker` class provides the main command-line interface (CLI) for interacting with the task manager. It uses a `Scanner` to read user input and execute the corresponding commands.

### Available Commands

- add: Add a new task (requires description).
- update: Update a task’s description (requires task ID).
- deletetask: Delete a task by ID.
- updatetaskstatus: Update a task's status (requires task ID and new status).
- listbystatus: List tasks filtered by status (`todo`, `in-progress`, `done`).
- display: Display all tasks.
- mark-in-progress: Mark a task as `in-progress` (requires task ID).
- mark-done: Mark a task as `done` (requires task ID).
- exit: Exit the application.
- help: Display available commands.

## JSON Storage

The tasks are stored in a `tasks.json` file. The task data is saved in a human-readable format using Gson for serialization. The file contains an array of tasks, where each task is represented as a JSON object.

## LocalDateTime Adapter (`LocalDateTimeAdapter.java`)

The `LocalDateTimeAdapter` class is used to handle the serialization and deserialization of `LocalDateTime` objects with Gson. It ensures that timestamps are saved and loaded correctly in ISO_LOCAL_DATE_TIME format.

- Serialization: The `write` method converts a `LocalDateTime` object into a string in the format `yyyy-MM-dd'T'HH:mm:ss`.
- Deserialization: The `read` method converts a string back into a `LocalDateTime` object.

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/TaskTracker.git
   cd TaskTracker
   ```

2. Compile the Java files:

   ```bash
   javac com/example/TaskTracker/*.java
   ```

3. Run the program:

   ```bash
   java com.example.TaskTracker.TaskTracker
   ```

## Example

```bash
Enter command: add
Enter task description: Finish homework

Enter command: display
Task{id=1, description='Finish homework', status='todo', createdAt=2025-01-25T14:30:00, updatedAt=2025-01-25T14:30:00}

Enter command: updatetaskstatus
Enter task ID to update status: 1
Enter new status (todo, in-progress, done): in-progress

Enter command: display
Task{id=1, description='Finish homework', status='in-progress', createdAt=2025-01-25T14:30:00, updatedAt=2025-01-25T14:35:00}
```

## Contributing

Feel free to fork the repository, make changes, and cr

project uri - https://github.com/MuraliPathivada/MyTaskManagerCLI
