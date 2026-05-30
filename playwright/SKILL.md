---
name: "playwright"
description: "当任务需要通过 `playwright-cli` 或随附的包装脚本在终端中自动化真实浏览器时使用，例如页面导航、表单填写、页面快照、截图、数据提取和 UI 流程调试。"
---


# Playwright CLI 技能

使用 `playwright-cli` 从终端驱动真实浏览器。优先使用随附的包装脚本，这样即使系统没有全局安装 CLI 也能运行。
把这个技能视为以命令行为主的自动化流程。除非用户明确要求编写测试文件，否则不要切换到 `@playwright/test`。

## 前置检查（必需）

在提出命令前，先检查 `npx` 是否可用，因为包装脚本依赖它：

```bash
command -v npx >/dev/null 2>&1
```

如果不可用，暂停并请用户安装 Node.js/npm，因为 npm 会提供 `npx`。请原样提供这些步骤：

```bash
# 验证 Node/npm 是否已安装
node --version
npm --version

# 如果缺失，先安装 Node.js/npm，然后运行：
npm install -g @playwright/cli@latest
playwright-cli --help
```

当 `npx` 可用后，继续使用包装脚本。全局安装 `playwright-cli` 是可选的。

## 技能路径（设置一次）

```bash
export CODEX_HOME="${CODEX_HOME:-$HOME/.codex}"
export PWCLI="$CODEX_HOME/skills/playwright/scripts/playwright_cli.sh"
```

用户级技能安装在 `$CODEX_HOME/skills` 下，默认位置是 `~/.codex/skills`。

## 快速开始

使用包装脚本：

```bash
"$PWCLI" open https://playwright.dev --headed
"$PWCLI" snapshot
"$PWCLI" click e15
"$PWCLI" type "Playwright"
"$PWCLI" press Enter
"$PWCLI" screenshot
```

如果用户更喜欢全局安装，也可以这样做：

```bash
npm install -g @playwright/cli@latest
playwright-cli --help
```

## 核心流程

1. 打开页面。
2. 获取快照，拿到稳定的元素引用。
3. 使用最新快照中的引用进行交互。
4. 导航或 DOM 明显变化后重新获取快照。
5. 在有帮助时捕获产物，例如截图、PDF、trace。

最小循环：

```bash
"$PWCLI" open https://example.com
"$PWCLI" snapshot
"$PWCLI" click e3
"$PWCLI" snapshot
```

## 什么时候重新获取快照

以下情况后需要重新获取快照：

- 页面导航
- 点击会明显改变界面的元素
- 打开或关闭弹窗、菜单
- 切换标签页

元素引用可能过期。当命令因为找不到引用而失败时，重新获取快照。

## 推荐模式

### 填写并提交表单

```bash
"$PWCLI" open https://example.com/form
"$PWCLI" snapshot
"$PWCLI" fill e1 "user@example.com"
"$PWCLI" fill e2 "password123"
"$PWCLI" click e3
"$PWCLI" snapshot
```

### 使用 trace 调试 UI 流程

```bash
"$PWCLI" open https://example.com --headed
"$PWCLI" tracing-start
# ...执行交互...
"$PWCLI" tracing-stop
```

### 多标签页操作

```bash
"$PWCLI" tab-new https://example.com
"$PWCLI" tab-list
"$PWCLI" tab-select 0
"$PWCLI" snapshot
```

## 包装脚本

包装脚本使用 `npx --package @playwright/cli playwright-cli`，因此无需全局安装 CLI 也可以运行：

```bash
"$PWCLI" --help
```

除非仓库已经统一使用全局安装方式，否则优先使用包装脚本。

## 参考资料

只打开当前任务需要的文件：

- CLI 命令参考：`references/cli.md`
- 实用流程和故障排查：`references/workflows.md`

## 保护规则

- 引用 `e12` 这类元素 id 前，必须先获取快照。
- 当引用看起来过期时，重新获取快照。
- 除非确实需要，优先使用明确命令，而不是 `eval` 和 `run-code`。
- 如果没有最新快照，使用 `eX` 这类占位引用并说明原因；不要用 `run-code` 绕过引用机制。
- 当视觉检查有帮助时，使用 `--headed`。
- 在本仓库中捕获产物时，使用 `output/playwright/`，避免新增顶层产物目录。
- 默认使用 CLI 命令和工作流，而不是 Playwright 测试规范。
