# ReifyFlow Studio

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Status: Preview](https://img.shields.io/badge/Status-Preview-orange.svg)]()
[![Platform: VS Code](https://img.shields.io/badge/Platform-VS%20Code-blueviolet.svg)]()

> **The Interactive Workbench for the ReifyFlow Ecosystem.**
>
> **ReifyFlow 的可视化交互工作台。**

`reify-studio` 是 ReifyFlow 生态系统的**用户交互层 (Frontend Layer)**。它提供了一个沉浸式的图形化界面，让工程师能够以 **“上帝视角”** 编排硬件资源、验证软件架构，并实时监控物理设备的运行状态。

目前，它主要以 **VS Code Extension** 的形式交付。

## ✨ Core Features (核心功能)

### 1. 🗺️ Intelligent Topology Canvas (智能拓扑画布)
*   **可视化映射**：将抽象的软件模块与具体的芯片引脚（如 `PA5`, `USART1`）通过连线直观绑定。
*   **拖拽式重构**：发现引脚冲突？直接拖动连线到空闲引脚，底层代码自动重写。
*   **实时校验**：自动检测电气冲突（如 GPIO 模式不匹配）并高亮警告。

### 2. 📖 Live Datasheet (手册实况联动)
*   **上下文感知**：点击画布上的 `TIM2` 模块，右侧面板自动跳转至 STM32 参考手册的定时器章节。
*   **AI 辅助阅读**：内置 RAG 检索引擎，直接回答“TIM2 的时钟源怎么配”等问题，并高亮原文依据。

### 3. 🩺 Digital Twin Dashboard (数字孪生仪表盘)
*   **HIL 回环监控**：实时接收物理硬件回传的 Telemetry 数据。
*   **虚拟示波器**：将传感器数据直接渲染为动态波形。
*   **故障自愈向导**：当硬件报错时，直接在拓扑图上标记故障点，并提供 AI 生成的修复建议。

## 🏗️ Architecture (架构设计)

本项目采用 **Monorepo** 结构设计，核心 UI 逻辑与宿主环境解耦，以支持未来的多端部署（VS Code, Web, Desktop）。

```text
reify-studio/
├── packages/
│   ├── ui-core/              # [Core] 通用 React 组件库 (Canvas, Charts)
│   │   └── ...
│   │
│   ├── app-vscode/           # [Target] VS Code 插件适配层
│   │   ├── src/extension.ts  # 插件主进程
│   │   └── package.json
│   │
│   └── app-web/              # [Target] (Planned) 纯网页版
│       └── ...
```

## 🚀 Getting Started (开发指南)

### Prerequisites
*   Node.js 18+
*   pnpm (推荐) 或 npm

### Installation
```bash
# 1. Clone repository
git clone https://github.com/ReifyFlow/reify-studio.git

# 2. Install dependencies
pnpm install

# 3. Build & Watch
pnpm run watch
```

### Debugging in VS Code
1.  Open this folder in VS Code.
2.  Press `F5` to launch a new Extension Development Host window.
3.  Execute command: `ReifyFlow: Open Studio`.

## 🤝 Contribution

We welcome contributions to the UI/UX design!
*   **Frontend Stack**: React, React Flow, Vite, TailwindCSS.
*   **Design System**: Based on VS Code Webview UI Toolkit.

---
*Part of the ReifyFlow.*
