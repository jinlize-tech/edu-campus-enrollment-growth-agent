---
name: edu-campus-enrollment-growth-agent-core
display_name: '校区招生增长诊断核心助手'
display_name_en: 'Campus Enrollment Growth Agent Core Assistant'
description: '为校区招生增长诊断提供输入校验、结构化整理和成果模板支持'
description_zh: '校验校区招生目标、历史数据、渠道、课程、团队、竞争环境和近期问题的完整性，并整理为可交付结构'
description_en: 'Validate structured inputs and prepare an output-ready structure for the parent agent.'
examples_zh:
  - '检查我提交的输入字段是否完整'
  - '整理这份业务资料并标出冲突项'
examples_en:
  - 'Check whether my structured input is complete.'
  - 'Organize the supplied business information and flag conflicts.'
version: 1.0.2
author: '广州金励泽科技服务有限公司'
---

# 校区招生增长诊断核心助手

本Skill是Agent内部的结构化支持组件，不替代Agent的诊断、方案设计、人工确认和复盘职责。

## 产品契约

- 核心任务：校区招生现状诊断、增长策略、行动计划和复盘。
- 主要风险：缺少完整数据时给出确定性经营结论
- 去重边界：与校长经营OS LITE区分：仅围绕招生增长，不提供综合经营系统；与单项活动策划相比含诊断和多步骤编排。

## 输入

- 校区招生目标
- 历史数据
- 渠道
- 课程
- 团队
- 竞争环境和近期问题

## 工作流程

1. 用户提供结构化JSON时，先执行 @scripts/validate_input.js。
2. 输入缺失时返回缺失字段，不要求Agent自行编造。
3. 输入冲突时返回确认项，暂停正式结论。
4. 安全检查通过后，按 @templates/OUTPUT_TEMPLATE.md 建立空结构。
5. 将结构交回Agent继续专业处理。

## 专属检查

- 先锁定招生目标、课程、时间窗口、目标客群和可得预算，再讨论创意与渠道。
- 把假设线索量、转化率和单价分别列示，不以单一历史数据外推全部结果。
- 逐项检查渠道费用、人员投入、活动固定成本和单人可变成本，防止重复计费。
- 对宣传承诺、价格、名额、效果和第三方素材做合规与真实性复核。

## 边界

不得生成虚假口碑、虚假名额、违法承诺或未经授权的宣传素材。

本Skill不产生最终业务结论，不调用外部收费API，不保存用户数据。
