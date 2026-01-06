# Deep Research Skill for Claude Code

[English](README.md) | [中文](README.zh.md)

> 灵感来源：[RhinoInsight: Improving Deep Research through Control Mechanisms for Model Behavior and Context](https://arxiv.org/abs/2511.18743)

Claude Code 的结构化调研工作流技能，支持两阶段调研：outline生成（可扩展）和深度调查。人在回路设计确保每个阶段的精确控制。

## 使用场景

- **学术研究**：论文综述、benchmark评测、文献分析
- **技术研究**：技术对比、框架评估、工具选型
- **市场研究**：竞品分析、行业趋势、产品比较
- **尽职调查**：公司研究、投资分析、风险评估

## 安装

```bash
# 中文版
cp -r skills/research-zh ~/.claude/skills/research

# 必需：安装agent
cp agents/web-search-agent.md ~/.claude/agents/
```

## 命令

> **注意**：使用 `run /research` 而非直接 `/research`，因为斜杠命令与内置命令冲突。

| 命令 | 描述 |
|------|------|
| `run /research` | 生成包含items和fields的调研outline |
| `run /research/add-items` | 向现有outline添加更多items |
| `run /research/add-fields` | 向现有outline添加更多fields |
| `run /research/deep` | 使用并行agents对每个item进行深度调研 |
| `run /research/report` | 从JSON结果生成markdown报告 |

## 工作流 & 示例

> 示例：调研 "AI Agent Demo 2025"

### 阶段1：生成Outline
```
run /research AI Agent Demo 2025
```
**输出：** `ai-agent-demo/outline.yaml`
```yaml
topic: "AI Agent Demo & 测评 (2025.9-2025.12)"
items:
  - name: "ChatGPT Agent"
    category: "浏览器Agent"
    brief: "OpenAI统一Agent，2025年7月发布"
  - name: "Claude Computer Use"
    category: "桌面Agent"
    brief: "Anthropic桌面操控Agent"
  # ... 另外15个items
```

### 阶段2：深度调研
```
run /research/deep
```
**输出：** `ai-agent-demo/results/ChatGPT_Agent.json`
```json
{
  "basic_info": {
    "name": "ChatGPT Agent",
    "company": "OpenAI",
    "release_date": "2025-07-17",
    "pricing": "Pro $200/月, Plus $20/月"
  },
  "tech_specs": {
    "underlying_model": "GPT-5系列",
    "agent_type": "统一型自主Agent"
  }
}
```

### 阶段3：生成报告
```
run /research/report
```
**输出：** `ai-agent-demo/report.md` - 带目录和所有item的Markdown报告

## 参考文献

- RhinoInsight: Improving Deep Research through Control Mechanisms for Model Behavior and Context

## 许可证

MIT
