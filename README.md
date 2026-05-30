# pya

`pya` 是一组轻量级、兼容 Codex 的中文技能集合，覆盖前端设计、浏览器自动化、程序规划、系统开发、代码质量、语言规范、毕业论文和答辩准备。

这个仓库用于集中保存可复用的技能说明，让它们便于整理、审查，并且可以按需选择安装。每个技能都放在自己的目录中，只有在和当前任务相关时才应该加载。

## 技能列表

| 技能 | 用途 |
| --- | --- |
| `frontend-design` | 指导生产级前端界面设计，强调清晰的视觉方向和精致的实现细节。 |
| `playwright` | 提供以命令行为主的 Playwright 浏览器自动化流程，用于导航、交互、截图和 UI 调试。 |
| `pya-is-skills` | 帮助把粗略的软件想法整理成可执行的程序设计、架构、模块、流程和实现计划。 |
| `webapp-testing` | 支持使用 Playwright 脚本、截图、浏览器日志和服务器生命周期辅助脚本测试本地 Web 应用。 |
| `system-feature-dev` | 按需求确认、代码理解、架构设计、实现、测试和总结 7 阶段开发系统功能。 |
| `codebase-explorer` | 分析 C++、Java、Python 项目的模块结构、入口、调用链、数据流和关键文件。 |
| `system-architect` | 设计系统架构、模块划分、数据库、API、数据流、安全和实现路线。 |
| `quality-review` | 检查 bug、测试缺口、异常处理、安全风险、重复代码和复杂实现。 |
| `thesis-writing` | 辅助编写软件系统毕业论文，包括摘要、绪论、需求分析、设计、实现、测试和总结。 |
| `thesis-defense` | 生成毕业答辩 PPT 大纲、讲稿、演示流程和常见问答。 |
| `language-cpp` | 指导 C++ 项目的 CMake、RAII、类设计、内存安全、性能和并发。 |
| `language-java` | 指导 Java/Spring Boot 项目的分层、DTO、事务、异常、权限和测试。 |
| `language-python` | 指导 Python/FastAPI/Django 项目的包结构、类型、依赖、异常、测试和工程化。 |

## 仓库结构

```text
.
|-- frontend-design/
|   |-- SKILL.md
|   `-- LICENSE.txt
|-- system-feature-dev/
|   |-- SKILL.md
|   `-- agents/
|-- codebase-explorer/
|   |-- SKILL.md
|   `-- agents/
|-- system-architect/
|   |-- SKILL.md
|   `-- agents/
|-- quality-review/
|   |-- SKILL.md
|   `-- agents/
|-- thesis-writing/
|   |-- SKILL.md
|   `-- agents/
|-- thesis-defense/
|   |-- SKILL.md
|   `-- agents/
|-- language-cpp/
|   |-- SKILL.md
|   `-- agents/
|-- language-java/
|   |-- SKILL.md
|   `-- agents/
|-- language-python/
|   |-- SKILL.md
|   `-- agents/
|-- playwright/
|   |-- SKILL.md
|   |-- agents/
|   |-- assets/
|   |-- references/
|   `-- scripts/
|-- pya-is-skills/
|   |-- SKILL.md
|   `-- agents/
|-- webapp-testing/
|   |-- SKILL.md
|   |-- examples/
|   `-- scripts/
`-- README.md
```

## 使用方式

克隆仓库：

```bash
git clone https://github.com/ppppp-2005/pya.git
```

然后只复制或链接你需要使用的技能目录到本地环境支持的技能目录中。启用任何技能前，请先阅读对应的 `SKILL.md`，确认它的适用场景和默认假设。

## 维护指南

- 保持每个技能只聚焦一个清晰的工作流或领域。
- 当行为、前置条件或使用方式变化时，更新对应的 `SKILL.md`。
- 将示例和辅助脚本放在依赖它们的技能目录附近。
- 避免添加会影响无关任务的宽泛指令。
- 在重新分发技能内容前，检查包含的许可证和声明文件。

## 贡献

欢迎提交 issue 和 pull request。对于较大的修改，请说明使用场景、预期行为、受影响的技能目录以及任何兼容性注意事项。

## 许可证

部分技能目录包含自己的许可证或声明文件。复用或重新分发前，请查看对应目录中的文件。
