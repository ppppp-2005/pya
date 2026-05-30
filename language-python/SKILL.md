---
name: language-python
description: 中文 Python 系统开发技能。用户要求编写、分析、调试或完善 Python、FastAPI、Django、Flask、自动化脚本、数据处理或毕业设计 Python 系统时使用；关注包结构、类型标注、虚拟环境、依赖、异常处理、测试、API 和工程化。
---

# Python 系统开发

使用这个技能处理 Python 项目时，优先保证结构清晰、依赖明确、错误可定位。

## 工程结构

- 明确入口：`main.py`、CLI、FastAPI/Django 启动文件、脚本入口。
- 业务逻辑放到可测试的模块中，不要全部写在脚本顶层。
- 配置、常量、数据库、外部 API 客户端分离。
- 使用 `.env.example` 说明环境变量，避免提交真实密钥。

## 质量要求

- 为公共函数和复杂数据结构添加类型标注。
- 使用 `venv`、`requirements.txt` 或 `pyproject.toml` 管理依赖。
- 异常处理要保留上下文，不要裸 `except` 后静默通过。
- I/O、网络、数据库操作要考虑超时、重试和失败反馈。
- 测试重点覆盖业务逻辑、边界条件和失败场景。

## Web 框架建议

- **FastAPI**：使用 Pydantic 模型、依赖注入、清晰路由分组。
- **Django**：保持 Model、View、Serializer/Form、Service 边界清晰。
- **Flask**：避免单文件膨胀，按 blueprint/service/repository 拆分。

## 输出要求

- 给出运行、安装、测试命令。
- 说明模块职责和数据流。
- 对毕业设计项目，提供可写进论文的实现说明和测试说明。
