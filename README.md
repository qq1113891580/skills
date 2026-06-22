# Claude Code Skills 清单

本目录提供可直接使用的 Claude Code Skills，覆盖从创意探索、规划、开发、测试到交付的完整工作流。

> 模板状态：生产可维护版（v1）

## 包含技能（19 个）

### 开发流程

| 技能 | 说明 |
|------|------|
| `brainstorming` | 创意工作前必用 — 探索用户意图、需求与设计，再动手实现 |
| `writing-plans` | 有需求规格或待办清单时，先写实施计划再编码 |
| `executing-plans` | 在独立会话中按计划执行实施，带审查检查点 |
| `test-driven-development` | 实现功能或修 bug 前，先写测试再写实现 |
| `verification-before-completion` | 完成工作前必须运行验证命令，用证据支撑结论 |
| `finishing-a-development-branch` | 实现完成、测试通过后，引导合并/PR/清理的结构化选项 |

### 代码质量与审查

| 技能 | 说明 |
|------|------|
| `code-simplifier` | 代码质量专家，专注于改进清晰度、一致性与可维护性 |
| `systematic-debugging` | 遇到 bug、测试失败或异常行为时，系统化定位根因再修复 |
| `receiving-code-review` | 收到代码审查反馈后，技术严谨地验证再实施，而非盲目接受 |
| `requesting-code-review` | 完成任务或实现重大功能后，请求审查以验证质量 |

### 架构与设计

| 技能 | 说明 |
|------|------|
| `api-contract` | 前后端接口对接时，统一请求/响应结构与协作流程 |
| `frontend-design` | 创建高辨识度、可直接部署的前端界面与组件 |
| `ui-ux-pro-max` | UI/UX 设计智能，涵盖 50+ 风格、161 色板、10 技术栈 |
| `new-project-template` | 生成项目设计文档套件（系统设计、API 设计、开发指南等） |

### 并行与子代理

| 技能 | 说明 |
|------|------|
| `dispatching-parallel-agents` | 面对 2+ 个独立任务时，并行调度子代理执行 |
| `subagent-driven-development` | 在当前会话中用子代理执行含独立任务的实施计划 |

### Git 与工作区

| 技能 | 说明 |
|------|------|
| `using-git-worktrees` | 需要隔离工作区时，通过 git worktree 创建独立环境 |
| `using-superpowers` | 会话启动时建立技能发现与调用机制 |
| `writing-skills` | 创建、编辑或验证技能，部署前确保可用 |

## 使用方式

1. 保持目录结构：`.claude/skills/<skill-name>/SKILL.md`
2. 在 Claude Code 中描述任务时，给出明确目标、范围和约束。
3. 让 Claude 自动匹配技能，或在提示中明确提到技能名称。

## 建议

- 每个技能只做一件事
- `description` 要写"触发条件"，避免泛化
- 技能内容优先写"步骤 + 验收标准"

## 统一模板规范（v1）

每个 `SKILL.md` 建议包含以下固定区块：

1. Frontmatter：`name`、`description`、`version`、`last_updated`、`owner`、`tags`
2. 定位
3. 适用场景 / 不适用场景
4. 输入要求（最少）
5. 执行流程
6. 输出产物（固定模板）
7. 质量门槛
8. 示例任务（正例/反例）
9. 维护清单
