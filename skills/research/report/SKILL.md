---
description: 将deep调研结果汇总为markdown报告，覆盖所有字段，跳过不确定值。
allowed-tools: Read, Write, Glob, Bash
---

# Research Report - 汇总报告

## 触发方式
`/research-report`

## 执行流程

### Step 1: 定位结果目录
在当前工作目录查找 `*/outline.yaml`，读取topic和output_dir配置。

### Step 2: 生成Python转换脚本
在 `{topic}/` 目录下生成 `generate_report.py`，脚本要求：
- 读取output_dir下所有JSON
- 读取fields.yaml获取字段结构
- 覆盖每个JSON的所有字段值
- 跳过值包含[不确定]的字段
- 跳过uncertain字段
- 生成markdown报告格式：目录（带锚点跳转）+ 详细内容（按字段分类）
- 保存到 `{topic}/report.md`

### Step 3: 执行脚本
运行 `python {topic}/generate_report.py`

## 输出
- `{topic}/generate_report.py` - 转换脚本
- `{topic}/report.md` - 汇总报告
