# Playwright CLI 工作流

使用包装脚本，并经常获取快照。
假设已经设置 `PWCLI`，并且 `pwcli` 是 `"$PWCLI"` 的别名。
在这个仓库中，从 `output/playwright/<label>/` 目录运行命令，以便把产物集中放置。

## 标准交互循环

```bash
pwcli open https://example.com
pwcli snapshot
pwcli click e3
pwcli snapshot
```

## 表单提交

```bash
pwcli open https://example.com/form --headed
pwcli snapshot
pwcli fill e1 "user@example.com"
pwcli fill e2 "password123"
pwcli click e3
pwcli snapshot
pwcli screenshot
```

## 数据提取

```bash
pwcli open https://example.com
pwcli snapshot
pwcli eval "document.title"
pwcli eval "el => el.textContent" e12
```

## 调试和检查

复现问题后捕获控制台消息和网络活动：

```bash
pwcli console warning
pwcli network
```

围绕可疑流程记录 trace：

```bash
pwcli tracing-start
# 复现问题
pwcli tracing-stop
pwcli screenshot
```

## 会话

使用会话隔离不同项目的工作：

```bash
pwcli --session marketing open https://example.com
pwcli --session marketing snapshot
pwcli --session checkout open https://example.com/checkout
```

也可以只设置一次会话：

```bash
export PLAYWRIGHT_CLI_SESSION=checkout
pwcli open https://example.com/checkout
```

## 配置文件

默认情况下，CLI 会从当前目录读取 `playwright-cli.json`。使用 `--config` 可以指定某个配置文件。

最小示例：

```json
{
  "browser": {
    "launchOptions": {
      "headless": false
    },
    "contextOptions": {
      "viewport": { "width": 1280, "height": 720 }
    }
  }
}
```

## 故障排查

- 如果元素引用失败，重新运行 `pwcli snapshot` 后再试。
- 如果页面看起来不对，用 `--headed` 重新打开并调整窗口大小。
- 如果流程依赖之前的状态，使用命名 `--session`。
