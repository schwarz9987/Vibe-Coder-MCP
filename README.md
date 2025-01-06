# Vibe Coder MCP Server

[![npm version](https://img.shields.io/npm/v/vibe-coder-mcp?style=flat-square&logo=npm&logoColor=white&cacheSeconds=300)](https://www.npmjs.com/package/vibe-coder-mcp)
[![npm downloads](https://img.shields.io/npm/dm/vibe-coder-mcp?style=flat-square&logo=npm&logoColor=white&cacheSeconds=300)](https://www.npmjs.com/package/vibe-coder-mcp)
[![npm total downloads](https://img.shields.io/npm/dt/vibe-coder-mcp?style=flat-square&logo=npm&logoColor=white&cacheSeconds=300)](https://www.npmjs.com/package/vibe-coder-mcp)
[![GitHub release](https://img.shields.io/github/v/release/freshtechbro/Vibe-Coder-MCP?style=flat-square&logo=github&logoColor=white&cacheSeconds=300)](https://github.com/freshtechbro/Vibe-Coder-MCP/releases)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen.svg?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square&logo=opensourceinitiative&logoColor=white)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/freshtechbro/Vibe-Coder-MCP?style=flat-square&logo=github&logoColor=white&cacheSeconds=300)](https://github.com/freshtechbro/Vibe-Coder-MCP/stargazers)

Vibe Coder is an MCP (Model Context Protocol) server designed to supercharge your AI assistant (like Cursor, Cline AI, or Claude Desktop) with powerful tools for software development. It helps with research, planning, generating requirements, creating starter projects, and more!

## 🆕 What's New in Version 0.3.5

### 🎉 Latest Release - Enhanced CLI, REPL, and Parameter Extraction

**Major Improvements:**
- **✨ Complete Hybrid Matcher Overhaul**: All 15 MCP tools now have comprehensive parameter extraction
- **🚀 CLI/REPL Experience**: Interactive confirmations, job status polling with visual progress
- **🔧 Fixed Critical Bugs**: Task-list-generator auto-generates user stories, multi-turn conversations work flawlessly
- **📊 Better Tool Matching**: Multi-strategy approach (keyword 35%, pattern 30%, semantic 15%, LLM 20%)
- **⚡ TypeScript Strict Mode**: Zero `any` types, all explicit typing, production-grade code quality

**User Experience Enhancements:**
- Low-confidence matches now prompt for user confirmation
- Visual progress indicators for long-running jobs
- Cleaner output with JSON log filtering in interactive mode
- Session persistence across commands
- Enhanced error messages and validation feedback

### Previous Notable Releases

#### Version 0.3.1 - Global Installation & Synchronization
- Fixed global/local version synchronization issues
- Enhanced clean build process for installations
- Improved packaging workflow for NPM publication

#### Version 0.2.8 - CLI Interactive Mode
- Fixed configuration persistence in interactive mode
- Enhanced project root detection for CLI users
- Improved context-aware configuration

#### Version 0.2.3 - Interactive REPL & Setup Wizard

- **Interactive REPL Mode** with chat-style interface and session persistence
- **Enhanced Setup Wizard** with automatic first-run detection
- **Configuration Templates** in `src/config-templates/`
- **Performance Improvements** with optimized memory usage
- **Unified CLI Binary** - single `vibe` command for all operations


## 🚀 Quick Start

```bash
# Install globally (recommended)
npm install -g vibe-coder-mcp@latest

# Run setup wizard on first use
vibe --setup

# Or use instantly with npx (no installation)
npx vibe-coder-mcp@latest --setup
```

**The setup wizard will:**
1. ✅ Configure your OpenRouter API key
2. ✅ Set up project directories
3. ✅ Create configuration files from templates
4. ✅ Validate your environment
5. ✅ Get you ready to use all features!

## 📦 Installation

[![npm version](https://img.shields.io/npm/v/vibe-coder-mcp)](https://www.npmjs.com/package/vibe-coder-mcp)
[![npm downloads](https://img.shields.io/npm/dm/vibe-coder-mcp)](https://www.npmjs.com/package/vibe-coder-mcp)

```bash
# Recommended: Install globally for the 'vibe' command
npm install -g vibe-coder-mcp@latest

# Or run instantly without installation
npx vibe-coder-mcp@latest
```

### Installation Methods

**Global Installation (Recommended)**
```bash
npm install -g vibe-coder-mcp@latest

# Use the 'vibe' command anywhere
vibe                                    # Start MCP server
vibe "create a PRD for a todo app"     # CLI mode
vibe --interactive                     # Interactive REPL mode
vibe --setup                           # Setup wizard
```

**Quick Run with npx**
```bash
# No installation needed
npx vibe-coder-mcp@latest
npx vibe-coder-mcp@latest "research React best practices"
```

**Local Project Installation**
```bash
npm install vibe-coder-mcp
npx vibe-coder-mcp "map the codebase structure"
```

### Command Line Usage

```bash
# MCP Server Mode (for Claude Desktop, Cursor, etc.)
vibe                                    # Start with stdio transport
vibe --sse                             # Start with Server-Sent Events

# CLI Mode - Natural Language Commands
vibe "research modern JavaScript frameworks"
vibe "create a PRD for an e-commerce platform"
vibe "map the codebase structure" --json
vibe "generate user stories for auth system"

# Interactive REPL Mode
vibe --interactive                     # Chat interface with context retention

# Configuration
vibe --setup                           # Run setup wizard
vibe --help                            # Show all options
vibe --version                         # Show version
```

**Interactive Mode Features:**
- Chat-style conversation with context retention
- Live tool execution with progress indicators
- Session persistence and history
- Markdown rendering support
- Multiple themes and customization
- Slash commands for quick actions

## 🎯 MCP Client Integration (Claude Desktop, Cursor, Cline AI)

### Quick Integration Guide

Vibe-Coder MCP integrates seamlessly with any MCP-compatible client. Here's how to configure it:

#### Option 1: Using NPX (Recommended)
In your MCP client's server configuration dialog:
- **Server Name**: `vibe-coder-mcp`
- **Command/URL**: `npx`
- **Arguments**: `vibe-coder-mcp`
- **Environment Variables**:
  - `OPENROUTER_API_KEY`: Your OpenRouter API key (required)
  - `VIBE_PROJECT_ROOT`: `/path/to/your/project` (required)
  - `LOG_LEVEL`: `info` (optional)
  - `NODE_ENV`: `production` (optional)

#### Option 2: Global Installation
```bash
# First install globally
npm install -g vibe-coder-mcp
```
Then configure:
- **Command/URL**: `vibe`
- **Arguments**: (leave empty)
- **Environment Variables**: Same as Option 1

#### Option 3: Node with Full Path
- **Command/URL**: `node`
- **Arguments**: `/path/to/node_modules/vibe-coder-mcp/build/index.js`
- **Environment Variables**: Same as Option 1

### Claude Desktop Specific Configuration

For Claude Desktop users, add this to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "vibe-coder-mcp": {
      "command": "npx",
      "args": ["vibe-coder-mcp"],
      "env": {
        "OPENROUTER_API_KEY": "your-openrouter-api-key",
        "VIBE_PROJECT_ROOT": "/path/to/your/project",
        "LOG_LEVEL": "info",
        "NODE_ENV": "production"
      }
    }
  }
}
```

See `example_claude_desktop_config.json` for a complete example.

### Available Tools After Integration

Once configured, your MCP client will have access to:
- **vibe-task-manager**: AI-native task management with RDD methodology
- **research-manager**: Deep research using Perplexity integration
- **map-codebase**: Advanced codebase analysis (35+ languages)
- **curate-context**: Intelligent context curation for AI development
- **generate-prd**: Product requirements document generator
- **generate-user-stories**: User story generator  
- **generate-task-list**: Task list generator
- **generate-fullstack-starter-kit**: Project scaffolding tool
- **run-workflow**: Multi-step workflow execution

### Testing Your Integration

After configuration, test by asking your AI assistant:
- "Use vibe to research React best practices"
- "Map the codebase for this project"
- "Generate a PRD for a task management app"

## 🆕 Unified Project Root Configuration

### Zero Configuration for CLI Users
```bash
# Automatic project detection - just run from your project!
cd /path/to/your/project
vibe "map the codebase structure"
```

### Simple Configuration for MCP Clients
```json
{
  "env": {
    "OPENROUTER_API_KEY": "your_key_here",
    "VIBE_PROJECT_ROOT": "/path/to/your/project"
  }
}
```

- **One Variable**: `VIBE_PROJECT_ROOT` replaces multiple directory configs
- **Auto-Detection**: CLI automatically detects project root
- **Backward Compatible**: Legacy variables still supported

## 🔧 Environment Configuration

**Required:** You need an OpenRouter API key to use Vibe Coder MCP.

### Get Your OpenRouter API Key
1. Visit [openrouter.ai](https://openrouter.ai/)
2. Create an account if you don't have one
3. Navigate to API Keys section
4. Create a new API key and copy it

### Set Up Environment Variables

**Option 1: Using Setup Wizard (Recommended for v0.2.3+)**
```bash
# Run the interactive setup wizard
vibe --setup

# The wizard will:
# • Configure your OpenRouter API key
# • Set up project directories
# • Create configuration files
# • Validate your setup
```

**Option 2: Environment Variables**
```bash
# Set your OpenRouter API key
export OPENROUTER_API_KEY="your_api_key_here"

# Optional: Set custom directories
export VIBE_CODER_OUTPUT_DIR="/path/to/output/directory"
export VIBE_PROJECT_ROOT="/path/to/your/project"

# Legacy variables (still supported for backward compatibility)
export CODE_MAP_ALLOWED_DIR="/path/to/your/source/code"
export VIBE_TASK_MANAGER_READ_DIR="/path/to/your/project"
```

**Option 3: Create .env file (templates provided in v0.2.3+)**
Create a `.env` file in your working directory (or copy from `src/config-templates/.env.template`):
```dotenv
# Required: Your OpenRouter API key
OPENROUTER_API_KEY="your_api_key_here"

# Optional: Unified project root configuration
VIBE_CODER_OUTPUT_DIR="/path/to/output/directory"
VIBE_PROJECT_ROOT="/path/to/your/project"
VIBE_USE_PROJECT_ROOT_AUTO_DETECTION="true"

# Legacy variables (still supported for backward compatibility)
CODE_MAP_ALLOWED_DIR="/path/to/your/source/code"  
VIBE_TASK_MANAGER_READ_DIR="/path/to/your/project"

# Optional: Other settings
OPENROUTER_BASE_URL="https://openrouter.ai/api/v1"
GEMINI_MODEL="google/gemini-2.5-flash-preview-05-20"
```

### Directory Configuration (Unified & Simplified)

**🆕 Unified Configuration (Recommended)**
- **VIBE_PROJECT_ROOT**: Single variable for all project operations (automatic detection enabled by default for CLI)
- **VIBE_USE_PROJECT_ROOT_AUTO_DETECTION**: Enable automatic project root detection for CLI users (default: `"true"`)
- **VIBE_CODER_OUTPUT_DIR**: Where generated files are saved (default: `./VibeCoderOutput/`)

**Legacy Configuration (Still Supported)**
- **CODE_MAP_ALLOWED_DIR**: Security boundary for code analysis (fallback if VIBE_PROJECT_ROOT not set)
- **VIBE_TASK_MANAGER_READ_DIR**: Security boundary for task manager operations (fallback if VIBE_PROJECT_ROOT not set)

**Auto-Detection Benefits:**
- **Zero Configuration**: CLI users get automatic project root detection
- **Context Aware**: Different behavior for CLI vs MCP client usage
- **Intelligent Fallbacks**: 5-priority resolution chain ensures reliable operation

## 🔌 MCP Client Setup

Configure your AI assistant to connect to Vibe Coder MCP:

### For Cursor AI / Windsurf / VS Code MCP Clients

Add this to your MCP settings (usually in `settings.json`):

```json
{
  "mcpServers": {
    "vibe-coder-mcp": {
      "command": "npx",
      "args": ["vibe-coder-mcp"],
      "env": {
        "OPENROUTER_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### For Claude Desktop

Add this to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "vibe-coder-mcp": {
      "command": "npx",
      "args": ["vibe-coder-mcp"],
      "env": {
        "OPENROUTER_API_KEY": "your_api_key_here",
        "VIBE_PROJECT_ROOT": "/path/to/your/project"
      }
    }
  }
}
```

## 💻 CLI Usage Guide

Vibe Coder includes a powerful command-line interface with multiple modes for direct interaction with all tools.

### Interactive Setup Wizard (Enhanced in v0.2.3)
```bash
# First-time setup (runs automatically on first use)
vibe --setup

# Features:
# • Smart first-run detection
# • OS-specific configuration paths
# • Non-interactive mode for CI/CD
# • Configuration validation
# • Backup system for existing configs

# Reconfigure existing installation
vibe --reconfigure
```

### Interactive REPL Mode (NEW in v0.2.3!)
```bash
# Start interactive chat session
vibe --interactive

# Or with alias
vibe -i

# Resume a previous session
vibe --resume <session-id>
```

**REPL Features:**
- 🎯 **Chat Interface**: Natural conversation flow with context retention
- 📝 **Multi-line Input**: Use `"""` for multi-line messages
- 🎨 **Themes**: Multiple color themes with `/theme` command
- 💾 **Session Management**: Auto-save and resume capabilities
- 📊 **Markdown Rendering**: Rich text formatting in responses
- ⚡ **Live Progress**: Real-time execution feedback
- 🔧 **Slash Commands**: Quick actions like `/tools`, `/history`, `/save`
- 🎮 **Auto-completion**: Tab completion for commands and tools

### CLI Command Examples

#### Research & Analysis
```bash
vibe "research modern React patterns and best practices"
vibe "analyze current trends in microservices architecture"
vibe "research security best practices for Node.js APIs"
```

#### Project Planning
```bash
vibe "create a PRD for an e-commerce platform with user authentication"
vibe "generate user stories for authentication system"
vibe "create development tasks from user stories"
```

#### Code Analysis & Generation
```bash
vibe "map the codebase structure"
vibe "create context for implementing authentication"
vibe "generate a fullstack starter kit for e-commerce"
vibe "create coding standards for TypeScript projects"
```

#### Task Management
```bash
vibe "create a new project for building a todo app"
vibe "list all my projects"
vibe "show project status for MyApp"
vibe "create high priority task for implementing OAuth"
```

### CLI Options
```bash
# Output formats
vibe "research React hooks" --json
vibe "create PRD for todo app" --yaml

# Verbosity control
vibe "create project MyApp" --verbose
vibe "research Node.js patterns" --quiet

# Interactive REPL mode (NEW!)
vibe --interactive
vibe -i

# Session management (NEW!)
vibe --resume <session-id>
vibe --list-sessions
```

### Interactive REPL Commands (v0.2.3+)
Once in interactive mode (`vibe --interactive`), use these commands:

```bash
# Help and navigation
/help              # Show available commands
/tools             # List all MCP tools
/status            # Show session status

# Session management
/save              # Save current session
/sessions          # List saved sessions
/export [file]     # Export session to markdown

# Conversation control
/clear             # Clear conversation history
/history           # Show conversation history

# Customization
/theme             # Change color theme
/markdown          # Toggle markdown rendering
/config            # Manage configuration

# Exit
/quit or /exit     # Exit interactive mode
```

### File Organization
Generated files are automatically organized in `VibeCoderOutput/`:
```
VibeCoderOutput/
├── research/                    # Research reports
├── prd-generator/              # Product requirements
├── user-stories-generator/     # User stories
├── task-list-generator/        # Development tasks
├── fullstack-starter-kit-generator/  # Project templates
├── map-codebase/              # Code analysis
├── vibe-task-manager/         # Task management data
└── workflow-runner/           # Workflow outputs
```

---

## 🔄 Migration Guide (v0.2.3)

### Breaking Changes

**None!** Version 0.2.3 is fully backward compatible. All existing configurations and workflows continue to work.

### Technical Improvements

- Unified CLI architecture with single entry point
- Better error handling and recovery
- Improved resource cleanup
- Enhanced type safety throughout codebase
- Memory leak prevention in long-running sessions
- **CI/CD Pipeline Optimization**:
  - 70% faster execution (~3 minutes vs ~10 minutes)
  - Focused on essential checks: type-check, lint, build
  - Unit tests moved to local development workflow
  - See [CI/CD Guide](./CI_CD_GUIDE.md) for details
- Memory usage optimized for large codebases
- Faster first-run experience with smart detection

---

## 📚 Development Setup (Advanced)

If you want to contribute to development or run from source, follow the detailed setup guide below.

## Overview & Features

Vibe Coder MCP integrates with MCP-compatible clients to provide the following capabilities:

### 🚀 **Core Architecture**
*   **Quad Transport Support**: stdio, SSE, WebSocket, and HTTP transport protocols for maximum client compatibility
*   **Dynamic Port Allocation**: Intelligent port management with conflict resolution and graceful degradation
*   **Semantic Request Routing**: Intelligently routes requests using embedding-based semantic matching with sequential thinking fallbacks
*   **Tool Registry Architecture**: Centralized tool management with self-registering tools
*   **Unified Communication Protocol**: Agent coordination across all transport mechanisms with real-time notifications
*   **Session State Management**: Maintains context across requests within sessions

### 🧠 **AI-Native Task Management**
*   **Vibe Task Manager**: Production-ready task management with 99.9% test success rate and comprehensive integration *(Functional but actively being enhanced)*
*   **Natural Language Processing**: 21 supported intents with multi-strategy recognition (pattern matching + LLM fallback)
*   **Recursive Decomposition Design (RDD)**: Intelligent project breakdown into atomic tasks
*   **Agent Orchestration**: Multi-agent coordination with capability mapping, load balancing, and real-time status synchronization
*   **Multi-Transport Agent Support**: Full integration across stdio, SSE, WebSocket, and HTTP transports
*   **Real Storage Integration**: Zero mock code policy - all production integrations
*   **Artifact Parsing Integration**: Seamless integration with PRD Generator and Task List Generator outputs
*   **Session Persistence**: Enhanced session tracking with orchestration workflow triggers
*   **Comprehensive CLI**: Natural language command-line interface with extensive functionality

### 🔍 **Advanced Code Analysis & Context Curation**
*   **Code Map Tool**: 35+ programming language support with 95-97% token reduction optimization
*   **Context Curation Tool**: Language-agnostic project detection with 95%+ accuracy across 35+ languages
*   **Intelligent Codemap Caching**: Configurable caching system that reuses recent codemaps to optimize workflow performance
*   **Enhanced Import Resolution**: Third-party integration for accurate dependency mapping
*   **Multi-Strategy File Discovery**: 4 parallel strategies for comprehensive analysis
*   **Memory Optimization**: Sophisticated caching and resource management
*   **Security Boundaries**: Separate read/write path validation for secure operations

### 📋 **Research & Planning Suite**
*   **Research Tool**: Deep research using Perplexity Sonar via OpenRouter
*   **Context Curation**: Intelligent codebase analysis with 8-phase workflow pipeline and intelligent codemap caching for AI-driven development
*   **Document Generators**: PRDs (`prd-generator`), user stories (`user-stories-generator`), task lists (`task-list-generator`), development rules (`rules-generator`)
*   **Project Scaffolding**: Full-stack starter kits (`fullstack-starter-kit-generator`) with dynamic template generation
*   **Workflow Execution**: Predefined sequences of tool calls defined in `workflows.json`

### ⚡ 