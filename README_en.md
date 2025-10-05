

# ACPM - AI Coding API Provider Manager

![AI Coding Tools](https://img.shields.io/badge/AI%20Coding-Tools-blue)
![API Provider Management](https://img.shields.io/badge/Provider-Manager-green)
![Shell Support](https://img.shields.io/badge/Shell-bash%20%7C%20zsh%20%7C%20fish-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)  

[简体中文](README.md) | [English](README_en.md)

A collection of command-line tools that help manage API providers for various AI coding tools and provide seamless shell integration across bash, zsh, and fish shells.

## Overview

This package contains three tools:

- **`ccm`** - Claude Code Provider Manager for Claude Code API providers
- **`cxm`** - Codex API Provider Manager for Codex API providers
- **`gnm`** - Gemini-cli Provider Manager for Gemini-cli API providers

## Tools

### `ccm` - Claude Code Provider Manager

Claude Code Provider Manager (`ccm`) helps manage Claude Code API providers and automatically updates shell environments.

#### Features
- Manage multiple Claude API providers
- Automatically update environment variables across shells (bash, zsh, fish)
- Interactive configuration setup
- Switch between providers seamlessly

#### Commands
- `ccm init` - Create a template config file
- `ccm ls` - List all configured providers
- `ccm add` - Add a new provider interactively
- `ccm rm <name>` - Remove a provider
- `ccm use <name>` - Switch to a provider and update shell configuration
- `ccm edit` - Edit config file with nvim
- `ccm help` - Show help message

#### Configuration File
- Location: `~/.config/claude/config`
- Format: `name key url`

### `cxm` - Codex Provider Manager

Codex API Provider Manager (`cxm`) manages API providers for Codex.

#### Features
- Manage multiple API providers for Codex
- Generate configuration files for Codex
- Support for different API formats (responses/chat)

#### Commands
- `cxm init` - Create template providers file
- `cxm ls` - List all API providers
- `cxm add` - Add new provider interactively
- `cxm rm <name>` - Remove a provider
- `cxm use <name>` - Switch to provider and update config
- `cxm edit` - Edit providers file with nvim
- `cxm show` - Show current config.toml
- `cxm help` - Show help message

#### Configuration Files
- Providers: `~/.config/codex/providers`
- Format: `name url key model type<response|chat> `

### `gnm` - Gemini-CLI Provider Manager

Gemini-cli Provider Manager (`gnm`) helps manage Gemini-cli API providers and automatically updates shell environments.

#### Features
- Manage multiple Gemini API providers
- Automatically update environment variables across shells (bash, zsh, fish)
- Interactive configuration setup
- Switch between providers seamlessly

#### Commands
- `gnm init` - Create a template config file
- `gnm ls` - List all configured providers
- `gnm add` - Add a new provider interactively
- `gnm rm <name>` - Remove a provider
- `gnm use <name>` - Switch to a provider and update shell configuration
- `gnm edit` - Edit config file with nvim
- `gnm help` - Show help message

#### Configuration File
- Location: `~/.config/gemini/config`
- Format: `name key url`

## Shell Support

All configuration managers support multiple shells:

- **bash** - Updates `.bashrc`
- **zsh** - Updates `.zshrc`
- **fish** - Updates `.config/fish/config.fish`

When you use `ccm use <name>` or `gnm use <name>`, the tools will:
1. Remove old environment variable exports from all supported shell configuration files
2. Add new environment variable exports to all supported shell configuration files
3. Source the appropriate configuration file based on your current shell

## Installation

Place the `ccm`, `cxm`, and `gnm` executables in your PATH (e.g., `/usr/local/bin` or `~/.local/bin`).

## Usage Examples

### Claude Config Manager
```bash
# Initialize configuration
ccm init

# Add a Claude API provider
ccm add

# List providers
ccm ls

# Switch to a provider
ccm use anthropic
```

### Codex API Provider Manager
```bash
# Initialize configuration
cxm init

# Add a provider
cxm add

# Switch to a provider and use Codex
cxm use openrouter
codex
```

### Gemini Config Manager
```bash
# Initialize configuration
gnm init

# Add a Gemini API provider
gnm add

# List providers
gnm ls

# Switch to a provider
gnm use official
```

## Configuration File Format

### Claude and Gemini Config Managers
```
# Comments start with #
name key url

# Example:
anthropic sk-ant-xxx https://api.anthropic.com
official sk-gem-xxx https://generativelanguage.googleapis.com
```

### Codex Provider Manager
```
# Single-line format per provider:
# name url key model type
# example https://api.example.com/v1 sk-xxxxxxxx gpt-5 responses
```

## License

MIT License - see the LICENSE file for details.