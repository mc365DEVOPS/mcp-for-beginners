<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "affcf199a44f60283a289dcb69dc144e",
  "translation_date": "2025-07-17T13:28:55+00:00",
  "source_file": "03-GettingStarted/02-client/complete_examples.md",
  "language_code": "en"
}
-->
# Complete MCP Client Examples

This directory contains complete, working examples of MCP clients in various programming languages. Each client showcases the full functionality described in the main README.md tutorial.

## Available Clients

### 1. Java Client (`client_example_java.java`)
- **Transport**: SSE (Server-Sent Events) over HTTP
- **Target Server**: `http://localhost:8080`
- **Features**: 
  - Establishing connection and pinging
  - Listing available tools
  - Calculator operations (add, subtract, multiply, divide, help)
  - Error handling and extracting results

**To run:**
```bash
# Ensure your MCP server is running on localhost:8080
javac client_example_java.java
java client_example_java
```

### 2. C# Client (`client_example_csharp.cs`)
- **Transport**: Stdio (Standard Input/Output)
- **Target Server**: Local .NET MCP server via dotnet run
- **Features**:
  - Automatic server startup using stdio transport
  - Listing tools and resources
  - Calculator operations
  - Parsing JSON results
  - Comprehensive error handling

**To run:**
```bash
dotnet run
```

### 3. TypeScript Client (`client_example_typescript.ts`)
- **Transport**: Stdio (Standard Input/Output)
- **Target Server**: Local Node.js MCP server
- **Features**:
  - Full MCP protocol support
  - Operations with tools, resources, and prompts
  - Calculator operations
  - Reading resources and executing prompts
  - Robust error handling

**To run:**
```bash
# First compile TypeScript (if needed)
npm run build

# Then run the client
npm run client
# or
node client_example_typescript.js
```

### 4. Python Client (`client_example_python.py`)
- **Transport**: Stdio (Standard Input/Output)  
- **Target Server**: Local Python MCP server
- **Features**:
  - Async/await pattern for operations
  - Discovering tools and resources
  - Testing calculator operations
  - Reading resource contents
  - Organized with classes

**To run:**
```bash
python client_example_python.py
```

## Common Features Across All Clients

Each client implementation demonstrates:

1. **Connection Management**
   - Connecting to the MCP server
   - Handling connection errors
   - Proper cleanup and resource management

2. **Server Discovery**
   - Listing available tools
   - Listing available resources (where supported)
   - Listing available prompts (where supported)

3. **Tool Invocation**
   - Basic calculator operations (add, subtract, multiply, divide)
   - Help command for server information
   - Correct argument passing and result handling

4. **Error Handling**
   - Connection errors
   - Tool execution errors
   - Graceful failure and user feedback

5. **Result Processing**
   - Extracting text content from responses
   - Formatting output for readability
   - Handling different response formats

## Prerequisites

Before running these clients, make sure you have:

1. **The corresponding MCP server running** (from `../01-first-server/`)
2. **Required dependencies installed** for your chosen language
3. **Proper network connectivity** (for HTTP-based transports)

## Key Differences Between Implementations

| Language   | Transport | Server Startup | Async Model | Key Libraries       |
|------------|-----------|----------------|-------------|--------------------|
| Java       | SSE/HTTP  | External       | Sync        | WebFlux, MCP SDK    |
| C#         | Stdio     | Automatic      | Async/Await | .NET MCP SDK        |
| TypeScript | Stdio     | Automatic      | Async/Await | Node MCP SDK        |
| Python     | Stdio     | Automatic      | AsyncIO     | Python MCP SDK      |

## Next Steps

After exploring these client examples:

1. **Modify the clients** to add new features or operations
2. **Create your own server** and test it with these clients
3. **Experiment with different transports** (SSE vs. Stdio)
4. **Build a more complex application** that integrates MCP functionality

## Troubleshooting

### Common Issues

1. **Connection refused**: Make sure the MCP server is running on the expected port/path
2. **Module not found**: Install the required MCP SDK for your language
3. **Permission denied**: Check file permissions for stdio transport
4. **Tool not found**: Confirm the server implements the expected tools

### Debug Tips

1. **Enable verbose logging** in your MCP SDK
2. **Check server logs** for error messages
3. **Verify tool names and signatures** match between client and server
4. **Test with MCP Inspector** first to validate server functionality

## Related Documentation

- [Main Client Tutorial](./README.md)
- [MCP Server Examples](../../../../03-GettingStarted/01-first-server)
- [MCP with LLM Integration](../../../../03-GettingStarted/03-llm-client)
- [Official MCP Documentation](https://modelcontextprotocol.io/)

**Disclaimer**:  
This document has been translated using the AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). While we strive for accuracy, please be aware that automated translations may contain errors or inaccuracies. The original document in its native language should be considered the authoritative source. For critical information, professional human translation is recommended. We are not liable for any misunderstandings or misinterpretations arising from the use of this translation.