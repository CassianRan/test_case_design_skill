---
name: test-case-design
description: This skill should be used when generating test cases, writing test cases, designing test cases, supplementing exception scenarios and boundary values, designing complex interaction test cases, outputting standardized test cases, compatibility testing, adaptation testing, API testing, security testing, UI visual testing, mobile/App/mini-program/H5/desktop/PC Web testing, AI Agent testing, linkage testing, or routing testing. Only focuses on writing test cases, does not involve test plans, test strategies, or test automation scripts.
---

## 执行流程

1. **识别用例类型**：
   - 含"接口测试"/"API 测试" → 接口测试用例
   - 含"Agent 测试"/"Agent"/"智能体" → Agent 测试用例
   - 默认 → 功能测试用例
2. **加载能力文件**：始终加载 `templates/common-rules.md`（规则），能力文件按类型选择：
   - 接口测试 → `core-capabilities/api-testing.md`
   - Agent 测试 → `core-capabilities/agent-testing.md`+ `core-capabilities/functional-testing.md中的第一部分：测试用例设计方法+第二部分：测试用例质量标准` 
   - 功能测试 → `core-capabilities/functional-testing.md`
3. **加载平台专项**（接口测试跳过此步骤）：
   - 匹配平台关键词 → 加载 `platform/{平台}.md`
4. **生成用例**：按加载的能力文件以及平台专项生成测试用例
5. **自查**：
   - 接口测试 → `checklists/api-checklist.md`
   - Agent 测试 → `checklists/agent-checklist.md` + `checklists/common-checklist.md中的一、功能测试检查清单`
   -  Agent 测试+平台 → `checklists/agent-checklist.md` + `checklists/common-checklist.md中的一、功能测试检查清单`+  `checklists/{平台}-checklist.md`
   - 功能测试+平台 → `checklists/common-checklist.md`+ `checklists/{平台}-checklist.md` 
   - 功能测试无平台 → `checklists/common-checklist.md`
6. **输出**：按 `examples/format-spec.md` 规定的表格格式，Markdown 表格输出

## 能力边界
✅ 可生成：功能测试、接口测试、AI agent测试、基础安全测试、平台专项测试
❌ 不可生成：测试方案、测试策略、测试计划、渗透测试执行、漏洞扫描、性能压测（并发/压力/负载）、自动化脚本

## 指令映射表

> 规则文件始终加载 `templates/common-rules.md`。能力文件按用例类型选择，平台文件按需叠加。

### 能力文件

| 关键词触发 | 加载 | 说明 |
|-----------|------|------|
| "接口测试"、"API 测试" | `core-capabilities/api-testing.md` | 独立使用，不叠加平台 |
| "Agent 测试"、"Agent"、"智能体" | `core-capabilities/agent-testing.md`+`core-capabilities/functional-testing.md中的第一部分：测试用例设计方法+第二部分：测试用例质量标准` | 可叠加任意平台 |
| 默认 | `core-capabilities/functional-testing.md` | 功能测试 |

### 平台文件（叠加到能力文件之上，接口测试除外）

| 关键词触发 | 加载 | 说明 |
|-----------|------|------|
| "移动端测试"、"App 测试" | `platform/mobile-app.md` | 手势/中断/网络/权限/推送/兼容/性能 |
| "小程序测试" | `platform/mini-program.md` | 生命周期/授权/分享/支付/跳转/订阅 |
| "移动 Web 测试"、"H5 测试" | `platform/mobile-web.md` | 响应式/触摸/浏览器/视口/H5/SEO |
| "桌面端测试"、"桌面应用测试" | `platform/desktop.md` | 窗口/快捷键/文件/系统集成/多显示器 |
| "PC Web 测试"、"Web 端测试" | `platform/pc-web.md` | 浏览器/布局/键盘/表单/会话/路由/拖拽 |
