# MCP Weather Server

A simple MCP server built following the [official MCP quickstart tutorial](https://modelcontextprotocol.io/docs/develop/build-server).

Exposes two tools:
- **`get_alerts`** — Get active weather alerts for a US state (two-letter code, e.g. `CA`, `TX`)
- **`get_forecast`** — Get a weather forecast for a lat/lon coordinate

Data is sourced from the [US National Weather Service API](https://www.weather.gov/documentation/services-web-api) (US locations only).

## Setup

```bash
# Install uv if you don't have it
curl -LsSf https://astral.sh/uv/install.sh | sh

# Create venv and install deps
uv venv
source .venv/bin/activate
uv add "mcp[cli]" httpx

# Run the server
uv run weather.py
```

## Claude Desktop Config

Add to `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "weather": {
      "command": "uv",
      "args": ["--directory", "/ABSOLUTE/PATH/TO/mcp-weather-server", "run", "weather.py"]
    }
  }
}
```

## Example Queries

- *"What's the weather in Sacramento?"*
- *"What are the active weather alerts in Texas?"*
