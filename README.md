# AI 体态监测与矫正

> 面向学生的浏览器端坐姿监测 Demo —— 实时检测不良坐姿，提醒矫正，保护视力和脊柱。

## 在线 Demo

👉 **https://taoyuchen-ai.github.io/human-sitting-posture/**

（需在浏览器中允许摄像头权限）

## 功能

- **实时姿态检测** — 基于 Google MediaPipe Pose，浏览器端 WASM 推理，30fps
- **4 项体态指标** — 头部前倾角、面部距屏幕距离、躯干前倾角（侧面模式）、久坐时长
- **手动校准基线** — 30 帧取中位数锁定个人"正确坐姿"，后续检测为相对偏移量
- **姿态评分** — 0-100 分，绿（≥80）/ 黄（60-79）/ 红（<60）三级
- **骨架叠加** — 摄像头预览上实时绘制人体骨架，颜色随评分变化
- **智能提醒** — 不良姿态持续 5 秒弹窗 + 60 秒冷却防骚扰
- **20-20-20 法则** — 持续注视 20 分钟后提醒看远处 20 秒，保护视力
- **正面/侧面切换** — 正面模式覆盖头部+面部+久坐；侧面模式增加躯干前倾角
- **纯本地** — 摄像头画面不上传，数据存 localStorage，零后端零隐私风险

## 使用方法

1. 打开 [在线 Demo](https://taoyuchen-ai.github.io/human-sitting-posture/) 或双击 `index.html`
2. 点击「开始监测」→ 允许摄像头权限
3. 坐直 → 点击「校准基线坐姿」→ 保持 30 帧
4. 正常学习/工作，系统实时监测
5. 不良坐姿持续 5 秒 → 弹窗提醒
6. 每 20 分钟 → 20-20-20 休息提醒

## 技术栈

| 组件 | 技术 |
|---|---|
| 姿态检测 | Google MediaPipe Pose (WASM, 33 关键点) |
| 前端 | 纯 Vanilla JS 单 HTML 文件，零构建步骤 |
| 数据存储 | localStorage (基线 + 评分趋势 + 提醒历史) |
| 部署 | GitHub Pages (静态) |
| CI | GitHub Actions (HTML 校验 + 自动部署) |

## 架构决策

| ADR | 决策 |
|---|---|
| [0001](docs/adr/0001-local-first-architecture.md) | 纯本地架构 — 无后端、无云端 |
| [0002](docs/adr/0002-vanilla-js-single-file.md) | Vanilla JS 单文件 — 无构建工具、无框架 |
| [0003](docs/adr/0003-github-project-management.md) | GitHub 作为项目管理中心 |

## 领域术语

详见 [CONTEXT.md](CONTEXT.md) — 体态、校准、基线、姿态评分、20-20-20 法则等 13 个核心术语定义。

## 目标用户

学生（伏案学习，近视高发场景）。

## License

MIT
