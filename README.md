# skill-optimizer

Skill 创建后的质检工具。[Agent Skills](https://agentskills.io) 格式。

对已有 Skill 做质量审查、差距识别、优化落地。包含 5 种类型分类定位 + 7 维度审查清单。

## 方法论来源

- **5 种 Skill 分类体系**：参考 skills.sh 社区流行的 Skill 分类框架。同时受 Google Developer Relations Engineer Lavi Nigam 的博客 [*5 Agent Skill Design Patterns Every ADK Developer Should Know*](https://lavinigam.com/posts/adk-skill-design-patterns/) 启发——该文从内容设计模式角度归纳了 Tool Wrapper、Generator、Reviewer、Inversion、Pipeline 五种结构模板，与本工具的 Skill 类型分类定位侧重点不同但互为补充。
- **7 维度审查清单**：基于 Anthropic 博文 [*Equipping agents for the real world with Agent Skills*](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) 中提出的 Skill 设计原则以及 OpenClaw skill-builder 的实践经验提取，涵盖 Description 覆盖度、SKILL.md 长度、渐进式披露、自由度分层、前置/后置条件、失败回退路径、反模式检查。

## 5 种 Skill 分类体系

对目标 Skill 进行类型定位，以确定审查侧重点：

| # | 类型 | 核心特征 | 审查侧重点 |
|---|------|---------|-----------|
| 1 | **Code & Development** | 代码生成/审查/调试/优化，框架最佳实践 | 代码示例准确性、框架版本时效性 |
| 2 | **Data & Information Management** | 数据收集/处理/分析/查询/知识管理 | 数据格式规范、知识结构清晰度 |
| 3 | **Automation & Orchestration** | 多步骤自动化工作流、多 Agent 协调 | 工作流完整性、步骤衔接、失败处理 |
| 4 | **Specialized Domain & Production** | 特定行业/领域的专家级能力 | 领域知识准确性、边界声明 |
| 5 | **Reasoning & Strategic** | 增强推理/规划/战略决策的元技能 | 推理框架清晰度、决策树完整性 |

一个 Skill 可能包含主类型 + 辅类型的组合。类型决定审查时的侧重方向。

## 7 维度审查清单

| # | 维度 | 合格标准 |
|---|------|---------|
| 1 | **Description 覆盖度** | 包含"做什么"+"何时触发"，覆盖至少 5 种常见触发场景 |
| 2 | **SKILL.md 长度** | 30-80 行理想，80 行绝对上限；细节下沉到引用文件 |
| 3 | **渐进式披露** | 每个引用文件有明确的「何时加载」标注，嵌入在工作流对应位置 |
| 4 | **自由度分层** | 每步标注自由度等级（高/中/低），低自由度使用"必须/禁止"强措辞 |
| 5 | **前置/后置条件** | 有明确的触发前置检查和完成标准/交付物定义 |
| 6 | **失败回退路径** | 主要步骤有简要失败处理指引，有明确的"最多重试 N 次"上限 |
| 7 | **反模式检查** | 无 README.md/INSTALLATION.md 等冗余文件，无重复信息 |

## 安装

```bash
npx skills add lpreterite/skill-optimizer
```

或直接通过 GitHub：

```bash
npx skills add https://github.com/lpreterite/skill-optimizer/tree/main/skills/skill-optimizer
```

## 结构

```
skills/skill-optimizer/
├── SKILL.md                               # 主 Skill 文件（触发条件 + 工作流）
└── references/
    ├── classification.md                  # 5 种 Skill 分类体系 + 定位方法
    └── review-checklist.md                # 7 维度审查清单（合格标准 + 修复建议）
```

## 工作流

```
[加载目标 Skill] → [定位 Skill 类型] → [逐项审查 7 维度] → [产出优化方案] → [队长确认] → [执行优化]
```

## 用法

1. 在支持 [Agent Skills](https://agentskills.io) 的 coding agent 中安装
2. 对 agent 说"帮我对这个 skill 做审查"
3. agent 自动加载 skill-optimizer 完成 5 种分类定位 + 7 维度审查

## License

MIT
