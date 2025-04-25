[![MseeP Badge](https://mseep.net/pr/puravparab-gitingest-mcp-badge.jpg)](https://mseep.ai/app/puravparab-gitingest-mcp)

# Gitingest-MCP ![smithery badge](https://smithery.ai/badge/@puravparab/gitingest-mcp)

An MCP server for [gitingest](https://github.com/cyclotruc/gitingest). This allows MCP clients like Claude Desktop, Cline, Cursor, etc to quickly extract information about Github repositories including

- Repository summaries
- Project directory structure
- File content

<a href="https://glama.ai/mcp/servers/g0dylqhn3h">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/g0dylqhn3h/badge" alt="Gitingest-MCP MCP server" />
</a>

https://github.com/user-attachments/assets/c1fa596b-a70b-4d37-91d9-ea5e80284793

## Table of Contents
- [Installation](#installation)
  - [Installing via Smithery](#installing-via-smithery)
  - [Install via Github](#install-via-github)
  - [Installing Repo Manually](#installing-repo-manually)
  - [Updating the MCP client configuration](#updating-the-mcp-client-configuration)
- [Debug](#debug)


## Installation

### Installing via Smithery

- To install gitingest-mcp via [Smithery](https://smithery.ai/server/@puravparab/gitingest-mcp):

	```bash
	npx -y @smithery/cli@latest install @puravparab/gitingest-mcp --client claude --config "{}" # Claude
 	```
 	```bash
 	npx -y @smithery/cli@latest run @puravparab/gitingest-mcp --client cursor --config "{}" # Cursor
  	```
  	```bash
 	npx -y @smithery/cli@latest install @puravparab/gitingest-mcp --client windsurf --config "{}" # Windsurf
   	```
   	```bash
 	npx -y @smithery/cli@latest install @puravparab/gitingest-mcp --client cline --config "{}" # Cline
	```

### Install via Github

1. Add this to the MCP client config file

	```json
	{
		"mcpServers": {
			"gitingest-mcp": {
				"command": "<path to uv>/uvx",
				"args": [
					"--from",
					"git+https://github.com/puravparab/gitingest-mcp",
					"gitingest-mcp"
				]
			}
		}
	}
	```

### Installing Repo Manually

1. Clone the repo
	```bash
	git clone https://https://github.com/puravparab/Gitingest-MCP
	cd Gitingest-MCP
	```

2. Install dependencies
	```bash
	uv sync
	```

3. Add this to the MCP client config file

	```json
	{
		"mcpServers": {
			"gitingest": {
				"command": "<path to uv>/uv",
				"args": [
					"run",
					"--with",
					"mcp[cli]",
					"--with-editable",
					"<path to gitingest-mcp project>/gitingest_mcp",
					"mcp",
					"run",
					"<path to gitingest-mcp project>/gitingest-mcp/src/gitingest_mcp/server.py"
				]
			}
		}
	}
	```

5. If you have issues, follow this [MCP server documentation](https://modelcontextprotocol.io/quickstart/server)

### Updating the MCP client configuration

1. Add to Claude Desktop

	Open config file in your IDE
	```bash
	cursor ~/Library/Application\ Support/Claude/claude_desktop_config.json
	```
	```bash
	code ~/Library/Application\ Support/Claude/claude_desktop_config.json
	```

## Debug

1. Using mcp inspector
	```
	uv run mcp dev src/gitingest_mcp/server.py
	```
