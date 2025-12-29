---
description: 读取调研outline，为每个item启动独立agent进行深度调研。禁用task output。
allowed-tools: Bash, Read, Write, Glob, WebSearch, Task
---

# Research Deep - 深度调研

## 触发方式
`/research-deep`

## 执行流程

### Step 1: 自动定位Outline
在当前工作目录查找 `*_outline.yaml` 文件，读取items列表、fields定义、execution配置。

### Step 2: 断点续传检查
- 检查output_dir下已完成的JSON文件
- 跳过已完成的items

### Step 3: 分批执行
- 按batch_size分批（默认5个）
- 每个item启动1个web-search-agent（后台并行，禁用task output）
- 每个agent读取outline获取字段定义
- 输出结构化JSON到output_dir

### Step 4: 等待与监控
- 等待当前批次完成
- 启动下一批
- 显示进度

### Step 5: 汇总报告
全部完成后输出：
- 完成数量
- 失败/不确定标记的items
- 输出目录

## Agent配置
- 每批并行: 5个agent（可在outline中配置）
- 后台执行: 是
- Task Output: 禁用（agent完成时有明确输出文件）
- 断点续传: 是
