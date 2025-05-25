# MCP Servers Guide

This document provides a comprehensive overview of all Model Context Protocol (MCP) servers available in MCPyATS. Each server exposes specific tools and capabilities through the standardized MCP interface, enabling AI agents to interact with various services and APIs.

## Network Infrastructure Servers

### pyats_mcp_server
**Purpose**: Core network automation using Cisco pyATS framework  
**Key Tools**:
- `run_show_command`: Execute show commands on network devices
- `configure_device`: Apply configuration to devices
- `ping`: Network connectivity testing
- `run_linux_command`: Execute commands on Linux hosts

**Use Cases**: Network device configuration, troubleshooting, validation testing  
**Requirements**: pyATS testbed.yaml configuration file

### aci_mcp
**Purpose**: Cisco Application Centric Infrastructure (ACI) integration  
**Key Tools**: Dynamically generated based on ACI endpoints (tenants, policies, etc.)  
**Use Cases**: Query and manage ACI fabric, tenant management, policy automation  
**Requirements**: APIC URL, username, and password

### ise_mcp
**Purpose**: Cisco Identity Services Engine (ISE) integration  
**Key Tools**: Dynamic tools for endpoints, identity groups, network devices  
**Use Cases**: Security policy management, endpoint profiling, guest access  
**Requirements**: ISE server credentials

### subnet_calculator
**Purpose**: IP subnet calculations and network planning  
**Key Tools**: `calculate_subnet` - Detailed subnet information from CIDR  
**Use Cases**: Network design, IP address planning, subnet validation  
**Requirements**: None (pure Python implementation)

### netbox
**Purpose**: NetBox IPAM/DCIM integration  
**Key Tools**:
- `get_netbox_objects`: Retrieve objects by type
- `search_netbox`: Full-text search
- `get_netbox_object_by_id`: Get specific object

**Use Cases**: IP address management, device inventory, cable documentation  
**Requirements**: NetBox API token

## Visualization & Diagramming Servers

### drawio_mcp
**Purpose**: Draw.io diagram automation with real-time control  
**Key Tools**:
- `create_drawing`: Initialize new diagrams
- `add_cell`: Add shapes to diagrams
- `connect_cells`: Create connections between shapes
- `modify_cell`: Update existing elements

**Use Cases**: Network topology diagrams, architecture visualization, automated documentation  
**Requirements**: Draw.io browser extension, WebSocket connection

### excalidraw
**Purpose**: Excalidraw drawing management  
**Key Tools**:
- `create_excalidraw_drawing`: Create new drawings
- `export_excalidraw_to_json`: Export drawing data

**Use Cases**: Whiteboard-style diagrams, collaborative sketches  
**Requirements**: Node.js environment

### mermaid
**Purpose**: Text-to-diagram conversion using Mermaid syntax  
**Key Tools**: `generate` - Convert Mermaid code to PNG images  
**Use Cases**: Flowcharts, sequence diagrams, state machines, Gantt charts  
**Requirements**: Puppeteer, Chrome/Chromium

### vegalite
**Purpose**: Data visualization using Vega-Lite specifications  
**Key Tools**:
- `save_data_table`: Store data for visualization
- `visualize_data`: Create charts from data

**Use Cases**: Statistical charts, data analysis visualizations  
**Requirements**: Python with vega dependencies

### quickchart
**Purpose**: Quick chart generation via QuickChart.io API  
**Key Tools**:
- `generate_chart`: Create charts using Chart.js syntax
- `download_chart`: Save charts locally

**Use Cases**: Reports, dashboards, data presentations  
**Requirements**: None (uses public API)

## Communication & Collaboration Servers

### slack
**Purpose**: Slack workspace automation  
**Key Tools**:
- `list_channels`: Get available channels
- `post_message`: Send messages
- `add_reaction`: React to messages
- `get_user_info`: Retrieve user details

**Use Cases**: Notifications, automated reporting, team collaboration  
**Requirements**: Slack bot token and team ID

### email
**Purpose**: Email automation via SMTP  
**Key Tools**: `send-email` - Compose and send emails  
**Use Cases**: Alert notifications, report distribution, automated communications  
**Requirements**: SMTP server configuration

### servicenow
**Purpose**: ServiceNow problem management integration  
**Key Tools**:
- `create_problem`: Create new problem records
- `update_problem`: Modify existing problems
- `get_problem_state`: Check problem status

**Use Cases**: Incident management, problem tracking, ITSM automation  
**Requirements**: ServiceNow instance credentials

## Development & Documentation Servers

### github
**Purpose**: GitHub repository automation  
**Key Tools**:
- Repository management (create, fork, update)
- File operations (read, create, update)
- Issues and pull request management
- Code search functionality

**Use Cases**: CI/CD automation, code management, issue tracking  
**Requirements**: GitHub personal access token

### filesystem
**Purpose**: Local file system operations  
**Key Tools**:
- File I/O (read, write, edit)
- Directory management
- File search and information retrieval

**Use Cases**: Configuration management, log analysis, file processing  
**Requirements**: Appropriate file system permissions

### rfc
**Purpose**: IETF RFC document access  
**Key Tools**:
- `get_rfc`: Retrieve full RFC text
- `search_rfcs`: Search RFC database
- `get_rfc_section`: Extract specific sections

**Use Cases**: Standards research, protocol documentation, technical reference  
**Requirements**: None

## Information & Intelligence Servers

### wikipedia
**Purpose**: Wikipedia content retrieval  
**Key Tools**:
- `search`: Find Wikipedia pages
- `get_content`: Retrieve full page content
- `get_summary`: Get page summaries
- `get_links`: Extract page links

**Use Cases**: Research, fact checking, knowledge gathering  
**Requirements**: Python with wikipedia-api

### nist
**Purpose**: NIST National Vulnerability Database access  
**Key Tools**:
- `get_cve`: Retrieve CVE details
- `search_cves`: Search vulnerability database

**Use Cases**: Security assessments, vulnerability tracking, compliance  
**Requirements**: NVD API key (optional for higher rate limits)

### google_search
**Purpose**: Web search automation with CAPTCHA handling  
**Key Tools**: `search` - Parallel Google searches  
**Use Cases**: Information gathering, competitive analysis, research  
**Requirements**: Playwright browser

### google_maps
**Purpose**: Location services via Google Maps API  
**Key Tools**:
- `geocode`: Convert addresses to coordinates
- `reverse_geocode`: Convert coordinates to addresses
- `get_elevation`: Retrieve elevation data

**Use Cases**: Location analysis, mapping, geographic data enrichment  
**Requirements**: Google Maps API key

## AI & Reasoning Servers

### chatgpt
**Purpose**: External AI reasoning using OpenAI GPT-4  
**Key Tools**: `ask_chatgpt` - Send queries to ChatGPT  
**Use Cases**: Complex reasoning, content generation, analysis augmentation  
**Requirements**: OpenAI API key

### sequentialthinking
**Purpose**: Structured problem-solving methodology  
**Key Tools**: `sequential_thinking` - Step-by-step reasoning process  
**Use Cases**: Complex problem breakdown, decision trees, logical analysis  
**Requirements**: None

## Server Categories Summary

1. **Network Infrastructure**: Core networking tools for device management and automation
2. **Visualization**: Tools for creating diagrams and data visualizations
3. **Communication**: Integration with messaging and ticketing platforms
4. **Development**: Code and documentation management tools
5. **Information**: Access to external knowledge bases and databases
6. **AI/Reasoning**: Enhanced cognitive capabilities and problem-solving

Each server runs in its own Docker container and communicates via the MCP protocol, ensuring consistent interfaces and easy integration with AI agents and development tools.