# AI Sticky Notes MCP Server

A simple yet powerful Model Context Protocol (MCP) server that provides AI assistants with persistent sticky note functionality. This server allows AI models to create, read, and manage notes that persist across conversations.

## Features

- **Persistent Notes**: Notes are stored in a local text file and persist between sessions
- **Simple API**: Easy-to-use tools for adding and reading notes
- **Latest Note Access**: Resource endpoint to quickly access the most recent note
- **Smart Summarization**: Built-in prompt for AI to summarize all current notes
- **Auto-initialization**: Automatically creates the notes file if it doesn't exist

## Installation

### Prerequisites

- Python 3.7+
- `fastmcp` library

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/naakaarafr/AI-Sticky-Notes-MCP-Server.git
   cd AI-Sticky-Notes-MCP-Server
   ```

2. Install the required dependency:
   ```bash
   pip install fastmcp
   ```

3. Run the server:
   ```bash
   python main.py
   ```

## Usage

### Tools Available

#### `add_note(message: str)`
Appends a new note to the sticky notes file.

**Parameters:**
- `message` (str): The content of the note to be added

**Returns:**
- Confirmation message: "Note saved!"

**Example:**
```python
add_note("Remember to buy groceries tomorrow")
# Returns: "Note saved!"
```

#### `read_notes()`
Retrieves all notes from the sticky notes file.

**Returns:**
- All notes as a single string, separated by line breaks
- "No notes yet." if no notes exist

**Example:**
```python
read_notes()
# Returns: "Remember to buy groceries tomorrow\nCall dentist for appointment\nFinish project report"
```

### Resources Available

#### `notes://latest`
Provides quick access to the most recently added note.

**Returns:**
- The last note entry
- "No notes yet." if no notes exist

### Prompts Available

#### `note_summary_prompt()`
Generates a prompt asking the AI to summarize all current notes.

**Returns:**
- A formatted prompt string including all notes for summarization
- "There are no notes yet." if no notes exist

## File Structure

```
project-directory/
├── main.py          # Main MCP server implementation
├── notes.txt        # Persistent storage file (auto-created)
└── README.md        # This file
```

## How It Works

1. **File Management**: The server automatically creates a `notes.txt` file in the same directory as `main.py` if it doesn't exist
2. **Note Storage**: Each note is stored as a separate line in the text file
3. **Persistence**: Notes persist between server restarts and AI conversation sessions
4. **MCP Integration**: The server exposes tools, resources, and prompts that AI models can use seamlessly

## Integration with AI Assistants

This MCP server is designed to work with AI assistants that support the Model Context Protocol. Once connected, the AI can:

- Save important information for later reference
- Maintain context across multiple conversations
- Create to-do lists and reminders
- Store research findings or insights
- Keep track of ongoing projects

## Example Use Cases

### Personal Assistant
```
AI: "I'll add that to your notes."
add_note("Meeting with Sarah on Friday at 2 PM")
```

### Research Assistant
```
AI: "Let me save this key finding."
add_note("Study shows 40% improvement in efficiency with new method")
```

### Project Management
```
AI: "I'll note this task for your project."
add_note("TODO: Review and update project timeline by end of week")
```

## Technical Details

- **Framework**: Built using FastMCP for easy MCP server creation
- **Storage**: Simple text file storage for maximum compatibility
- **Error Handling**: Includes file existence checks and graceful error handling
- **Performance**: Lightweight implementation with minimal dependencies

## Customization

You can easily customize this server by:

1. **Changing the storage location**: Modify the `NOTES_FILE` path
2. **Adding note categories**: Extend the `add_note` function to include categories
3. **Implementing search**: Add a new tool to search through notes
4. **Adding timestamps**: Modify notes to include creation timestamps
5. **Implementing note deletion**: Add tools to remove specific notes

## Troubleshooting

### Common Issues

**File Permission Errors**
- Ensure the script has write permissions in its directory
- Check that the directory exists and is accessible

**Import Errors**
- Verify that `fastmcp` is installed: `pip install fastmcp`
- Ensure you're using Python 3.7 or later

**Notes Not Persisting**
- Check that `notes.txt` is being created in the expected location
- Verify file write permissions

## Contributing

This is a simple implementation that can be extended in many ways. We welcome contributions! Some ideas:

- Add note categories or tags
- Implement note search functionality
- Add note deletion capabilities
- Include timestamps for notes
- Create a web interface for note management
- Add note export functionality (JSON, CSV, etc.)

Please feel free to:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For issues or questions about this MCP server, please:
- Create an issue on [GitHub](https://github.com/naakaarafr/AI-Sticky-Notes-MCP-Server/issues)
- Check the FastMCP documentation for general MCP questions
