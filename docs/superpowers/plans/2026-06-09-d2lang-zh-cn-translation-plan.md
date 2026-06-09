# D2 文档站修复 — 实施计划

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 修复 d2lang-cn 文档站的 locale 配置、硬编码资源路径、以及重新翻译 63 篇中文文档

**Architecture:** Fork 方案。保持 `docs/tour/` 为英文源（与上游 terrastruct/d2-docs 同步），`defaultLocale` 改为 `"en"`，翻译写入 `i18n/zh-cn/`。翻译按侧边栏顺序分 10 组并行执行。

**Tech Stack:** Docusaurus 3 + i18n, Markdown, subagent-driven translation

---

## 文件结构

| 路径 | 角色 | 操作 |
|---|---|---|
| `docusaurus.config.ts` | 站点配置 | 修改 `defaultLocale` 为 `"en"` |
| `src/pages/index.js` | 首页组件 | 修复 2 处硬编码 img src |
| `src/theme/Footer/index.js` | 页脚组件 | 修复 2 处硬编码 img src，添加 `useBaseUrl` 导入 |
| `docs/tour/*.md` | 英文源文件（63 篇） | 不修改 |
| `i18n/zh-cn/docusaurus-plugin-content-docs/current/tour/*.md` | 简体中文翻译（63 篇） | 覆盖重写 |

---

### Task 1: 修复 defaultLocale 配置

**Files:**
- Modify: `docusaurus.config.ts:67`

- [ ] **Step 1: 将 defaultLocale 从 "zh-cn" 改为 "en"**

```diff
   i18n: {
-    defaultLocale: "zh-cn",
+    defaultLocale: "en",
     locales: ["en", "ko", "zh-cn"],
```

- [ ] **Step 2: 验证修改正确**

查看 `docusaurus.config.ts:67`，确认 `defaultLocale: "en"`。

- [ ] **Step 3: 提交**

```bash
git add docusaurus.config.ts
git commit -m "fix: change defaultLocale from zh-cn to en"
```

---

### Task 2: 修复首页资源路径

**Files:**
- Modify: `src/pages/index.js:24-32`

- [ ] **Step 1: 将首页两处硬编码 img src 改为 useBaseUrl 调用**

```diff
   <img
     className="Directory__Banner--Circles"
-    src="/img/directory/circles.svg"
+    src={useBaseUrl("/img/directory/circles.svg")}
     alt="Decorative circles"
   />
   <img
     className="Directory__Banner--Icon"
-    src="/img/d2_graphic.svg"
+    src={useBaseUrl("/img/d2_graphic.svg")}
     alt="D2 logo"
   />
```

注意：`useBaseUrl` 已在 `src/pages/index.js:3` 导入：
```js
import useBaseUrl from "@docusaurus/useBaseUrl";
```

- [ ] **Step 2: 提交**

```bash
git add src/pages/index.js
git commit -m "fix: use useBaseUrl for image paths in index page"
```

---

### Task 3: 修复页脚资源路径

**Files:**
- Modify: `src/theme/Footer/index.js`

- [ ] **Step 1: 添加 useBaseUrl 导入**

在文件顶部 imports 区域添加：
```diff
+import useBaseUrl from "@docusaurus/useBaseUrl";
```

- [ ] **Step 2: 将页脚两处硬编码 img src 改为 useBaseUrl 调用**

```diff
-<img className="Footer__Logo" src="/img/d2_logo.png" alt="D2 logo" />
+<img className="Footer__Logo" src={useBaseUrl("/img/d2_logo.png")} alt="D2 logo" />
```

```diff
-Created by <img src="/img/terrastruct_logo.svg" alt="Terrastruct logo" />
+Created by <img src={useBaseUrl("/img/terrastruct_logo.svg")} alt="Terrastruct logo" />
```

- [ ] **Step 3: 提交**

```bash
git add src/theme/Footer/index.js
git commit -m "fix: use useBaseUrl for image paths in Footer"
```

---

### Task 4: 翻译 Group 1 — Introduction

**Source files:** `docs/tour/intro.md`, `docs/tour/experience.md`, `docs/tour/design.md`, `docs/tour/community.md`, `docs/tour/future.md`

**Target paths (under `i18n/zh-cn/docusaurus-plugin-content-docs/current/tour/`):**
- `intro.md`, `experience.md`, `design.md`, `community.md`, `future.md`

- [ ] **Step 1: 读取 5 个英文源文件**

读取 `docs/tour/intro.md`、`docs/tour/experience.md`、`docs/tour/design.md`、`docs/tour/community.md`、`docs/tour/future.md` 的内容。

- [ ] **Step 2: 启动 subagent 翻译 Group 1**

Subagent 指令：
- 正文全部翻译为简体中文
- 专有名词/代码变量：保留英文原名，紧跟括号加中文翻译，如 `x（变量）`、`shape（形状）`、`layout（布局）`
- PostgreSQL、AWS 等与 D2 语言无直接关联的产品名/服务名，保留英文不译
- 代码块不修改，只翻译已有的英文注释
- 保留 markdown 结构、URL、锚点、frontmatter
- 返回 `{filename: translated_content}` 映射

- [ ] **Step 3: 将译文写入目标目录**

确认目标目录存在后，写入 5 个文件。

- [ ] **Step 4: 随机抽查 1 篇验证规范执行**

对照英文原文，检查：
- 括号翻译格式是否正确
- 代码块是否未被修改
- PostgreSQL/AWS 等是否未翻译

---

### Task 5: 翻译 Group 2 — Getting Started

**Source files:** `docs/tour/install.md`, `docs/tour/hello-world.md`, `docs/tour/shapes.md`, `docs/tour/connections.md`, `docs/tour/containers.md`

**Target paths:** `install.md`, `hello-world.md`, `shapes.md`, `connections.md`, `containers.md`

- [ ] **Step 1: 读取 5 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 2**

翻译规范同 Task 4。

- [ ] **Step 3: 将译文写入目标目录

- [ ] **Step 4: 随机抽查 1 篇验证

---

### Task 6: 翻译 Group 3 — Special Objects

**Source files:** `docs/tour/text.md`, `docs/tour/icons.md`, `docs/tour/sql-tables.md`, `docs/tour/uml-classes.md`, `docs/tour/sequence-diagrams.md`, `docs/tour/grid-diagrams.md`

**Target paths:** `text.md`, `icons.md`, `sql-tables.md`, `uml-classes.md`, `sequence-diagrams.md`, `grid-diagrams.md`

- [ ] **Step 1: 读取 6 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 3

- [ ] **Step 3: 写入目标目录

- [ ] **Step 4: 抽查验证

---

### Task 7: 翻译 Group 4 — Customization

**Source files:** `docs/tour/themes.md`, `docs/tour/style.md`, `docs/tour/classes.md`, `docs/tour/dimensions.md`, `docs/tour/positions.md`, `docs/tour/sketch.md`, `docs/tour/interactive.md`, `docs/tour/fonts.md`

**Target paths:** `themes.md`, `style.md`, `classes.md`, `dimensions.md`, `positions.md`, `sketch.md`, `interactive.md`, `fonts.md`

- [ ] **Step 1: 读取 8 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 4

- [ ] **Step 3: 写入目标目录

- [ ] **Step 4: 抽查验证

---

### Task 8: 翻译 Group 5 — Layouts

**Source files:** `docs/tour/layouts.md`, `docs/tour/dagre.md`, `docs/tour/elk.md`, `docs/tour/tala.md`

**Target paths:** `layouts.md`, `dagre.md`, `elk.md`, `tala.md`

- [ ] **Step 1: 读取 4 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 5

- [ ] **Step 3: 写入目标目录

- [ ] **Step 4: 抽查验证

---

### Task 9: 翻译 Group 6 — In Depth

**Source files:** `docs/tour/strings.md`, `docs/tour/vars.md`, `docs/tour/globs.md`, `docs/tour/comments.md`, `docs/tour/overrides.md`, `docs/tour/models.md`, `docs/tour/legend.md`, `docs/tour/auto-formatter.md`

**Target paths:** `strings.md`, `vars.md`, `globs.md`, `comments.md`, `overrides.md`, `models.md`, `legend.md`, `auto-formatter.md`

- [ ] **Step 1: 读取 8 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 6

- [ ] **Step 3: 写入目标目录

- [ ] **Step 4: 抽查验证

---

### Task 10: 翻译 Group 7 — Composition

**Source files:** `docs/tour/composition.md`, `docs/tour/layers.md`, `docs/tour/scenarios.md`, `docs/tour/steps.md`, `docs/tour/linking.md`, `docs/tour/composition-formats.md`

**Target paths:** `composition.md`, `layers.md`, `scenarios.md`, `steps.md`, `linking.md`, `composition-formats.md`

- [ ] **Step 1: 读取 6 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 7

- [ ] **Step 3: 写入目标目录

- [ ] **Step 4: 抽查验证

---

### Task 11: 翻译 Group 8 — Imports

**Source files:** `docs/tour/imports.md`, `docs/tour/imports-use-cases.md`, `docs/tour/model-view.md`, `docs/tour/modular-classes.md`, `docs/tour/nested-composition.md`, `docs/tour/version-visualization.md`, `docs/tour/imported-template.md`

**Target paths:** `imports.md`, `imports-use-cases.md`, `model-view.md`, `modular-classes.md`, `nested-composition.md`, `version-visualization.md`, `imported-template.md`

- [ ] **Step 1: 读取 7 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 8

- [ ] **Step 3: 写入目标目录

- [ ] **Step 4: 抽查验证

---

### Task 12: 翻译 Group 9 — Extensions

**Source files:** `docs/tour/extensions.md`, `docs/tour/vscode.md`, `docs/tour/vim.md`, `docs/tour/obsidian.md`, `docs/tour/slack.md`, `docs/tour/discord.md`

**Target paths:** `extensions.md`, `vscode.md`, `vim.md`, `obsidian.md`, `slack.md`, `discord.md`

- [ ] **Step 1: 读取 6 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 9

- [ ] **Step 3: 写入目标目录

- [ ] **Step 4: 抽查验证

---

### Task 13: 翻译 Group 10 — 末尾独立页面

**Source files:** `docs/tour/man.md`, `docs/tour/exports.md`, `docs/tour/cheat-sheet.md`, `docs/tour/faq.md`, `docs/tour/troubleshoot.md`, `docs/tour/help.md`

**Target paths:** `man.md`, `exports.md`, `cheat-sheet.md`, `faq.md`, `troubleshoot.md`, `help.md`

- [ ] **Step 1: 读取 6 个英文源文件内容

- [ ] **Step 2: 启动 subagent 翻译 Group 10

- [ ] **Step 3: 写入目标目录

- [ ] **Step 4: 抽查验证

---

### Task 14: 最终验证

- [ ] **Step 1: 确认文件数量一致**

```bash
ls docs/tour/*.md | wc -l   # 应为 63
ls i18n/zh-cn/docusaurus-plugin-content-docs/current/tour/*.md | wc -l   # 应为 63
```

- [ ] **Step 2: 确认存在的翻译无法访问**

```bash
ls i18n/zh-cn/docusaurus-plugin-content-docs/current/tour/api.md   # 应有
ls i18n/zh-cn/docusaurus-plugin-content-docs/current/tour/editor-support.md   # 应有
```

- [ ] **Step 3: 启动 Docusaurus 预览验证**

```bash
yarn dev
```

手动检查：
- 根路径 `/` 显示英文
- 访问 `/zh-cn/tour/intro/` 显示中文
- 首页图片正常加载
- locale dropdown 有 English / 简体中文 两个选项

- [ ] **Step 4: 提交所有改动**

```bash
git add docusaurus.config.ts src/pages/index.js src/theme/Footer/index.js i18n/zh-cn/
git commit -m "feat: fix locale config, resource paths, and retranslate zh-cn docs"
```
