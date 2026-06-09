# D2 Documentation 中文翻译 — 设计文档 (v2)

## 目标

将 terrastruct/d2-docs 的 fork 仓库（d2lang-cn）改造为以简体中文为目标语言的文档站。包含三个子任务：

1. 修复 locale 配置，使默认语言为英文（而非韩文），中文位于 `/zh-cn/`
2. 修复硬编码资源路径（缺少 `/d2lang/` baseUrl 前缀）
3. 按侧边栏顺序重新翻译 63 篇文档为简体中文

## 架构

```text
fork 仓库（d2lang-cn ← terrastruct/d2-docs）
├── docs/tour/              ← 英文源（与上游同步，不做修改）
├── i18n/en/                ← 不存在（默认 locale 无需额外目录）
├── i18n/ko/                ← 保留（来自上游，不删除）
├── i18n/zh-cn/             ← 简体中文翻译（重新翻译后覆盖）
└── docusaurus.config.ts    ← 修改 defaultLocale
```

### Docusaurus i18n 路由

| 路径 | 语言 | 内容来源 |
|---|---|---|
| `/` | 英文（default） | `docs/tour/*.md` |
| `/ko/` | 韩文 | `i18n/ko/.../tour/*.md`（上游贡献） |
| `/zh-cn/` | 简体中文 | `i18n/zh-cn/.../tour/*.md`（本项目译） |

### 配置变更

- `defaultLocale`: `"zh-cn"` → `"en"`
- `locales`: 保持不变 `["en", "ko", "zh-cn"]`
- `i18n/ko/`：保留文件，不做任何修改（来自上游）

## 资源路径修复

### 问题

部分 JSX 组件中使用了硬编码的绝对路径（如 `src="/img/directory/circles.svg"`），未包含 baseUrl 前缀 `/d2lang/`，在部署后图片无法加载。

### 修复清单

| 文件 | 行 | 当前代码 | 修复后 |
|---|---|---|---|
| `src/pages/index.js` | 26 | `src="/img/directory/circles.svg"` | `src={useBaseUrl("/img/directory/circles.svg")}` |
| `src/pages/index.js` | 31 | `src="/img/d2_graphic.svg"` | `src={useBaseUrl("/img/d2_graphic.svg")}` |
| `src/theme/Footer/index.js` | 19 | `src="/img/d2_logo.png"` | `src={useBaseUrl("/img/d2_logo.png")}` |
| `src/theme/Footer/index.js` | 31 | `src="/img/terrastruct_logo.svg"` | `src={useBaseUrl("/img/terrastruct_logo.svg")}` |

`useBaseUrl` 已导入于 `src/pages/index.js` 并用于其他引用。`src/theme/Footer/index.js` 需添加导入。

### 不需要修复的

- Markdown 中的 `/tour/...`、`/examples/...` 等内部链接由 Docusaurus 客户端路由自动处理 baseUrl
- 英文源文件 `sketch.md` 中的 `/blog/hand-drawn-diagrams` 同样由客户端路由处理

## 翻译规范

### 正文翻译

- 全部翻译为简体中文
- **专有名词/代码变量**：保留英文原名，紧跟括号加中文翻译
  - 例：`x（变量）`、`shape（形状）`、`layout（布局）`
  - 例：`x（变量）`、`shape（形状）`、`layout（布局）`
  - PostgreSQL、AWS 等与 D2 语言无直接关联的产品名/服务名，保留英文不译
- 只对关键变量/术语做括号标注，不需要每个词都加
- 文风：易读简洁，准确性 > 流畅性

### 代码块

- 不新增任何中文注释
- 只翻译代码块内已有的英文注释（保留原位置和格式）

### 格式要求

- 保留原 markdown 结构：标题层级、代码围栏、列表、空行、缩进
- 不修改任何 URL、文件路径、锚点链接、图片路径
- 保留 frontmatter 不做修改

### 术语参考

| 英文 | 中文 |
|---|---|
| shape | 形状 |
| container | 容器 |
| layout | 布局 |
| import | 导入 |
| connection | 连接 |
| board | 面板 |
| layer | 图层 |
| scenario | 场景 |
| step | 步骤 |
| theme | 主题 |
| style | 样式 |
| class | 类 |
| variable | 变量 |
| glob | 通配 |
| comment | 注释 |
| icon | 图标 |
| override | 覆写 |
| model | 模型 |
| composition | 组合 |

## 翻译分组方案（按侧边栏顺序）

英文源 63 篇，按侧边栏章节顺序分 10 组，每组由一个 subagent 并行翻译。已有的 61 篇中文翻译全部覆盖重写。

| 组 | 分类 | 文件 | 数量 |
|---|---|---|---|
| G1 | Introduction | intro, experience, design, community, future | 5 |
| G2 | Getting Started | install, hello-world, shapes, connections, containers | 5 |
| G3 | Special Objects | text, icons, sql-tables, uml-classes, sequence-diagrams, grid-diagrams | 6 |
| G4 | Customization | themes, style, classes, dimensions, positions, sketch, interactive, fonts | 8 |
| G5 | Layouts | layouts, dagre, elk, tala | 4 |
| G6 | In Depth | strings, vars, globs, comments, overrides, models, legend, auto-formatter | 8 |
| G7 | Composition | composition, layers, scenarios, steps, linking, composition-formats | 6 |
| G8 | Imports | imports, imports-use-cases, model-view, modular-classes, nested-composition, version-visualization, imported-template | 7 |
| G9 | Extensions | extensions, vscode, vim, obsidian, slack, discord | 6 |
| G10 | 独立页 | man, exports, cheat-sheet, faq, troubleshoot, help | 6 |

### 翻译流程

1. 主进程读每组英文源文件（`docs/tour/`）+ 翻译规范
2. 并行启动 10 个 subagent，各翻译一组
3. 每个 subagent 返回 `{filename: translated_content}` 映射
4. 主进程将译文写入 `i18n/zh-cn/docusaurus-plugin-content-docs/current/tour/`
5. 已有 61 篇全部覆盖，缺少的 2 篇（当前已有中文不存在）一并创建
6. 文件数验证：63 篇英文 = 63 篇中文

## 架构图

```dot
执行顺序:
  主进程 ──→ 修复配置 + 资源路径（串行）
        │
        ├── subagent G1 ──→ Translation Group 1
        ├── subagent G2 ──→ Translation Group 2
        ├── subagent G3 ──→ Translation Group 3
        ├── subagent G4 ──→ Translation Group 4
        ├── subagent G5 ──→ Translation Group 5
        ├── subagent G6 ──→ Translation Group 6
        ├── subagent G7 ──→ Translation Group 7
        ├── subagent G8 ──→ Translation Group 8
        ├── subagent G9 ──→ Translation Group 9
        └── subagent G10 ──→ Translation Group 10
                │
                ▼
        主进程统一写入 i18n/zh-cn/*.md
                │
                ▼
        验证: yarn dev --locale zh-cn
```

## 错误处理

- 单个 subagent 翻译失败不影响其他组，失败组可单独重试
- 每个 subagent 输出文件级映射，主进程逐文件写入，避免部分写入导致的不一致
- 写入前先确认目标目录存在

## 验证

1. `docusaurus.config.ts`: defaultLocale 为 `"en"`，locales 包含 `"zh-cn"`
2. 资源路径修复后 `yarn dev` 无 404，图片正常显示
3. 翻译完成后 `yarn dev --locale zh-cn` 所有页面正常渲染
4. 文件数检查：`ls docs/tour/*.md | wc -l` = `ls i18n/zh-cn/.../tour/*.md | wc -l` = 63
5. 抽查 3-5 篇译文，检查术语一致性、括号翻译格式、代码块完整性
