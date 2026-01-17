# CLAUDE.md

此文件为 Claude Code (claude.ai/code) 在处理此代码库中的代码时提供指导。

## 项目概述

这是一个关于捕蝇草的单页交互式阅读课程，设计为一个教育性的 HTML/CSS 应用程序。该项目展示了一篇关于捕蝇草工作原理的英文阅读文章，采用滚动捕捉（scroll-snap）导航，并包含双语内容（英文文本配中文标题）。

## 架构

### 核心结构
- **`index.html`** - 包含所有内容、样式和结构的单页应用
- **`assets/`** - 包含课程中使用的 5 张图片的目录：
  - `title.png` - 标题页的封面/背景图片
  - `The Trap.png` - A 部分的图片
  - `Scientist studying plants.png` - B 部分的图片
  - `Close up of Venus Flytrap hairs.png` - C 部分的图片
  - `Closed trap digesting.png` - D 部分的图片

### 主要功能

**滚动捕捉导航**
- 在容器上使用 CSS `scroll-snap-type: y mandatory`
- 每个 `<section>` 都有 `scroll-snap-align: start` 用于逐页滚动
- 创建类似演示文稿的体验，滚动时会自动捕捉到每个部分

**内容结构**
- 总共 5 个部分：
  1. 带标题和滚动提示的封面页
  2. A 部分："The Trap" - 捕蝇草简介
  3. B 部分："An Electrical Plant" - 科学发现
  4. C 部分："The Trigger" - 捕捉机制的工作原理
  5. D 部分："Digestion" - 消化过程

**样式方法**
- 所有 CSS 都嵌入在 HTML 的 `<style>` 标签中
- 响应式设计，包含移动端媒体查询（max-width: 768px）
- 绿色/植物主题配色方案 (#2e7d32, #e8f5e9, #f4f9f4)
- 使用 `.highlight` 类高亮显示词汇（红色、粗体）
- 带有绿色强调边框的摘要框

**视觉设计**
- 桌面端双列布局（文本 + 图片）
- 移动端单列布局
- 基于卡片的内容容器，带有阴影和圆角
- 封面页使用全视口高度，带有背景图片叠加

## 开发

### 运行应用程序
这是一个静态 HTML 文件，无需构建过程。开发方式：

1. **使用 VS Code Live Server**（推荐）
   - `.vscode/settings.json` 已配置端口 5501
   - 右键点击 `index.html` → "Open with Live Server"

2. **使用 Python 简单 HTTP 服务器**
   ```bash
   python3 -m http.server 8000
   # 在浏览器中打开 http://localhost:8000
   ```

3. **使用 Node.js http-server**
   ```bash
   npx http-server -p 8000
   ```

### 添加内容
添加新部分：
1. 在 `index.html` 中复制一个 `<section>` 块
2. 更新 `h3` 标题、`p.article-text` 内容和 `img src` 路径
3. 在 `assets/` 文件夹中添加对应的图片
4. 使用 `<span class="highlight">` 标签更新词汇
5. 更新摘要框文本

### 修改样式
所有样式都在 `index.html` 的 `<style>` 块中：
- **颜色**：更改绿色主题颜色（第 35、77、82-83、91 行）
- **排版**：调整 `.cover h1`、`.cover h2`、`h3`、`p.article-text` 的字体大小
- **布局**：修改 `.content-wrapper` 的 max-width、gap、padding
- **响应式**：调整 `@media (max-width: 768px)` 中的断点

### Git 工作流
- 当前分支：`main`
- 最近的提交遵循简单的描述性消息（例如 "fix:var css 报错"、"init"）
- 没有复杂的构建或测试过程 - 更改直接作用于 `index.html`

## 注意事项

- 这是一个独立的教育项目，没有外部依赖
- 不使用构建工具、打包器或框架
- 图片是较大的 PNG 文件（每个 8-9MB）- 生产环境考虑优化
- 项目是双语的（英文内容配中文标题）
- 除了滚动行为外，没有服务器端逻辑或交互性
