# Architecture Diagram Generator Skill

[中文文档](#中文说明) | [English](#architecture-diagram-generator-skill)

This skill empowers AI agents to instantly generate professional, responsive, and visually appealing HTML architecture diagrams from text descriptions. It's perfect for visualizing system designs, workflows, and technical stacks without needing external diagramming tools.

## ✨ Features

- 🏗️ **Professional Layouts**: Automatically organizes content into logical layers (e.g., UI, Business, Data).
- 📱 **Responsive Design**: Generated diagrams adapt to different screen sizes.
- 🎨 **Modern Aesthetics**: Uses a clean, corporate color palette suitable for documentation and presentations.
- 🚀 **Zero Dependencies**: Outputs a single, self-contained HTML file that works in any browser.

## 📦 Installation

You can install this skill into your agent workspace using the `skills` CLI:

```bash
npx skills add Zevi-zzy/arch-diagram-gen-skills
```

## 🎮 Usage

Once installed, you can ask your agent:

> "Generate an architecture diagram for a microservices e-commerce system."
> "Visualize the user login flow as a diagram."
> "Create a technical stack diagram for a React + Node.js application."

The agent will analyze your request and output a complete HTML file that you can save and view.

## 🛠️ Skill Definition

The core logic is defined in `SKILL.md`, which provides the system prompt instructions for the agent to follow when generating the HTML structure and CSS styles.

---

# 中文说明

这个 Skill 赋予 AI Agent 将文本描述即时转化为专业、响应式且美观的 HTML 架构图的能力。非常适合用于可视化系统设计、工作流程和技术栈，无需依赖外部绘图工具。

## ✨ 功能特性

- 🏗️ **专业布局**: 自动将内容组织成逻辑分层（如用户界面层、业务逻辑层、数据层）。
- 📱 **响应式设计**: 生成的图表可适应不同屏幕尺寸。
- 🎨 **现代美学**: 采用简洁、商务的配色方案，适合用于文档和演示。
- 🚀 **零依赖**: 输出单个独立的 HTML 文件，可在任何浏览器中打开。

## 📦 安装

您可以使用 `skills` CLI 将此 Skill 安装到您的 Agent 工作区：

```bash
npx skills add Zevi-zzy/arch-diagram-gen-skills
```

## 🎮 使用方法

安装完成后，您可以直接告诉 Agent：

> "为一个微服务电商系统生成架构图。"
> "将用户登录流程可视化为图表。"
> "为 React + Node.js 应用创建一个技术栈图。"

Agent 将分析您的请求并输出一个完整的 HTML 文件，您可以保存并查看。

## 🛠️ Skill 定义

Skill 的核心逻辑定义在 `SKILL.md` 文件中，它包含了指导 Agent 生成 HTML 结构和 CSS 样式的系统提示指令。

## 📄 License

MIT
