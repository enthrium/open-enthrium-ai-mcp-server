# OE MCP Server · `@openenterprise/oe-mcp`

**Connect Claude Code, Cursor & Windsurf to 2,600+ enterprise data sources — databases, APIs, files, SSH, messaging, and more. One binary. One YAML config.**

[![npm](https://img.shields.io/npm/v/@openenterprise/oe-mcp?color=0284c7)](https://www.npmjs.com/package/@openenterprise/oe-mcp)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-4f46e5.svg)](https://github.com/openenterprise-info/open-enterprise-ai-mcp-server/blob/main/LICENSE)
[![Website](https://img.shields.io/badge/Website-openenterprise.info-4f46e5)](https://www.openenterprise.info/mcp.html)
[![Discord](https://img.shields.io/badge/Discord-Community-5865F2?logo=discord&logoColor=white)](https://discord.com/invite/vWsZ24Msn)

---

## What is OE MCP?

OE MCP is a standalone binary that implements the [Model Context Protocol (MCP)](https://modelcontextprotocol.io). Define your connectors in a single `oe-mcp.yaml` file and expose them all as tools to your AI coding assistant — no code, no separate servers, no per-connector installs.

Replace 50+ individual MCP servers with one config file.

---

## Quick Start

**1. Create your config file** (`oe-mcp.yaml`)

```yaml
connectors:
  - name: my-postgres
    type: postgresql
    host: localhost
    port: 5432
    database: mydb
    user: postgres
    password: secret

  - name: my-codebase
    type: filesystem
    basePath: /home/user/projects/myapp
```

**2. Add to Claude Code** (`~/.mcp.json`)

```json
{
  "mcpServers": {
    "oe-mcp": {
      "command": "npx",
      "args": ["@openenterprise/oe-mcp", "--stdio", "/path/to/oe-mcp.yaml"]
    }
  }
}
```

**3. Reload Claude Code** — your connectors appear as tools automatically.

---

## Supported Connectors

**2,600+ connectors across 45+ categories:**

| Category | Examples |
|---|---|
| **SQL Databases** | PostgreSQL, MySQL, MSSQL, Oracle, SQLite, Snowflake, BigQuery, Redshift |
| **NoSQL / Cache** | MongoDB, Redis, Elasticsearch, DynamoDB, Cassandra |
| **Object Storage** | AWS S3, GCS, Azure Blob, MinIO, Cloudflare R2 |
| **Cloud Drives** | Google Drive, OneDrive, Dropbox, Box |
| **Filesystem** | Local directories — list, read, write, search |
| **Email** | Gmail, Outlook, Zoho Mail, SMTP |
| **Team Messaging** | Slack, Microsoft Teams, Discord, Telegram |
| **CRM** | HubSpot, Salesforce, Notion, Airtable |
| **Issue Tracking** | GitHub, Jira, GitLab, Linear |
| **REST API** | Any HTTP/REST endpoint |
| **SSH / SFTP** | Remote command execution, file transfer |
| **Message Queues** | Kafka, AWS SQS, Google Pub/Sub, RabbitMQ |
| **+ more** | LDAP, OCR, Image Generation, Healthcare, ERP, Web3, ... |

---

## Transport Modes

| Mode | Flag | Best for |
|---|---|---|
| **stdio** | `--stdio` | Claude Code VS Code extension, Claude Desktop |
| **HTTP** | `--serve --port 4040` | Cursor, Windsurf, shared cloud deployments |

---

## Built-in Memory

Every session includes persistent memory tools:

| Tool | Description |
|---|---|
| `memory_set` | Store a key-value pair across sessions |
| `memory_get` | Retrieve a stored value |
| `memory_list` | List all stored pairs |
| `memory_delete` | Remove a stored key |

---

## Links

- [Full Documentation](https://www.openenterprise.info/mcp.html)
- [GitHub Repository](https://github.com/openenterprise-info/open-enterprise-ai-mcp-server)
- [Discord Community](https://discord.com/invite/vWsZ24Msn)
- [OE Platform](https://www.openenterprise.info/platform.html) — full web app with Agent Builder, RAG, workspaces

---

## License

[Apache-2.0](https://github.com/openenterprise-info/open-enterprise-ai-mcp-server/blob/main/LICENSE) — free to use, modify, and deploy for any purpose including commercial use.
