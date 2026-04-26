# CHANGELOG

## 2026-04-27

### 新增

- `\gxufrontmatter{中文摘要路径}{英文摘要路径}` —— 2 参数封装，自动注入 `\cntitle` / `\entitle`，旧 `\makefrontmatter` 4 参数版保留
- `\gxumainmatter` —— 替代 `\startmainmatter`（旧名作别名保留）
- `\coverbreak` —— 替代 `\titlebreak`，仅在封面/扉页换行（旧名作别名保留）
- `\headerbreak` —— 仅在页眉换行
- `\abstractbreak` —— 仅在摘要章节标题换行
- `\gxuspinerotateletter` 开关 —— 单列书脊字母旋转，默认关闭
- `\gxunoheader` 开关 —— 完全隐藏页眉（旧版送审表现）

### 变更

- **送审 (`\gxublindtrue`)**：按 2026 学校新规范，保留页眉横线 + 右侧标题，仅隐藏左侧「广西大学某士学位论文」与封面校徽；旧的「完全无页眉」由新增命令 `\gxunoheader` 控制
- **单列书脊**：默认不旋转字母；未旋转字母放进等宽盒子居中，与汉字对齐
- **页眉西文**：与中文同样使用隶书（SimLi），不再继承 Times New Roman
- **封面标题行距**：自动换行与手动 `\\` 视觉统一（`\fontsize` 移至 TikZ 节点外，让 `@parboxrestore` 拿到正确 `\normalbaselineskip`）
- **摘要章节标题**：忽略 `\coverbreak` / `\titlebreak` 及紧随空格
- **参考文献样式**：升级 biblatex-gb7714-2015 至 v1.1w；去除了为 v1.1v 修复 bug 的临时代码；引用压缩阈值由 3 篇改为默认的 2 篇

### 修复

- `ulem` 加载选项加 `[normalem]`，`\emph{}` 恢复斜体（避免被覆盖为下划线）
- 修复了封面标题使用 `\titlebreak` 和 `\\` 产生的行距有细微差距的问题
