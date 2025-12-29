---
allowed-tools: Read, Write, Glob, WebSearch, Task, AskUserQuestion
description: 对目标话题进行初步调研，生成调研outline。用于学术调研、benchmark调研、技术选型等场景。
---

# Research Skill - 初步调研

## 触发方式
`/research <topic>`

## 执行流程

### Step 1: 模型内部知识生成初步框架
基于topic，利用模型已有知识生成：
- 该领域的主要研究对象/items列表
- 建议的调研字段框架

### Step 2: Web Search补充
启动1个web-search-agent（后台），根据topic自行设计搜索策略，补充最新的items和字段建议。

### Step 3: 询问用户已有字段
使用AskUserQuestion询问用户是否有已定义的字段文件，如有则读取并合并。

### Step 4: 生成Outline
合并所有信息，生成outline文件（YAML格式），包含：
- topic和基础配置
- items列表（调研对象）
- fields定义（调研字段）
- execution配置（批量大小等）

### Step 5: 输出并确认
- 保存到当前工作目录: `./{topic_slug}_outline.yaml`
- 展示给用户确认

## 输出路径
`{当前工作目录}/{topic_slug}_outline.yaml`

## 后续命令
- `/research-add-items` - 补充items
- `/research-add-fields` - 补充字段
- `/research-deep` - 开始深度调研
