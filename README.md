# Brave Search MCP Server

[![smithery badge](https://smithery.ai/badge/@arben-adm/brave-mcp-search)](https://smithery.ai/server/@arben-adm/brave-mcp-search)

This project implements a Model Context Protocol (MCP) server for Brave Search, allowing integration with AI assistants like Claude.

## Prerequisites

- Python 3.11+
- [uv](https://github.com/astral-sh/uv) - A fast Python package installer and resolver

## Installation

### Installing via Smithery

To install Brave Search MCP server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@arben-adm/brave-mcp-search):

```bash
npx -y @smithery/cli install @arben-adm/brave-mcp-search --client claude
```

### Manual Installation
1. Clone the repository:
   ```
   git clone https://github.com/your-username/brave-search-mcp.git
   cd brave-search-mcp
   ```

2. Create a virtual environment and install dependencies using uv:
   ```
   uv venv
   source .venv/bin/activate  # On Windows, use: .venv\Scripts\activate
   uv pip install -r requirements.txt
   ```

3. Set up your Brave Search API key:
   ```
   export BRAVE_API_KEY=your_api_key_here
   ```
   On Windows, use: `set BRAVE_API_KEY=your_api_key_here`

## Usage

1. Configure your MCP settings file (e.g., `claude_desktop_config.json`) to include the Brave Search MCP server:

   ```json
   {
     "mcpServers": {
       "brave-search": {
         "command": "uv",
         "args": [
           "--directory",
           "path-to\\mcp-python\\brave-mcp-search\\src",
           "run",
           "server.py"
         ],
         "env": {
           "BRAVE_API_KEY": "YOUR_BRAVE_API_KEY_HERE"
         }
       }
     }
   }
   ```

   Replace `YOUR_BRAVE_API_KEY_HERE` with your actual Brave API key.

2. Start the Brave Search MCP server by running your MCP-compatible AI assistant with the updated configuration.

3. The server will now be running and ready to accept requests from MCP clients.

4. You can now use the Brave Search functionality in your MCP-compatible AI assistant (like Claude) by invoking the available tools.

## Available Tools

The server provides two main tools:

1. `brave_web_search`: Performs a web search using the Brave Search API.
2. `brave_local_search`: Searches for local businesses and places.

Refer to the tool docstrings in `src/server.py` for detailed usage information.

## Development

To make changes to the project:

1. Modify the code in the `src` directory as needed.
2. Update the `requirements.txt` file if you add or remove dependencies:
   ```
   uv pip freeze > requirements.txt
   ```
3. Restart the server to apply changes.

## Troubleshooting

If you encounter any issues:

1. Ensure your Brave API key is correctly set.
2. Check that all dependencies are installed.
3. Verify that you're using a compatible Python version.
4. If you make changes to the code, make sure to restart the server.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
