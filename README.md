# 人类与 AI 协作开发标准

两张自包含的 HTML 架构图，纯矢量（SVG）渲染，可无限放大、可直接在浏览器里改文字，双击即开、无需联网、无需安装任何依赖。

## 在线看（不用下载）

| 看什么 | 网址 |
| --- | --- |
| **导航页**（推荐从这里进） | <https://ijiangli.github.io/ai-collab-workflow-diagrams/> |
| 流程图 · 先做什么后做什么 | <https://ijiangli.github.io/ai-collab-workflow-diagrams/human-ai-collab-workflow.html> |
| 结构图 · 谁依赖谁、谁有权改 | <https://ijiangli.github.io/ai-collab-workflow-diagrams/human-ai-collab-structure.html> |

手机上也能打开，右上角可切深色 / 浅色。

## 文件

| 文件 | 它回答的问题 | 看的时候注意什么 |
| --- | --- | --- |
| [`index.html`](index.html) | 导航页：两张图的关系、三道关卡一眼看全 | 卡片点进去就是大图；深色浅色跟随系统 |
| [`human-ai-collab-workflow.html`](human-ai-collab-workflow.html) | **先做什么、后做什么**——一条主干从定规矩走到人工验收 | 三条泳道（人 / AI / 仓库）；每个横向箭头都是一次交接；每个向下的虚线都是一次「入仓」；右下三张卡片是关卡、Git 硬规矩、打回规则 |
| [`human-ai-collab-structure.html`](human-ai-collab-structure.html) | **系统由哪几块组成、谁依赖谁、谁有权改什么**——同一件事的静态切面 | 三层（人的决策层 / AI 执行层 / 仓库事实源）；人的决策层故意分成「计划侧」和「验收侧」两处，中间那段空档表示 AI 连续作业时人不介入 |

两张图是一套：一张讲时间顺序，一张讲结构边界。同一条规矩在两张图上都能找到对应位置。

## 五阶段主线

1. **环境搭建** — `git init`、写 `AGENTS.md`、先配 `.gitignore`
2. **产品设计** — 人写产品方案，AI 出可点 Demo
3. **技术设计** — AI 出技术方案，人确认（关卡②，没批不准开工）
4. **产品实现** — AI 写代码 + AI 自测，推 PR 触发 CI
5. **人工验证** — CI 绿灯后人来验收（关卡③），人点了才合并

## 三道人工关卡

不通过就不往下走，这是这套标准里唯一不能省的部分：

- **关卡① 规矩关**：项目边界和 `AGENTS.md` 没定清楚，不开工
- **关卡② 方案关**：技术方案没被人确认，不写代码
- **关卡③ 验收关**：CI 没绿灯、人没点，不合并主干

## Git / GitHub 硬规矩

- 主干（`main`）受保护，谁都不能直接 push
- 一个任务一条 `feature/*` 分支，做完就删
- commit 写清楚「为什么」，不是「改了什么」
- `.gitignore` 在第一次 commit 之前就配好——密钥、构建产物、本地配置不许进仓库
- 合并只能走 PR：说明 + 自测结果 + 关联任务，三件套齐全才许提

## 打回规则（不要一律退回重做）

| 问题性质 | 退回到哪 |
| --- | --- |
| 代码 bug、实现没达标 | 退回「写代码」 |
| 技术选型错、方案不可行 | 退回「技术设计」 |
| 需求本身变了 | 退回「产品设计」 |

## 怎么用

- 直接浏览器打开 `human-ai-collab-workflow.html` 或 `human-ai-collab-structure.html`
- 右上角可切换深色 / 浅色
- 文字可以直接在编辑器里改（是普通 HTML + SVG，不是图片）
- 想导出图片，页面上有导出按钮（PNG / SVG）

## 一句话

这套规矩不是只给团队用的，是**自己也要遵守**的——只有这样规矩干活，项目才能更好。
