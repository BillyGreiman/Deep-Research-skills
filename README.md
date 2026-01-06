# Deep Research Skill for Claude Code

[English](README.md) | [中文](README.zh.md)

> Inspired by [RhinoInsight: Improving Deep Research through Control Mechanisms for Model Behavior and Context](https://arxiv.org/abs/2511.18743)

A structured research workflow skill for Claude Code, supporting two-phase research: outline generation (extensible) and deep investigation. Human-in-the-loop design ensures precise control at every stage.

## Use Cases

- **Academic Research**: Paper surveys, benchmark reviews, literature analysis
- **Technical Research**: Technology comparison, framework evaluation, tool selection
- **Market Research**: Competitor analysis, industry trends, product comparison
- **Due Diligence**: Company research, investment analysis, risk assessment

## Installation

```bash
# English version
cp -r skills/research-en ~/.claude/skills/research

# Required: Install agent
cp agents/web-search-agent.md ~/.claude/agents/
```

## Commands

> **Note**: Use `run /research` instead of `/research` directly, as slash commands conflict with built-in commands.

| Command | Description |
|---------|-------------|
| `run /research` | Generate research outline with items and fields |
| `run /research/add-items` | Add more items to existing outline |
| `run /research/add-fields` | Add more fields to existing outline |
| `run /research/deep` | Deep research each item with parallel agents |
| `run /research/report` | Generate markdown report from JSON results |

## Workflow & Example

> Example: Researching "AI Agent Demo 2025"

### Phase 1: Generate Outline
```
run /research AI Agent Demo 2025
```
**Output:** `ai-agent-demo/outline.yaml`
```yaml
topic: "AI Agent Demo & Review (2025.9-2025.12)"
items:
  - name: "ChatGPT Agent"
    category: "Browser Agent"
    brief: "OpenAI unified Agent, released July 2025"
  - name: "Claude Computer Use"
    category: "Desktop Agent"
    brief: "Anthropic desktop control Agent"
  # ... 15 more items
```

### Phase 2: Deep Research
```
run /research/deep
```
**Output:** `ai-agent-demo/results/ChatGPT_Agent.json`
```json
{
  "basic_info": {
    "name": "ChatGPT Agent",
    "company": "OpenAI",
    "release_date": "2025-07-17",
    "pricing": "Pro $200/mo, Plus $20/mo"
  },
  "tech_specs": {
    "underlying_model": "GPT-5 series",
    "agent_type": "Unified autonomous Agent"
  }
}
```

### Phase 3: Generate Report
```
run /research/report
```
**Output:** `ai-agent-demo/report.md` - Markdown report with TOC and all items

## References

- RhinoInsight: Improving Deep Research through Control Mechanisms for Model Behavior and Context

## License

MIT
