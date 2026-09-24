# ADR-0003: GitHub 作为项目管理中心

**Date**: 2026-09-25
**Status**: Accepted

## 背景

项目已完成 demo 阶段（单 HTML 文件 + MediaPipe），需要决定后续开发的项目管理方式。选项：继续本地开发、GitHub 全流程管理、或混合模式。

## 决策

以 GitHub (`github.com/taoyuchen-ai/human-sitting-posture`) 作为项目管理中心：

- **Issue 追踪** — GitHub Issues + 模板（Feature / Bug）
- **看板** — GitHub Project v2 Kanban（Todo → In Progress → In Review → Done）
- **CI/CD** — GitHub Actions（HTML 校验 + GitHub Pages 自动部署）
- **分支策略** — feature branch + PR，即使单人也留记录
- **与 jira_local 完全独立** — 无同步、无打通

## 理由

1. **单一可信源** — 代码、Issue、CI、部署都在一个平台，不用在本地工具和云端之间切换
2. **自动化** — push 到 main 自动部署到 GitHub Pages，CI 自动校验
3. **留痕** — PR 记录每次改动的原因和 diff，三个月后可追溯
4. **随时分享** — GitHub Pages 提供在线 demo 链接，无需额外部署

## 代价

- jira_local 和 GitHub 两套体系并行（但领域不同，不冲突）
- GitHub Pages 只支持静态站点，后续如需后端要另寻方案

## 否决的方案

- **GitHub 替代 jira_local** — jira_local 管无线测试领域，领域不同不该合并
- **jira_local 同步到 GitHub** — 双向同步增加复杂度，单人项目不值得
- **Git Flow 多分支** — 单人项目过度工程
