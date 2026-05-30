# Playwright CLI 参考

除非 CLI 已经全局安装，否则使用包装脚本：

```bash
export CODEX_HOME="${CODEX_HOME:-$HOME/.codex}"
export PWCLI="$CODEX_HOME/skills/playwright/scripts/playwright_cli.sh"
"$PWCLI" --help
```

用户级技能安装在 `$CODEX_HOME/skills` 下，默认位置是 `~/.codex/skills`。

可选的便捷别名：

```bash
alias pwcli="$PWCLI"
```

## 核心命令

```bash
pwcli open https://example.com
pwcli close
pwcli snapshot
pwcli click e3
pwcli dblclick e7
pwcli type "搜索关键词"
pwcli press Enter
pwcli fill e5 "user@example.com"
pwcli drag e2 e8
pwcli hover e4
pwcli select e9 "option-value"
pwcli upload ./document.pdf
pwcli check e12
pwcli uncheck e12
pwcli eval "document.title"
pwcli eval "el => el.textContent" e5
pwcli dialog-accept
pwcli dialog-accept "确认文本"
pwcli dialog-dismiss
pwcli resize 1920 1080
```

## 导航

```bash
pwcli go-back
pwcli go-forward
pwcli reload
```

## 键盘

```bash
pwcli press Enter
pwcli press ArrowDown
pwcli keydown Shift
pwcli keyup Shift
```

## 鼠标

```bash
pwcli mousemove 150 300
pwcli mousedown
pwcli mousedown right
pwcli mouseup
pwcli mouseup right
pwcli mousewheel 0 100
```

## 保存为产物

```bash
pwcli screenshot
pwcli screenshot e5
pwcli pdf
```

## 标签页

```bash
pwcli tab-list
pwcli tab-new
pwcli tab-new https://example.com/page
pwcli tab-close
pwcli tab-close 2
pwcli tab-select 0
```

## DevTools

```bash
pwcli console
pwcli console warning
pwcli network
pwcli run-code "await page.waitForTimeout(1000)"
pwcli tracing-start
pwcli tracing-stop
```

## 会话

使用命名会话隔离工作：

```bash
pwcli --session todo open https://demo.playwright.dev/todomvc
pwcli --session todo snapshot
```

也可以设置一次环境变量：

```bash
export PLAYWRIGHT_CLI_SESSION=todo
pwcli open https://demo.playwright.dev/todomvc
```
