# HTML to Image Skill for Agent

[中文文档](#中文说明) | [English](#html-to-image-skill-for-agent)

This skill allows AI agents to convert local HTML files into high-quality PNG images using the system's installed Google Chrome browser via `puppeteer-core`. This lightweight approach avoids the need to download a separate Chromium binary.

## Features

- 📸 **High-Quality Screenshots**: Captures full-page screenshots of any local HTML file.
- 🚀 **Lightweight**: Uses `puppeteer-core` and connects to your existing Chrome installation.
- 🤖 **Agent-Ready**: Designed to be easily invoked by AI agents (like Trae, Claude, etc.) via the Skills protocol.

## Installation

You can install this skill into your agent workspace using the `skills` CLI:

```bash
npx skills add Zevi-zzy/html-to-image-skills
```

## Prerequisites

1.  **Google Chrome**: Must be installed in the standard location.
    *   macOS: `/Applications/Google Chrome.app`
    *   (The script can be modified for Windows/Linux paths if needed)
2.  **Node.js**: The environment must support running Node.js scripts.

## Usage

Once installed, you can ask your agent to:

> "Convert report.html to an image."
> "Take a screenshot of dashboard.html."

The agent will use the `html-to-image` skill to:
1.  Verify `puppeteer-core` is installed.
2.  Generate a temporary Node.js script.
3.  Launch a headless Chrome instance.
4.  Render the HTML file.
5.  Save it as a PNG image in the same directory.

## Skill Definition

The skill is defined in `SKILL.md`, which provides the prompt engineering instructions for the agent to generate the correct Puppeteer script.

---

# 中文说明

这个 Skill 允许 AI Agent 使用系统已安装的 Google Chrome 浏览器（通过 `puppeteer-core`）将本地 HTML 文件转换为高质量的 PNG 图片。这种轻量级的方法避免了下载庞大的 Chromium 二进制文件。

## ✨ 功能特性

- 📸 **高质量截图**: 对任何本地 HTML 文件进行全网页长截图。
- 🚀 **轻量级**: 使用 `puppeteer-core` 并连接到您现有的 Chrome 安装，无需额外下载。
- 🤖 **Agent 友好**: 专为 AI Agent（如 Trae, Claude 等）设计，通过 Skills 协议轻松调用。

## 📦 安装

您可以使用 `skills` CLI 将此 Skill 安装到您的 Agent 工作区：

```bash
npx skills add Zevi-zzy/html-to-image-skills
```

## 📋 前置要求

1.  **Google Chrome**: 必须安装在标准位置。
    *   macOS: `/Applications/Google Chrome.app`
    *   (如果需要 Windows/Linux 支持，可修改脚本中的路径)
2.  **Node.js**: 您的环境必须支持运行 Node.js 脚本。

## 🎮 使用方法

安装完成后，您可以直接告诉 Agent：

> "帮我把 report.html 转成图片。"
> "把这个 dashboard.html 截图保存下来。"

Agent 将会自动调用 `html-to-image` Skill 执行以下步骤：
1.  验证 `puppeteer-core` 是否已安装。
2.  生成一个临时的 Node.js 脚本。
3.  启动一个无头 Chrome 实例。
4.  渲染 HTML 文件。
5.  将其保存为 PNG 图片到同一目录下。

## 🛠️ Skill 定义

Skill 的核心逻辑定义在 `SKILL.md` 文件中，它包含了指导 Agent 生成正确 Puppeteer 脚本的 Prompt Engineering 指令。

## 📄 许可证

MIT
