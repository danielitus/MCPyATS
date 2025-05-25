# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MCPyATS is an AI-powered network automation framework that combines Model Context Protocol (MCP) servers, Cisco pyATS, LangGraph, and Agent-to-Agent (A2A) communication. It enables network engineers to automate complex tasks using natural language by orchestrating 20+ specialized tool servers.

## Common Development Commands

### TypeScript/Node.js MCP Servers
Most MCP servers in `mcp_servers/` follow similar patterns:
- Build: `npm run build`
- Development: `npm run dev` or `npm run watch`
- Test: `npm test` (only in drawio_mcp with Jest)
- Lint: `npm run lint` (only in drawio_mcp)
- Format: `npm run format` (only in drawio_mcp)

### Python Components
- pyATS MCP Server: `python pyats_mcp_server.py`
- Streamlit UI: `streamlit run streamlit.py --server.port=8501`
- A2A Agent: `python -m agent`
- LangGraph: `langgraph dev --host 0.0.0.0 --port 2024`

### Docker Operations
- Build all containers: `./docker_startup.sh` (builds and runs entire stack)
- Individual builds: `docker build -t <name> <path>`

### Testing
- Jest tests (drawio_mcp): `npm test`, `npm run test:coverage` (80% threshold)
- Most TypeScript projects use `tsc` for type checking

## High-Level Architecture

### Component Structure
```
MCPyATS/
├── mcp_servers/          # 20+ MCP tool servers (Docker containers)
│   ├── pyats_mcp_server/ # Core network automation via Cisco pyATS
│   ├── drawio_mcp/       # Draw.io integration with WebSocket bridge
│   ├── github/           # GitHub API operations
│   ├── netbox/           # NetBox DCIM integration
│   └── ...               # Other tools (Slack, email, visualization, etc.)
├── mcpyats/              # LangGraph agent (orchestrates MCP tools)
├── a2a/                  # Agent-to-Agent communication adapter
├── streamlit/            # Web UI (port 8501)
└── docker_startup.sh     # One-command startup script
```

### Key Design Patterns

1. **MCP Protocol**: All tools expose standardized interfaces via Model Context Protocol
2. **Dynamic Tool Discovery**: LangGraph agent discovers available tools at runtime
3. **Event-Driven Architecture**: Especially in drawio_mcp with EventEmitter and WebSocket
4. **Modular Containers**: Each tool runs in its own Docker container
5. **Shared Volume**: `/shared` directory for cross-container artifact storage

### Configuration
- Environment variables in `.env` file
- Network topology in `mcp_servers/pyats_mcp_server/testbed.yaml`
- LangGraph configuration in `mcpyats/langgraph.json`

### Important Notes
- The system is designed for Cisco DevNet CML Sandbox
- Requires either OpenAI or Google Gemini API keys
- WebSocket bridge runs on port 3000 for Draw.io integration
- All MCP servers follow similar TypeScript patterns with `index.ts` as entry point