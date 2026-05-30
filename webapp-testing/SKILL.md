---
name: webapp-testing
description: 使用 Playwright 与本地 Web 应用交互并进行测试的工具包。支持验证前端功能、调试 UI 行为、捕获浏览器截图，以及查看浏览器日志。
license: 完整条款见 LICENSE.txt
---

# Web 应用测试

测试本地 Web 应用时，编写原生 Python Playwright 脚本。

**可用辅助脚本**：

- `scripts/with_server.py` - 管理服务器生命周期，支持多个服务器。

**始终先用 `--help` 运行脚本**，查看使用方式。除非你已经尝试运行脚本，并确认确实需要定制方案，否则不要直接阅读脚本源码。这些脚本可能很长，会占用大量上下文。它们的定位是作为黑盒脚本直接调用，而不是把源码整体读入上下文。

## 决策树：选择测试方式

```text
用户任务 -> 是否是静态 HTML？
    |-- 是 -> 直接读取 HTML 文件以识别选择器
    |         |-- 成功 -> 使用选择器编写 Playwright 脚本
    |         `-- 失败或信息不足 -> 按动态应用处理
    |
    `-- 否，动态 Web 应用 -> 服务器是否已经运行？
        |-- 否 -> 运行：python scripts/with_server.py --help
        |        然后使用辅助脚本，并编写简化的 Playwright 脚本
        |
        `-- 是 -> 先侦察、再行动：
            1. 导航并等待 networkidle
            2. 截图或检查 DOM
            3. 从渲染后的状态识别选择器
            4. 使用发现的选择器执行操作
```

## 示例：使用 with_server.py

要启动服务器，先运行 `--help`，再使用辅助脚本：

**单个服务器：**

```bash
python scripts/with_server.py --server "npm run dev" --port 5173 -- python your_automation.py
```

**多个服务器，例如后端加前端：**

```bash
python scripts/with_server.py \
  --server "cd backend && python server.py" --port 3000 \
  --server "cd frontend && npm run dev" --port 5173 \
  -- python your_automation.py
```

创建自动化脚本时，只包含 Playwright 逻辑；服务器会由辅助脚本自动管理：

```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch(headless=True) # 始终以无头模式启动 chromium
    page = browser.new_page()
    page.goto('http://localhost:5173') # 服务器已经运行并准备就绪
    page.wait_for_load_state('networkidle') # 关键：等待 JS 执行完成
    # ...你的自动化逻辑...
    browser.close()
```

## 先侦察、再行动模式

1. **检查渲染后的 DOM**：

   ```python
   page.screenshot(path='/tmp/inspect.png', full_page=True)
   content = page.content()
   page.locator('button').all()
   ```

2. **从检查结果中识别选择器**

3. **使用发现的选择器执行操作**

## 常见陷阱

- 错误示例：在动态应用中，等待 `networkidle` 之前就检查 DOM。
- 正确做法：检查前先等待 `page.wait_for_load_state('networkidle')`。

## 最佳实践

- **把随附脚本当作黑盒使用**：完成任务时，先判断 `scripts/` 中是否已有脚本可以帮忙。这些脚本能可靠处理常见的复杂流程，同时避免污染上下文。使用 `--help` 查看用法，然后直接调用。
- 使用 `sync_playwright()` 编写同步脚本。
- 完成后始终关闭浏览器。
- 使用描述性选择器，例如 `text=`、`role=`、CSS 选择器或 ID。
- 添加合适的等待，例如 `page.wait_for_selector()` 或 `page.wait_for_timeout()`。

## 参考文件

- **examples/** - 展示常见模式的示例：
  - `element_discovery.py` - 发现页面上的按钮、链接和输入框。
  - `static_html_automation.py` - 使用 file:// URL 自动化本地 HTML。
  - `console_logging.py` - 在自动化过程中捕获控制台日志。
