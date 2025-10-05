
# ACPM - AI 编码 API 提供商管理器

![AI Coding Tools](https://img.shields.io/badge/AI%20Coding-Tools-blue)
![API Provider Management](https://img.shields.io/badge/Provider-Manager-green)
![Shell Support](https://img.shields.io/badge/Shell-bash%20%7C%20zsh%20%7C%20fish-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)

[简体中文](README.md) | [English](README_en.md)

一个命令行工具集合，用于管理不同 AI 服务的 API 配置，并在 bash、zsh 和 fish shell 之间提供无缝的集成。

## 概述

此包包含三个工具：

- **`ccm`** - Claude Code 中转商管理器，用于 Claude Code API 提供商
- **`cxm`** - Codex API 中转商管理器，用于 Codex API 提供商
- **`gnm`** - Gemini-cli 中转商管理器，用于 Gemini-cli API 提供商

## 工具

### `ccm` - Claude Code 中转商管理器

Claude Code 中转商管理器 (`ccm`) 帮助管理 Claude Code API 提供商并自动更新 shell 环境。

#### 特性
- 管理多个 Claude API 中转商
- 自动更新跨 shell 的环境变量（bash、zsh、fish）
- 交互式配置设置
- 无缝切换中转商

#### 命令
- `ccm init` - 创建模板配置文件
- `ccm ls` - 列出所有配置的中转商
- `ccm add` - 交互式添加新中转商
- `ccm rm <name>` - 移除中转商
- `ccm use <name>` - 切换到中转商并更新 shell 配置
- `ccm edit` - 使用 nvim 编辑配置文件
- `ccm help` - 显示帮助信息

#### 配置文件
- 位置: `~/.config/claude/config`
- 格式: `name key url`

### `cxm` - Codex API 中转商管理器

Codex API 中转商管理器 (`cxm`) 管理 Codex 的 API 提供商。

#### 特性
- 管理 Codex 的多个 API 中转商
- 为 Codex 生成配置文件
- 支持不同 API 格式（responses/chat）

#### 命令
- `cxm init` - 创建模板中转商文件
- `cxm ls` - 列出所有 API 中转商
- `cxm add` - 交互式添加新中转商
- `cxm rm <name>` - 移除中转商
- `cxm use <name>` - 切换到中转商并更新配置
- `cxm edit` - 使用 nvim 编辑中转商文件
- `cxm show` - 显示当前 config.toml
- `cxm help` - 显示帮助信息

#### 配置文件
- 中转商: `~/.config/codex/providers`
- 格式：`name url key model type<response|chat> `

### `gnm` - Gemini-cli 中转商管理器

Gemini-cli 中转商管理器 (`gnm`) 帮助管理 Gemini-cli API 提供商并自动更新 shell 环境。

#### 特性
- 管理多个 Gemini API 中转商
- 自动更新跨 shell 的环境变量（bash、zsh、fish）
- 交互式配置设置
- 无缝切换中转商

#### 命令
- `gnm init` - 创建模板配置文件
- `gnm ls` - 列出所有配置的中转商
- `gnm add` - 交互式添加新中转商
- `gnm rm <name>` - 移除中转商
- `gnm use <name>` - 切换到中转商并更新 shell 配置
- `gnm edit` - 使用 nvim 编辑配置文件
- `gnm help` - 显示帮助信息

#### 配置文件
- 位置: `~/.config/gemini/config`
- 格式: `name key url`

## Shell 支持

所有配置管理器都支持多个 shell：

- **bash** - 更新 `.bashrc`
- **zsh** - 更新 `.zshrc`
- **fish** - 更新 `.config/fish/config.fish`

当您使用 `ccm use <name>` 或 `gnm use <name>` 时，工具将：
1. 从所有支持的 shell 配置文件中移除旧的环境变量导出
2. 向所有支持的 shell 配置文件中添加新的环境变量导出
3. 根据当前 shell 源相应的配置文件

## 安装

将 `ccm`、`cxm` 和 `gnm` 可执行文件放入您的 PATH 中（例如 `/usr/local/bin` 或 `~/.local/bin`）。

## 使用示例

### Claude Code 中转商管理器
```bash
# 初始化配置
ccm init

# 添加 Claude API 中转商
ccm add

# 列出中转商
ccm ls

# 切换到中转商
ccm use anthropic
```

### Codex  中转商管理器
```bash
# 初始化配置
cxm init

# 添加中转商
cxm add

# 切换到中转商并使用 Codex
cxm use openrouter
codex
```

### Gemini-CLI 中转商管理器
```bash
# 初始化配置
gnm init

# 添加 Gemini API 中转商
gnm add

# 列出中转商
gnm ls

# 切换到中转商
gnm use official
```

## 配置文件格式

### Claude 和 Gemini 配置管理器
```
# 注释以 # 开头
name key url

# 示例:
anthropic sk-ant-xxx https://api.anthropic.com
official sk-gem-xxx https://generativelanguage.googleapis.com
```

### Codex 中转商管理器
```
# 每个中转商的单行格式:
# name url key model type
# example https://api.example.com/v1 sk-xxxxxxxx gpt-5 responses
```

## 许可证

MIT 许可证 - 详见 LICENSE 文件。