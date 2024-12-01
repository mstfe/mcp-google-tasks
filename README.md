# Google Tasks MCP Server

A Model Context Protocol (MCP) server for managing Google Tasks.

This TypeScript-based MCP server demonstrates core MCP concepts by integrating with the Google Tasks API. It allows managing tasks in a structured and efficient way.

---

## Features

### Resources
- **Default Task List**: Access tasks in the default Google Tasks list via the URI `tasks://default`.
- **Task Details**: Provides metadata about tasks such as title, notes, and completion status.
- **JSON Mime Type**: Tasks are represented in a machine-readable JSON format.

### Tools
- **`create_task`**: Create a new task in the default task list.
  - **Parameters**:
    - `title` (string, optional): Title of the task.
    - `notes` (string, optional): Additional notes for the task.
    - `taskId` (string, optional): Unique ID for the task.
    - `status` (string, optional): Status of the task (e.g., "needsAction" or "completed").
  - **Response**: Returns the details of the created task.
- **`list_tasks`**: List all tasks in the default task list.
  - **Parameters**: None.
  - **Response**: Returns a JSON array of all tasks in the default task list.
- **`delete_task`**: Delete a task from the default task list.
  - **Parameters**:
    - `taskId` (string, required): ID of the task to delete.
  - **Response**: Confirms successful deletion of the task.
- **`update_task`**: Update an existing task in the default task list.
  - **Parameters**:
    - `taskId` (string, required): ID of the task to update.
    - `title` (string, optional): New title for the task.
    - `notes` (string, optional): New notes for the task.
  - **Response**: Returns the updated details of the task.
- **`complete_task`**: Toggle the completion status of a task.
  - **Parameters**:
    - `taskId` (string, required): ID of the task to toggle completion status.
  - **Response**: Returns the updated task details, including the new status.

---

## Functionality

- Provides easy integration with Large Language Models (LLMs) or other applications via MCP.
- Structured tool definitions make task management intuitive and accessible.
- Full support for creating, listing, deleting, updating, and toggling the completion status of tasks.

---

## Usage

### Running the Server
To start the server:
```bash
node build/index.js
```

### Available Commands
- **`create_task`**:
  Create a new task with optional parameters.
  ```json
  {
    "title": "Complete project",
    "notes": "Finalize module 3",
    "status": "needsAction"
  }
  ```
- **`list_tasks`**:
  Retrieve all tasks in the default task list.
  - No parameters required.
  - Returns an array of tasks.
- **`delete_task`**:
  Delete a task by its ID.
  ```json
  {
    "taskId": "unique-task-id"
  }
  ```
- **`update_task`**:
  Update a task's title, notes, or other details by its ID.
  ```json
  {
    "taskId": "unique-task-id",
    "title": "Updated task title",
    "notes": "Updated task notes"
  }
  ```
- **`complete_task`**:
  Toggle the completion status of a task.
  ```json
  {
    "taskId": "unique-task-id"
  }
  ```

### Example Response for `complete_task`

#### Before Completion
```json
{
  "taskId": "unique-task-id",
  "title": "Finish the report",
  "status": "needsAction"
}
```

#### After Completion
```json
{
  "taskId": "unique-task-id",
  "title": "Finish the report",
  "status": "completed"
}
```

---

## Debugging

Since MCP servers communicate over stdio, debugging requires additional tools. We recommend using the [MCP Inspector](https://github.com/modelcontextprotocol/inspector).

To start the inspector:
```bash
npm run inspector
```

The Inspector will provide a URL to access debugging tools in your browser, making it easier to test and debug the server.

## License

This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License.