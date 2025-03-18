# A bare-bones MCP

## Setup

1. Install [`uv`](https://docs.astral.sh/uv/#__tabbed_1_2) for Python project managemenet:

   MacOS / Linux:

   ```bash
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```

   Windows:

   ```bash
   powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
   ```

2. If no `pyporject.toml` file exists, start a new project:

   ```bash
   uv init
   ```
3. Create a virtual environment
   ```bash
   uv venv
   ```

4. Start the virtual environment
   ```bash
   source .venv/bin/activate
   ```

   NOTE: To stop the virtual environment:
   ```bash
   deactivate
   ```

5. Install [MCP Python SDK](https://github.com/modelcontextprotocol/python-sdk):

   ```bash
   uv add "mcp[cli]"
   ```

## Quickstart

1. [Create your MCP using Python](https://modelcontextprotocol.io/introduction)
2. Run your server in the MCP Inspector:
   ```bash
   mcp dev <your_server_name.py>
   ```
3. Install the server in Claude Desktop:
   ```bash
   mcp install <your_server_name.py>
   ```
4. Open `claude_desktop_config.js` in an editor:
   From Claude:

   1. Open Claude
   2. Go to Settings
   3. In the pop-up, select "Developer"
   4. Click "Edit Config"

   File location:
   MacOS / Linux `~/Library/Application/Support/Claude/claude_desktop_config.json`
   Windows `AppData\Claude\claude_desktop_config.json`

5. Find the full path to `uv`:
   MacOS / Linux:
   ```bash
   which uv
   ```
   Windows:
   ```bash
   where uv
   ```
6. In `claude_desktop_config.js`, set the `command` property to the full `uv` path for your MCP Server
   Example:
   ```json
   "weather": {
      "command": "/Users/mrh/.local/bin/uv",
      "args": [
        "run",
        "--with",
        "mcp[cli]",
        "mcp",
        "run",
        "/Users/mrh/Documents/mcp-playground/weather/weather.py"
      ]
    },
   ```
7. Reboot Claude Desktop and use a prompt that will trigger your MCP.
