# ADR-0002: Vanilla JS 单文件 — 无构建工具、无框架

**Date**: 2026-09-25
**Status**: Accepted

## 背景

前端技术选型。可选用 Vanilla JS 单文件、Vite + TypeScript、Vite + React + TypeScript。

## 决策

采用纯 Vanilla JS 单 HTML 文件 + MediaPipe CDN 引入：

- 单个 `index.html` 包含全部 HTML/CSS/JS
- MediaPipe 通过 `<script src="https://cdn.jsdelivr.net/npm/@mediapipe/pose">` CDN 引入
- 零构建步骤、零 npm 依赖、双击即开

## 理由

1. **Demo 核心目标**：最快验证"摄像头 → 检测 → 评分 → 提醒"链路，构建配置是负担
2. **零门槛**：学生双击 HTML 即可使用，无需 `npm install`
3. **MediaPipe 官方支持 CDN 方案**，无需打包
4. **迁移成本可控**：后续扩为产品时，迁移到 Vite 只是代码搬运（搬进 .ts 文件），不是重写

## 代价

- 无类型安全（但 demo 规模 < 500 行 JS，可控）
- 无组件化（但只有一个页面，不需要）
- 无热更新（手动刷新即可）

## 否决的方案

- **Vite + TypeScript**：构建配置对 demo 是负担，TypeScript 类型收益在 < 500 行时有限
- **Vite + React + TypeScript**：组件化对单页面 demo 是过度工程，React 运行时也是不必要的体积
