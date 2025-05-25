# 🧠 MCPyATS: AI-Powered Network Automation

MCPyATS combines Model Context Protocol (MCP), Cisco pyATS, LangGraph, and Agent-to-Agent (A2A) communication to enable natural language network automation through 20+ specialized tool servers.

## 🚀 Quick Start

```bash
# Clone and setup
git clone https://github.com/danielitus/MCPyATS
cd MCPyATS
cp .env.example .env  # Add your API keys
./docker_startup.sh   # Launch all services
```

**Access Points:**
- Web UI: http://localhost:8501
- API: http://localhost:2024
- Draw.io: http://localhost:8080

## 🎯 Usage

**Natural Language Commands** (via Web UI):
- "Show BGP status on router R1"
- "Create network diagram with 3 routers"
- "Send alert to Slack #network-ops"
- "Calculate subnet for 192.168.1.0/24"

**Programmatic Access**:
```python
from a2a.agent.client import Client
client = Client("http://localhost:10000")
response = client.query("Show interface status")
```

## 📦 Available MCP Servers

**Network**: pyATS, ACI, ISE, NetBox, Subnet Calculator  
**Visualization**: Draw.io, Mermaid, Excalidraw, VegaLite, QuickChart  
**Communication**: Slack, Email, ServiceNow  
**Development**: GitHub, Filesystem, RFC  
**Intelligence**: Wikipedia, NIST CVE, Google Search/Maps  
**AI**: ChatGPT, Sequential Thinking

## ⚙️ Configuration

Essential `.env` variables:
```env
# LLM (choose one)
OPENAI_API_KEY=xxx
GOOGLE_API_KEY=xxx

# Network
PYATS_TESTBED_PATH=./mcp_servers/pyats_mcp_server/testbed.yaml

# Services (as needed)
GITHUB_TOKEN=xxx
SLACK_BOT_TOKEN=xxx
```

## 📚 Documentation

- [MCP Servers Guide](./MCP_SERVERS_GUIDE.md) - Detailed server descriptions
- [Architecture](./CLAUDE.md) - Technical overview
- Individual server READMEs in `mcp_servers/*/`

## 🏗️ Architecture

```
MCPyATS/
├── mcp_servers/      # 20+ MCP tool servers
├── mcpyats/          # LangGraph agent orchestrator
├── streamlit/        # Web UI frontend
├── a2a/              # Agent-to-Agent adapter
└── docker_startup.sh # One-command launcher
```

## 🔧 Key Features

- **Natural Language Interface**: Control network infrastructure through conversational AI
- **20+ Tool Integrations**: Network, visualization, communication, and intelligence tools
- **Modular Design**: Each tool runs in its own Docker container
- **Dynamic Discovery**: Agent automatically finds available tools at runtime
- **Multi-Agent Support**: A2A protocol enables collaboration between agents
- **Cisco DevNet Ready**: Pre-configured for CML Sandbox

## 📖 Additional Resources

- **Cisco DevNet Sandbox**: [CML Sandbox](https://devnetsandbox.cisco.com/DevNet/catalog/cml-sandbox_cml)
- **Custom Topology**: Edit `testbed.yaml` in `mcp_servers/pyats_mcp_server/`
- **LLM Options**: Supports OpenAI GPT-4 or Google Gemini (configurable in `mcpyats.py`)