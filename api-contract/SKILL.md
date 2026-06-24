---
name: api-contract
description: 当计划或任务要生成项目的接口返回规范时调用，前后端统一请求/响应结构与协作流程，避免契约不一致。
version: 1.0.0
last_updated: 2026-03-04
owner: engineering
tags: [contract, api, backend, frontend, reliability]
---

# 定位
定义后端统一返回结构（`ApiResult` 系列）并明确前端/后端各自的检查点，确保接口请求、响应和错误处理达成一致。

# 适用场景
- 新增/修改 REST 接口（含 CRUD、分页、操作）
- 前端联调接口、后端输出规范需同步
- 需要对齐错误提示、分页参数、链路追踪数据的团队

# 不适用场景
- 仅做 UI 体验设计或视觉调整
- 接口完全在内部 SDK/库内使用且不跨团队

# 输入要求（最少）
- 接口目的（功能/业务）
- 是否携带数据（单对象/列表/分页）
- 需上报的上下文字段（如 `requestId`、trace）
- 返回的权限/错误信息需求

# 执行流程
1. 先决定返回类型：`ApiResult` / `ApiDataResult<T>` / `ApiPageResult<T>`。
2. 后端补齐 `ok`/`message`，并在分页中填 `limit`/`page`/`total`。
3. 前端统一判断 `ok`，对 `false` 统一触发全局提示/上报。
4. 双方在接口文档（Swagger/OpenAPI）中列出 `data` 的结构及错误码描述。
5. 所有接口必须带上统一鉴权/版本/跨域头部，便于零碎环境兼容。

# 输出产物（固定模板）
- `ApiResult` 系列定义（含泛型示例）
- 接口列表（按功能分类）+ 对应返回类型
- 错误码/提示映射表
- 前端操作建议（如 toast/表单 field 显示）
- 请求/响应示例（确保前后端都能复现）

# 质量门槛
- 所有 HTTP 接口必须返回 `ok` 布尔值
- 仅在 `ok=true` 时读取 `data`
- 分页接口务必返回 `limit`/`page`/`total`
- 后端错误必须伴随 HTTP 4xx/5xx 状态码
- 前端不得绕过统一错误处理，需统一上报 `message`

# 示例任务
- 正例：`GET /api/coupons?page=1&limit=20` ➜ `ApiPageResult<CouponVO>`，前端在 `total` 赋值分页组件链表。
- 反例：`GET /api/coupons` 直接返回 `[{...}]`，忽略 `ok`、`page`/`limit`，导致前端不停向后端请求。

# 维护清单
- 每次接口失败时回顾 `message` 内容并补充到文档
- 添加新分页接口时同步更新 `ApiPageResult` 示例
- 定期审查 `requestId`/trace 等字段是否齐全