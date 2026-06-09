# skill-optimizer

Skill 创建后的质检工具。[Agent Skills](https://agentskills.io) 格式。

对已有 Skill 做质量审查、差距识别、优化落地。包含 5 种类型分类定位 + 7 维度审查清单。

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
├── SKILL.md                               # 主 Skill 文件
└── references/
    ├── classification.md                  # 5 种 Skill 分类体系
    └── review-checklist.md                # 7 维度审查清单
```

## 用法

1. 在支持 [Agent Skills](https://agentskills.io) 的 coding agent 中安装
2. 对 agent 说"帮我对这个 skill 做审查"
3. agent 自动加载 skill-optimizer 完成 7 维度审查

## License

MIT
