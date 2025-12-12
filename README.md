# db-mcp

> **⚠️ UNDER DEVELOPMENT** - This project is actively being developed and is not yet ready for production use.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![CodeQL](https://github.com/neverinfamous/db-mcp/actions/workflows/codeql.yml/badge.svg)](https://github.com/neverinfamous/db-mcp/actions/workflows/codeql.yml)

A multi-database **Model Context Protocol (MCP)** server written in TypeScript, featuring OAuth 2.0 authentication, tool filtering, and granular access control.

## Features

- 🔐 **OAuth 2.0 Authentication** - Secure access with token-based authentication
- 🛡️ **Tool Filtering** - Control which database operations are exposed
- 👥 **Access Control** - Limit users to read-only operations or specific databases
- 🗄️ **Multi-Database Support** - Connect to multiple database types simultaneously
- ⚡ **Code Mode Architecture** - Built using the MCP SDK for maximum flexibility

## Architecture

This server is built in **Code Mode** using the official MCP TypeScript SDK, rather than using stdio-based configuration. This architectural choice enables:

| Capability | Benefit |
|---|---|
| **Dynamic Tool Registration** | Register/unregister database tools at runtime based on user permissions |
| **OAuth 2.0 Integration** | Implement authentication middleware before tool execution |
| **Per-Request Context** | Access user identity, scopes, and database restrictions per request |
| **Tool Filtering** | Programmatically control which tools are available to each user |
| **Multi-Tenancy** | Support multiple users with different database access levels |

```typescript
// Code Mode allows programmatic server control
import { Server } from '@modelcontextprotocol/sdk/server';

const server = new Server({
  name: 'db-mcp',
  version: '1.0.0'
});

// Dynamic tool registration based on user permissions
server.setRequestHandler(ListToolsRequestSchema, async (request) => {
  const userScopes = await validateOAuthToken(request);
  return { tools: getToolsForScopes(userScopes) };
});
```


## Supported Databases

| Database | Status | Priority |
|---|---|---|
| SQLite | 🔄 Planned | High |
| MySQL | 🔄 Planned | High |
| PostgreSQL | 🔄 Planned | High |
| MongoDB | 🔄 Planned | High |
| Redis | 🔄 Planned | High |
| SQL Server | 🔄 Planned | Low |

## Installation

```bash
# Coming soon
npm install db-mcp
```

## Usage

```bash
# Coming soon
```

## OAuth 2.0 Access Control

The server supports granular access control through OAuth 2.0 scopes:

| Scope | Description |
|---|---|
| `read` | Read-only access to all databases |
| `write` | Read and write access to all databases |
| `admin` | Full administrative access |

### Planned Features

- **Database-level restrictions** - Limit users to specific databases
- **Table-level restrictions** - Limit users to specific tables within databases
- **Operation-level filtering** - Allow/deny specific SQL operations

## Roadmap

- [ ] Core MCP server implementation
- [ ] SQLite adapter
- [ ] MySQL adapter
- [ ] PostgreSQL adapter
- [ ] MongoDB adapter
- [ ] Redis adapter
- [ ] OAuth 2.0 integration
- [ ] Tool filtering system
- [ ] Access control layer
- [ ] SQL Server adapter

## Contributing

Contributions are welcome! Please read our [Contributing Guidelines](CONTRIBUTING.md) before submitting a pull request.

## Security

For security concerns, please see our [Security Policy](SECURITY.md).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Code of Conduct

Please read our [Code of Conduct](CODE_OF_CONDUCT.md) before participating in this project.
