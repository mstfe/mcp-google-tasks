# Google Tasks MCP Server

A Model Context Protocol (MCP) server for managing Google Tasks.

This TypeScript-based MCP server demonstrates core MCP concepts by integrating with Google Tasks API. It allows managing tasks in a structured and efficient way.

## Features

### Resources
- **Default Task List**: Access tasks in the default Google Tasks list via the URI `tasks://default`.
- **Task Details**: Provides metadata about tasks such as title, notes, and completion status.
- **JSON Mime Type**: Tasks are represented in a machine-readable JSON format.

### Tools
- **`create_task`**: Create a new task in the default task list.
  - Takes `title` (required) and `notes` (optional) as parameters.
  - Stores the task in Google Tasks via the API.
- **`list_tasks`**: List all tasks in the default task list.
  - Returns a structured list of tasks with metadata such as title, notes, and status.

### Functionality
- Provides easy integration with Large Language Models (LLMs) or other applications via MCP.
- Structured tool definitions make task management intuitive and accessible.

## Development

### Install Dependencies
```bash
npm install
```

### Build the Server
```bash
npm run build
```

## Installation

To use with Claude Desktop, add the server configuration:

On MacOS: `~/Library/Application Support/Claude/claude_desktop_config.json`  
On Windows: `%APPDATA%/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "google-tasks": {
      "command": "/path/to/google-tasks/build/index.js"
    }
  }
}
```

## Usage

### Running the Server
To start the server:
```bash
node build/index.js
```

### Available Commands
- `list_tasks`: Retrieve all tasks in the default task list.
- `create_task`: Add a new task with a title and optional notes.

### Example Interactions
- Use `list_tasks` to get a JSON array of all tasks.
- Use `create_task` to add a new task to your list.

## Debugging

Since MCP servers communicate over stdio, debugging requires additional tools. We recommend using the [MCP Inspector](https://github.com/modelcontextprotocol/inspector).

To start the inspector:
```bash
npm run inspector
```

The Inspector will provide a URL to access debugging tools in your browser, making it easier to test and debug the server.

## License

This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License.