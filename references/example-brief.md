# 样例：Presentation Strategy Brief（端到端范例）

> 本文件是 `presentation-report-preflight` Skill 的参考样例，迁移到 Skill 后路径为 `references/example-brief.md`。
> 它演示「一段真实输入 → 一份完整 brief」的全过程，作为输出质量基准与回归测试用例。
> 包含两份样例：**样例 A（full 档，销售提案）** 与 **样例 B（lite 档，内部周会）**，分别对应 SKILL.md 的两套输出骨架。

---

# 样例 A：full 档（销售提案，交给 huashu-design）

---

## 目录

**样例 A（full 档，销售提案）**
- [0. 模拟输入（用户给的原始材料）](#0-模拟输入用户给的原始材料)
- [Direction Snapshot + Timing Brief（确认点）](#direction-snapshot--timing-brief确认点)
- [摘要（人读）](#摘要人读)
- [Timing Brief（时长策略）](#timing-brief时长策略)
- [Slide Title Chain](#slide-title-chain)
- [Universal Handoff Contract（权威）](#universal-handoff-contract权威)
- [Adapter-specific Appendix — `huashu-design`](#adapter-specific-appendix-—-huashu-design)
- [交付前自检（最弱环）](#交付前自检最弱环)

**样例 B（lite 档，内部周会）**
- [样例 B：lite 档（内部周会，5 分钟）](#样例-b：lite-档内部周会5-分钟)


## 0. 模拟输入（用户给的原始材料）

> 用户消息：
> “帮我做一份卖给中型电商公司的销售提案，我们产品是自动化对账 SaaS。下面是销售给我的素材，做完先别出 HTML，后面交给 huashu-design。听众是客户的财务 VP 和 CFO，现场 20 分钟。”
>
> 附带素材（节选）：
> - 目标客户：GMV 5–50 亿的中型电商，财务团队 8–15 人。
> - 痛点访谈：财务每周花约 6 小时手工核对支付/平台/银行三方流水，月底关账平均 3 天。
> - 我们的数据：已接入 40+ 支付与平台渠道；试点客户对账周期从 3 天降到 2 小时；差错率从约 0.8% 降到 0.05%。
> - 定价：每年 18 万，含实施。
> - 竞品：客户现在用 Excel + 一个老 ERP 模块。
> - 试点客户：某家居电商（已授权具名）、某美妆电商（仅可匿名）。

**Skill 的推断**：场景=销售提案；听众=财务高管（VP/CFO）；目标动作=同意进入 POC/试点；时长=20 分钟；语言=中文；下游=huashu-design（已指定）。
唯一标 `待补` 项：ROI 测算口径（客户自身人力成本未知）、美妆客户能否具名。→ 不阻塞方向确认。

---

## Direction Snapshot + Timing Brief（确认点）

**Direction Snapshot**
- 场景：销售提案（B2B SaaS，自动化对账）。
- 听众：客户方财务 VP 与 CFO，关注 ROI、风险、实施成本和对现有 ERP 的影响。
- 目标动作：让客户当场同意启动 4 周、单一业务线的付费 POC。
- 成功标准：离场时双方就 POC 范围与时间达成口头一致，并约定下一次对接会。
- brief 档位：`full`，因为这是对外销售提案且涉及 ROI、案例、合规与决策请求。
- 推荐叙事骨架：Problem → Solution → Benefit，理由是财务高管按“证据→收益”决策。
- 下游目标：`huashu-design`。
- 待补：ROI 客户侧口径、美妆客户具名授权、我方 VI。

**Timing Brief**
- 总时长预估：20 分钟。
- 正式讲述 / Q&A：讲述 15 分钟，Q&A 5 分钟。
- 建议页数：12 页，其中 1 页为安全/合规附录。
- 节奏：快开场、稳证据、行动收束；Problem 控制在 5 分钟内。
- 重点页：收益页 6–8、案例页 9、POC 行动页 10。
- 可压缩版本：若只有 10 分钟，保留 1、2、4、6、8、9、10 七页。
- 超时风险：ROI 解释和案例细节容易拖长，需把 slide 8 的计算口径提前准备好。

**确认问题**：我会按这个方向和时长生成 brief。方向/时长对吗？要改听众、目标、叙事骨架、时长，还是直接继续？

> 模拟用户确认：“继续。”

---

## 摘要（人读）

- **一句话主张**：把月底关账从 3 天压到 2 小时、差错率降一个数量级，第一年就能用省下的人力成本覆盖订阅费。
- **听众听完应记住**：手工三方对账正在每月吃掉财务团队 ~3 人日，且差错风险不可控。
- **听众听完应做**：当场同意启动一个 4 周、单一业务线的付费 POC。
- **推荐叙事骨架**：Problem → Solution → Benefit（备选：客户案例四段式）。理由：财务高管对“证据—收益”链路敏感，先用其自身痛点的量化把问题立住，再给可验证的收益，比功能罗列更有效。
- **推荐时长策略**：20 分钟拆成 15 分钟讲述 + 5 分钟 Q&A，12 页以内；ROI 与案例页是重点，不在功能页消耗时间。
- **状态**：含 2 项待补（ROI 客户侧口径、美妆客户具名授权），不影响主线。

---

## Timing Brief（时长策略）

- **总时长预估**：20 分钟。
- **正式讲述 / Q&A**：15 分钟讲述 + 5 分钟 Q&A。
- **建议页数**：12 页，其中 slide 12 是附录，只在被问到安全/权限/合规时使用。
- **平均节奏**：开场 30 秒；Problem 4–5 分钟；Solution 4 分钟；Benefit/证据 5–6 分钟；行动与收尾 2 分钟。
- **重点页预计耗时**：slide 6–8 各 1.5–2 分钟；slide 9 案例 2 分钟；slide 10 POC 请求 1 分钟。
- **可压缩版本**：10 分钟版本保留 slide 1、2、4、6、8、9、10；附录只答疑使用。
- **超时风险**：ROI 口径和案例故事容易拖长；会前准备三档 ROI 模板，案例只讲一个具名客户。

---

## Slide Title Chain

| 页码 | 叙事阶段 | 结论式标题 | 本页作用 | 证据 / 素材 | 备注 |
| --- | --- | --- | --- | --- | --- |
| 1 | 钩子 | 你的财务团队每月有 3 个人日，正消失在三方对账里 | 用听众自身痛点开场，制造“这说的就是我”的代入 | 痛点访谈：6 小时/周 × 团队规模 | 前 30 秒不讲产品 |
| 2 | Problem | 手工对账的真正代价不是时间，是月底 3 天关账期里的不可控差错 | 把痛点从“慢”升级到“有风险” | 关账 3 天、差错率 ~0.8% | 引出风险，而非效率叙事 |
| 3 | Problem | Excel + 老 ERP 模块撑不住 40+ 渠道的对账复杂度 | 点出现状方案的天花板（隐性竞品定位） | 渠道数 40+；现状=Excel+ERP | 不点名贬低，讲结构性局限 |
| 4 | Solution | 自动化对账把三方流水核对从“人找差异”变成“系统报差异” | 给出方案的核心机制 | 产品机制：自动归集+差异标注 | 一页一观点，配流程示意 |
| 5 | Solution | 已接入 40+ 支付与平台渠道，接入即用，无需改造现有 ERP | 消除“要不要换系统”的顾虑 | 渠道清单；与 ERP 并存 | 降低迁移恐惧 |
| 6 | Benefit | 对账周期：3 天 → 2 小时（试点实测） | 收益证据 1：速度 | 试点数据，注明“试点客户实测” | 双柱对比图 |
| 7 | Benefit | 差错率：0.8% → 0.05%，一个数量级 | 收益证据 2：质量/风险 | 试点数据 | KPI 数字卡 |
| 8 | Benefit | 第一年订阅费由省下的人力成本覆盖（ROI 测算） | 把收益换算成钱，对 CFO 说话 | 18 万/年 vs 人力节省 `待补口径` | 标待补，现场用客户自报工资填 |
| 9 | 证据 | 某家居电商上线 8 周后，关账提前 2.5 天 | 第三方背书，降低风险感 | 具名客户案例（已授权） | 案例页，含 logo |
| 10 | 行动 | 建议从一条业务线起步，做 4 周付费 POC | 给一个低门槛的下一步 | POC 范围/周期/交付物 | CTA 必须具体可执行 |
| 11 | 收尾 | 不是要你换掉财务团队，是把他们从对账里解放出来 | 金句收尾，呼应开场钩子 | —— | 留一句可复述的话 |
| 12 | 附录 | 安全、权限与数据合规说明 | 预置高风险 Q&A 的兜底页 | 合规要点 | 仅在被问到时翻出 |

---

## Universal Handoff Contract（权威）

```yaml
brief_tier: full
run_mode: interactive
output_language: zh
handoff_mode: universal_plus_adapter
adapter_resolution:
  requested: huashu-design
  resolved: huashu-design
  status: matched
deck_intent:
  scenario: 销售提案（B2B SaaS，自动化对账）
  audience: 客户方财务高管——财务 VP 与 CFO，懂业务、对 ROI 与风险敏感
  desired_action: 当场同意启动 4 周、单一业务线的付费 POC
  success_criteria: 离场时双方就 POC 范围与时间达成口头一致；约定下一次对接会
narrative:
  framework: Problem → Solution → Benefit
  rationale: 财务高管按“证据→收益”决策；先用其自身可量化的痛点立问题，再给可验证收益，优于功能罗列
  hook:
    type: 数据 + 代入
    content: “你的财务团队每月有约 3 个人日，正消失在三方对账里”——用听众自身规模反推
    first_30s: 不提产品名，只讲对方的真实一周
  stages: [钩子, Problem, Solution, Benefit, 行动, 收尾]
  closing:
    type: 金句 + 决策请求
    content: “不是替换财务团队，是把他们从对账里解放出来” + 启动 POC
runtime_plan:
  total_duration: 20 分钟
  talk_time: 15 分钟
  qa_time: 5 分钟
  slide_count_target: 12
  pacing: 快开场、稳证据、行动收束；Problem 控制在 5 分钟内
  section_allocation:
    - section: 钩子 + Problem
      duration: 5 分钟
      slides: [1, 2, 3]
    - section: Solution
      duration: 4 分钟
      slides: [4, 5]
    - section: Benefit + 证据
      duration: 6 分钟
      slides: [6, 7, 8, 9]
    - section: 行动 + 收尾
      duration: 2 分钟
      slides: [10, 11]
    - section: Q&A
      duration: 5 分钟
      slides: [12]
  heavy_slides: [6, 8, 9]
  cut_if_short_on_time: [3, 5, 7, 11]
  overrun_risks:
    - ROI 口径待补，slide 8 容易被追问拖长
    - 案例页如果讲两个客户会超时，默认只讲具名家居客户
slide_plan:
  - slide: 1
    stage: 钩子
    spec_density: full
    title: 你的财务团队每月有 3 个人日，正消失在三方对账里
    job: 制造代入，建立问题相关性
    evidence: 痛点访谈 6 小时/周
    asset_hint: 全屏数字 + 一周日历隐喻
    visual_hint: 极简、留白大、单一焦点
    speaker_note_focus: 开场不讲产品，先描述对方的一周
    content_spec:
      content_role: hook
      primary_message: 手工三方对账每月正在消耗约 3 个人日，且这不是财务团队最该花时间的地方
      on_slide_copy:
        headline: 你的财务团队每月有 3 个人日，正消失在三方对账里
        subheadline: 以 8-15 人财务团队、每周 6 小时人工核对估算
        body_blocks:
          - type: callout
            text: 先问一个问题：这 3 个人日，是在创造管理价值，还是在搬运流水？
        footnotes:
          - 数据来源：客户访谈，6 小时/周；团队规模按 8-15 人区间估算
      visual_blueprint:
        primary_visual:
          type: kpi_card
          purpose: 用单一大数字建立痛点代入
          data_refs: [ev-manual-hours]
          asset_refs: []
          annotation: 强调“每月 3 个人日”而不是产品能力
        layout_intent:
          composition: 全屏大数字，底部小字说明估算口径
          hierarchy: 3 个人日 > 每周 6 小时 > 访谈来源
          density: low
      data_requirements:
        metrics:
          - value: 每周 6 小时，折算约每月 3 个人日
            unit: 小时/人日
            source_ref: ev-manual-hours
        missing_sources: []
      asset_requirements:
        required: []
        optional: []
        fallback: 无需图片，用大数字和日历隐喻即可
      narration:
        talk_time: 30 秒
        key_talking_points:
          - 先讲客户的一周，不讲产品名
          - 把时间成本转成管理注意力成本
      constraints:
        must_include: [客户访谈口径, 每月 3 个人日]
        must_avoid: [直接开场介绍公司或功能, 把估算说成精确审计结果]
        split_if: []
        placeholder_policy: honest_placeholder
  - slide: 2
    stage: Problem
    spec_density: full
    title: 手工对账的真正代价不是时间，是月底 3 天关账期里的不可控差错
    job: 把痛点从“慢”升级到“风险”
    evidence: 关账 3 天、差错率 ~0.8%
    asset_hint: 风险链路图
    visual_hint: 关账周期 + 差错风险并列
    speaker_note_focus: 引出风险，而非效率叙事
    content_spec:
      content_role: setup
      primary_message: 手工对账的问题不止效率低，更会把差错风险集中到月底关账窗口
      on_slide_copy:
        headline: 慢只是表象，风险才是 CFO 真正在意的成本
        subheadline: 月底 3 天关账期内，人工核对越多，差错越难追溯
        body_blocks:
          - type: bullets
            text: 关账周期平均 3 天；历史差错率约 0.8%；差错发现越晚，追溯成本越高
        footnotes:
          - 数据来源：客户访谈与历史对账记录，差错率为客户自报
      visual_blueprint:
        primary_visual:
          type: diagram
          purpose: 展示手工核对如何放大关账风险
          data_refs: [ev-close-cycle, ev-error-rate]
          asset_refs: []
          annotation: 从“流水核对”指向“差错追溯”和“关账延迟”
        layout_intent:
          composition: 左侧关账 3 天，右侧风险链路
          hierarchy: 风险结论 > 两个数字 > 原因链路
          density: medium
      data_requirements:
        metrics:
          - value: 3 天
            unit: 关账周期
            source_ref: ev-close-cycle
          - value: 约 0.8%
            unit: 差错率
            source_ref: ev-error-rate
        missing_sources: []
      asset_requirements:
        required: []
        optional: []
        fallback: 用流程风险图替代任何截图
      narration:
        talk_time: 1.5 分钟
        key_talking_points:
          - 承认时间成本重要，但 CFO 更关心可控性
          - 把后续方案定位成风险控制工具
      constraints:
        must_include: [3 天关账, 约 0.8% 差错率, 客户自报口径]
        must_avoid: [恐吓式表达, 夸大成重大合规事故]
        split_if: [如果加入具体事故案例，拆成独立案例页]
        placeholder_policy: honest_placeholder
  - slide: 3
    stage: Problem
    spec_density: compact
    title: Excel + 老 ERP 模块撑不住 40+ 渠道的对账复杂度
    job: 点出现状方案的结构性天花板
    evidence: 渠道数 40+；现状=Excel+ERP
    asset_hint: 渠道 logo 墙或复杂度矩阵
    visual_hint: 多渠道输入汇入人工核对瓶颈
    speaker_note_focus: 不贬低现有方案，讲复杂度变化
    content_spec:
      content_role: comparison
      primary_message: 现有 Excel + 老 ERP 不是“不够努力”，而是已经不适合 40+ 渠道的复杂度
      on_slide_copy:
        headline: 40+ 渠道之后，人工表格会变成系统瓶颈
        subheadline: 支付、平台、银行流水分散，差异需要跨系统定位
        body_blocks:
          - type: bullets
            text: 渠道多；格式不一；异常追溯依赖人工经验；ERP 只能覆盖部分链路
        footnotes:
          - 渠道数来自产品接入能力；客户当前方案来自销售素材
      visual_blueprint:
        primary_visual:
          type: diagram
          purpose: 展示多渠道输入汇入人工核对瓶颈
          data_refs: [ev-channel-count, ev-current-stack]
          asset_refs: [asset-channel-list]
          annotation: 不贬低 ERP，只说明它不是三方流水自动核对系统
        layout_intent:
          composition: 左侧 40+ 渠道，右侧 Excel+ERP 瓶颈
          hierarchy: 复杂度 > 现状方案 > 天花板
          density: medium
      data_requirements:
        metrics:
          - value: 40+
            unit: 支付与平台渠道
            source_ref: ev-channel-count
        missing_sources: []
      asset_requirements:
        required:
          - asset_refs: [asset-channel-list]
            reason: 需要渠道清单证明 40+ 不是空泛说法
        optional: []
        fallback: 若不展示具体渠道名，用“渠道类型”分组图替代 logo 墙
      narration:
        talk_time: 1.5 分钟
        key_talking_points:
          - 尊重客户已有系统
          - 说明复杂度已经超过人工核对模型
      constraints:
        must_include: [40+ 渠道, Excel + 老 ERP 当前状态]
        must_avoid: [贬低客户 ERP, 罗列全部渠道导致拥挤]
        split_if: [如果要逐一展示渠道 logo，拆为附录或生态页]
        placeholder_policy: honest_placeholder
  - slide: 4
    stage: Solution
    spec_density: full
    title: 自动化对账把三方流水核对从“人找差异”变成“系统报差异”
    job: 给出方案的核心机制
    evidence: 产品机制：自动归集 + 差异标注
    asset_hint: 三步流程图
    visual_hint: 输入-匹配-异常处理
    speaker_note_focus: 一页讲机制，不讲功能清单
    content_spec:
      content_role: explanation
      primary_message: 方案的核心不是替换财务判断，而是让系统先完成差异发现
      on_slide_copy:
        headline: 从“人找差异”到“系统报差异”
        subheadline: 自动归集三方流水，匹配正常项，把异常项交给财务判断
        body_blocks:
          - type: bullets
            text: 归集支付/平台/银行流水；自动匹配正常项；标注异常差异；保留人工复核入口
        footnotes: []
      visual_blueprint:
        primary_visual:
          type: process
          purpose: 解释方案机制，降低黑箱感
          data_refs: []
          asset_refs: [asset-product-flow-diagram]
          annotation: 重点标出“异常项”而非功能按钮
        layout_intent:
          composition: 横向三步流程，最后一步突出财务复核
          hierarchy: 机制结论 > 三步流程 > 异常项解释
          density: medium
      data_requirements:
        metrics: []
        missing_sources: []
      asset_requirements:
        required: []
        optional:
          - asset_refs: [asset-product-diff-screenshot]
            reason: 有产品截图可增强可信度
        fallback: 无截图时使用抽象流程图
      narration:
        talk_time: 2 分钟
        key_talking_points:
          - 先讲流程，不讲菜单
          - 强调财务仍掌握最终判断
      constraints:
        must_include: [人找差异, 系统报差异, 人工复核]
        must_avoid: [功能堆叠, 声称完全无需人工]
        split_if: [如果产品截图需要解释超过 3 个标注点，拆成 demo 页]
        placeholder_policy: honest_placeholder
  - slide: 5
    stage: Solution
    spec_density: compact
    title: 已接入 40+ 支付与平台渠道，接入即用，无需改造现有 ERP
    job: 消除“要不要换系统”的顾虑
    evidence: 渠道清单；与 ERP 并存
    asset_hint: 渠道清单 + 并存架构
    visual_hint: 兼容层示意
    speaker_note_focus: 降低迁移恐惧
    content_spec:
      content_role: proof
      primary_message: 方案可以作为对账层接入，不要求客户替换现有 ERP
      on_slide_copy:
        headline: 接入 40+ 渠道，不改造现有 ERP
        subheadline: 自动化对账作为并行能力层，补足三方流水核对
        body_blocks:
          - type: bullets
            text: 保留现有 ERP；接入支付与平台渠道；对账结果回流财务流程
        footnotes:
          - 渠道能力以当前产品清单为准
      visual_blueprint:
        primary_visual:
          type: diagram
          purpose: 消除系统替换顾虑
          data_refs: [ev-channel-count, ev-current-stack]
          asset_refs: [asset-channel-list, asset-erp-coexist-diagram]
          annotation: 标出“并存”而不是“替换”
        layout_intent:
          composition: 上方渠道输入，中间对账层，下方现有 ERP/财务流程
          hierarchy: 不替换 > 40+ 接入 > 回流流程
          density: medium
      data_requirements:
        metrics:
          - value: 40+
            unit: 渠道
            source_ref: ev-channel-count
        missing_sources: []
      asset_requirements:
        required:
          - asset_refs: [asset-channel-list]
            reason: 证明接入范围
        optional:
          - asset_refs: [asset-erp-coexist-diagram]
            reason: 更清楚解释并存架构
        fallback: 无架构图时用三层信息图
      narration:
        talk_time: 2 分钟
        key_talking_points:
          - 回答“会不会动 ERP”的隐性问题
          - 把实施风险降到最低
      constraints:
        must_include: [无需改造现有 ERP, 40+ 渠道]
        must_avoid: [暗示完全零实施成本, 过度技术化]
        split_if: []
        placeholder_policy: honest_placeholder
  - slide: 6
    stage: Benefit
    spec_density: full
    title: 对账周期 3 天 → 2 小时（试点实测）
    job: 用速度收益给出第一个硬证据
    evidence: 试点客户实测数据
    asset_hint: 3天 vs 2小时 双柱对比
    visual_hint: 对比强烈、数字主导
    speaker_note_focus: 强调“实测”，避免被当成营销话术
    content_spec:
      content_role: proof
      primary_message: 试点客户上线后，对账周期从 3 天压缩到 2 小时
      on_slide_copy:
        headline: 对账周期 3 天 → 2 小时
        subheadline: 试点实测显示，系统自动标注差异后，人工只需处理异常项
        body_blocks:
          - type: callout
            text: 速度收益来自流程改变，不是让财务加班更快核对。
        footnotes:
          - 数据来源：试点客户实测，统计周期待补
      visual_blueprint:
        primary_visual:
          type: before_after
          purpose: 用前后对比证明效率收益
          data_refs: [ev-cycle-time]
          asset_refs: []
          annotation: 重点标注“3 天”与“2 小时”的量级差异
        layout_intent:
          composition: 左侧大数字对比，右侧解释流程变化
          hierarchy: 数字 > 结论句 > 口径脚注
          density: low
      data_requirements:
        metrics:
          - value: 3 天 → 2 小时
            unit: 时间
            source_ref: ev-cycle-time
        missing_sources:
          - 统计周期待补
      asset_requirements:
        required: []
        optional:
          - asset_refs: [asset-product-diff-screenshot]
            reason: 有截图可增强可信度
        fallback: 无截图时使用 before/after 信息图
      narration:
        talk_time: 1.5 分钟
        key_talking_points:
          - 先讲结果，再讲机制
          - 强调“试点实测”
      constraints:
        must_include: [试点实测, 数据来源脚注]
        must_avoid: [表述成所有客户都能保证达到 2 小时]
        split_if: [如果要加入产品截图，则拆成 screenshot walkthrough 页]
        placeholder_policy: honest_placeholder
  - slide: 7
    stage: Benefit
    spec_density: full
    title: 差错率：0.8% → 0.05%，一个数量级
    job: 用质量收益证明风险降低
    evidence: 试点数据
    asset_hint: KPI 数字卡
    visual_hint: 大数字 + 降幅标注
    speaker_note_focus: 解释差错率口径，避免被质疑夸大
    content_spec:
      content_role: proof
      primary_message: 自动化匹配后，试点客户差错率从约 0.8% 降至 0.05%
      on_slide_copy:
        headline: 差错率从 0.8% 降到 0.05%
        subheadline: 风险收益来自异常项前置暴露，而非事后补救
        body_blocks:
          - type: caption
            text: 这是质量与可控性的收益，不只是效率收益。
        footnotes:
          - 0.8% 为客户历史自报；0.05% 为试点期间统计，统计周期待补
      visual_blueprint:
        primary_visual:
          type: kpi_card
          purpose: 强化风险降低的量级
          data_refs: [ev-error-rate]
          asset_refs: []
          annotation: 标注“一个数量级”但不要夸大为零差错
        layout_intent:
          composition: 中心大数字，旁侧放口径和 caveat
          hierarchy: 降幅 > 风险解释 > 口径脚注
          density: low
      data_requirements:
        metrics:
          - value: 0.8% → 0.05%
            unit: 差错率
            source_ref: ev-error-rate
        missing_sources:
          - 试点统计周期待补
      asset_requirements:
        required: []
        optional: []
        fallback: 纯 KPI 卡即可
      narration:
        talk_time: 1.5 分钟
        key_talking_points:
          - 将差错率连接到 CFO 的风险感
          - 主动说明口径限制
      constraints:
        must_include: [客户自报口径, 试点统计口径待补]
        must_avoid: [承诺零差错, 使用绝对化措辞]
        split_if: []
        placeholder_policy: honest_placeholder
  - slide: 8
    stage: Benefit
    spec_density: full
    title: 第一年订阅费由省下的人力成本覆盖
    job: 把收益翻译成 CFO 的语言——钱
    evidence: 18万/年 vs 人力节省（口径待补）
    asset_hint: 简单的回本对比
    visual_hint: 财务感、克制、可信
    speaker_note_focus: 现场询问对方平均人力成本，当场代入测算
    content_spec:
      content_role: proof
      primary_message: 若客户侧人力成本达到测算阈值，第一年订阅费可由节省的人力成本覆盖
      on_slide_copy:
        headline: 第一年订阅费可由节省的人力成本覆盖
        subheadline: 先用客户自己的平均人力成本代入，避免凭空承诺 ROI
        body_blocks:
          - type: callout
            text: 现场填入你们的平均人力成本，我们当场算回本周期。
        footnotes:
          - 订阅费：18 万/年；客户侧人力成本口径待补
      visual_blueprint:
        primary_visual:
          type: table
          purpose: 用三档测算模板呈现 ROI，而非编造固定金额
          data_refs: [ev-roi-subscription, ev-manual-hours]
          asset_refs: [asset-roi-calculator-template]
          annotation: 标出“待客户填入”的变量
        layout_intent:
          composition: 左侧 18 万订阅费，右侧高/中/低三档回本模板
          hierarchy: 回本逻辑 > 变量口径 > 订阅费
          density: medium
      data_requirements:
        metrics:
          - value: 18 万/年
            unit: 订阅费
            source_ref: ev-roi-subscription
        missing_sources:
          - 客户财务团队平均人力成本
      asset_requirements:
        required:
          - asset_refs: [asset-roi-calculator-template]
            reason: 需要现场可替换口径的测算模板
        optional: []
        fallback: 如不能现场测算，保留公式与待补变量，不给固定 ROI
      narration:
        talk_time: 2 分钟
        key_talking_points:
          - 对 CFO 透明说明变量
          - 邀请客户用自己的口径代入
      constraints:
        must_include: [18 万/年, 人力成本待补, 公式口径]
        must_avoid: [编造客户工资, 承诺固定回本周期]
        split_if: [如果用户要求完整财务模型，拆成附录]
        placeholder_policy: honest_placeholder
  - slide: 9
    stage: 证据
    spec_density: full
    title: 某家居电商上线 8 周后，关账提前 2.5 天
    job: 用具名客户案例降低风险感
    evidence: 具名客户案例（已授权）
    asset_hint: 客户 logo + 案例四段式
    visual_hint: 客户案例卡
    speaker_note_focus: 只讲一个具名客户，不展开第二个匿名客户
    content_spec:
      content_role: case
      primary_message: 具名家居电商案例证明，这套方案已在相似复杂度场景中跑通
      on_slide_copy:
        headline: 某家居电商上线 8 周后，关账提前 2.5 天
        subheadline: 从单一业务线切入，先验证对账周期与差错暴露
        body_blocks:
          - type: bullets
            text: 背景：多平台订单；挑战：月底关账慢；方案：自动归集与差异标注；结果：关账提前 2.5 天
        footnotes:
          - 客户具名与 logo 使用已授权；统计口径以案例素材为准
      visual_blueprint:
        primary_visual:
          type: quote_card
          purpose: 用真实案例提供第三方背书
          data_refs: [ev-home-case]
          asset_refs: [asset-customer-logo-home]
          annotation: logo 只作案例识别，不做品牌背书夸大
        layout_intent:
          composition: 左侧客户 logo/行业标签，右侧背景-挑战-方案-结果
          hierarchy: 结果 > 客户身份 > 案例路径
          density: medium
      data_requirements:
        metrics:
          - value: 8 周后关账提前 2.5 天
            unit: 时间
            source_ref: ev-home-case
        missing_sources: []
      asset_requirements:
        required:
          - asset_refs: [asset-customer-logo-home]
            reason: 具名案例页需要授权 logo 或明确匿名替代
        optional:
          - asset_refs: [asset-customer-quote-home]
            reason: 若有客户原话，可增强可信度
        fallback: 如授权撤回，改为“某家居电商”匿名案例并移除 logo
      narration:
        talk_time: 2 分钟
        key_talking_points:
          - 案例只讲一个，不贪多
          - 把案例结果连接到 POC 可验证性
      constraints:
        must_include: [已授权具名, 8 周, 提前 2.5 天]
        must_avoid: [未经授权展示客户信息, 讲第二个匿名案例导致超时]
        split_if: [如果加入第二个案例，拆成附录]
        placeholder_policy: block_until_provided
  - slide: 10
    stage: 行动
    spec_density: full
    title: 建议从一条业务线起步，做 4 周付费 POC
    job: 给出低门槛、可当场答应的下一步
    evidence: POC 范围/周期/交付物
    asset_hint: 4 周时间线
    visual_hint: 清晰、行动导向
    speaker_note_focus: 直接请求决策，给出本周可定的两个时间选项
    content_spec:
      content_role: cta
      primary_message: 最低风险的下一步是用一条业务线做 4 周付费 POC，用客户自己的数据复现收益
      on_slide_copy:
        headline: 从一条业务线起步，4 周验证结果
        subheadline: 不替换系统，先验证周期、差错率和实施成本
        body_blocks:
          - type: cta
            text: 今天确认 POC 范围；本周完成技术对接会；4 周后复盘是否扩大范围。
        footnotes: []
      visual_blueprint:
        primary_visual:
          type: timeline
          purpose: 把决策请求变成低门槛行动
          data_refs: [ev-poc-plan]
          asset_refs: [asset-poc-timeline]
          annotation: 每周一个交付物，避免显得不可控
        layout_intent:
          composition: 四周时间线 + 右侧决策请求
          hierarchy: CTA > 4 周节奏 > 交付物
          density: medium
      data_requirements:
        metrics:
          - value: 4 周
            unit: POC 周期
            source_ref: ev-poc-plan
        missing_sources: []
      asset_requirements:
        required: []
        optional:
          - asset_refs: [asset-poc-timeline]
            reason: 时间线可以由下游生成
        fallback: 用纯文本时间线
      narration:
        talk_time: 1 分钟
        key_talking_points:
          - 直接请求确认 POC
          - 给出本周可定的两个时间选项
      constraints:
        must_include: [4 周, 单一业务线, 付费 POC, 本周下一步]
        must_avoid: [模糊的“后续沟通”, 没有负责人/时间]
        split_if: []
        placeholder_policy: honest_placeholder
  - slide: 11
    stage: 收尾
    spec_density: compact
    title: 不是要你换掉财务团队，是把他们从对账里解放出来
    job: 金句收尾，呼应开场钩子
    evidence: 呼应 slide 1 的时间成本与 slide 10 的 POC
    asset_hint: 金句页
    visual_hint: 留白、强记忆点
    speaker_note_focus: 结尾只留一句话和一个行动
    content_spec:
      content_role: transition
      primary_message: 这套方案的价值是把财务从重复核对中释放出来，回到分析和风控判断
      on_slide_copy:
        headline: 不是替换财务团队，是把他们从对账里解放出来
        subheadline: 下一步，用一条业务线验证这件事是否也能发生在你们的数据里
        body_blocks:
          - type: cta
            text: 我们建议今天确认 POC 范围和技术对接时间。
        footnotes: []
      visual_blueprint:
        primary_visual:
          type: none
          purpose: 让收尾句成为唯一记忆点
          data_refs: []
          asset_refs: []
          annotation: 不需要装饰图，避免削弱金句
        layout_intent:
          composition: 中央大句 + 底部小 CTA
          hierarchy: 金句 > 下一步
          density: low
      data_requirements:
        metrics: []
        missing_sources: []
      asset_requirements:
        required: []
        optional: []
        fallback: 不使用图片
      narration:
        talk_time: 30 秒
        key_talking_points:
          - 呼应开场的 3 个人日
          - 停顿后转向 Q&A 或决策确认
      constraints:
        must_include: [金句, POC 下一步]
        must_avoid: [谢谢聆听页, 新增未讲过的信息]
        split_if: []
        placeholder_policy: honest_placeholder
  - slide: 12
    stage: 附录
    spec_density: compact
    title: 安全、权限与数据合规说明
    job: 预置高风险 Q&A 的兜底页
    evidence: 合规要点
    asset_hint: 安全控制清单
    visual_hint: 表格或控制矩阵
    speaker_note_focus: 仅在被问到时翻出
    content_spec:
      content_role: appendix
      primary_message: 财务流水敏感数据可通过权限、审计和数据范围控制降低实施风险
      on_slide_copy:
        headline: 安全、权限与数据范围可以在 POC 前置约定
        subheadline: 先限定业务线、账号范围、访问权限和审计留痕
        body_blocks:
          - type: bullets
            text: 最小权限；操作留痕；数据范围限定；POC 结束后的数据处理约定
        footnotes:
          - 具体合规条款以双方安全评审与合同为准
      visual_blueprint:
        primary_visual:
          type: table
          purpose: 回答 CFO/IT 对财务数据安全的高风险问题
          data_refs: [ev-security-controls]
          asset_refs: [asset-security-checklist]
          annotation: 按“风险-控制-POC 约定”三列呈现
        layout_intent:
          composition: 三列表格，保留足够可读空间
          hierarchy: 风险点 > 控制措施 > POC 约定
          density: high
      data_requirements:
        metrics: []
        missing_sources:
          - 具体安全认证或合规资质待补
      asset_requirements:
        required:
          - asset_refs: [asset-security-checklist]
            reason: 安全问答页需要真实控制清单或诚实待补
        optional: []
        fallback: 若缺安全材料，标“安全资料待补”，不要编造认证
      narration:
        talk_time: Q&A 按需使用
        key_talking_points:
          - 只在被问到时打开
          - 不承诺未确认的认证或合规条款
      constraints:
        must_include: [最小权限, 审计留痕, 数据范围限定]
        must_avoid: [编造安全认证, 主流程中主动展开过久]
        split_if: [如果客户 IT 在场并要求细节，拆成单独安全附录]
        placeholder_policy: honest_placeholder
evidence_plan:
  - id: ev-manual-hours
    claim_or_metric: 财务每周约 6 小时手工核对，折算每月约 3 个人日
    source: 客户痛点访谈
    source_status: user_reported
    comparison_baseline: 当前人工核对投入
    recommended_chart: kpi_card
    caveat: 为访谈估算，不是审计值
  - id: ev-close-cycle
    claim_or_metric: 月底关账平均 3 天
    source: 客户访谈
    source_status: user_reported
    comparison_baseline: 自动化后试点对账周期
    recommended_chart: before_after
    caveat: 需确认是否为全部业务线平均
  - id: ev-current-stack
    claim_or_metric: 客户当前使用 Excel + 老 ERP 模块
    source: 销售素材
    source_status: user_reported
    comparison_baseline: 自动化对账层
    recommended_chart: diagram
    caveat: 不得贬低现有系统
  - id: ev-channel-count
    claim_or_metric: 已接入 40+ 支付与平台渠道
    source: 产品事实
    source_status: verified
    comparison_baseline: 现状 Excel+ERP 不支持多渠道自动归集
    recommended_chart: logo_wall / diagram
    caveat: 列“40+”，勿逐一夸大具体渠道名
  - id: ev-cycle-time
    claim_or_metric: 对账周期 3 天 → 2 小时
    source: 试点客户实测（家居电商）
    source_status: user_reported
    comparison_baseline: 客户现状关账 3 天
    recommended_chart: 双柱对比
    caveat: 单一试点，需说明样本；勿表述为“所有客户”
  - id: ev-error-rate
    claim_or_metric: 差错率 0.8% → 0.05%
    source: 试点实测
    source_status: user_reported
    comparison_baseline: 手工对账历史差错率
    recommended_chart: KPI 数字卡 + 降幅标注
    caveat: 0.8% 为客户自报，标注来源
  - id: ev-roi-subscription
    claim_or_metric: 第一年 ROI 回本
    source: 待补——依赖客户侧人力成本
    source_status: to_verify
    comparison_baseline: 18 万/年订阅费
    recommended_chart: 回本对比
    caveat: 口径待补，现场用客户自报数据测算，brief 内不得编造具体金额
  - id: ev-home-case
    claim_or_metric: 某家居电商上线 8 周后，关账提前 2.5 天
    source: 具名客户案例（已授权）
    source_status: user_reported
    comparison_baseline: 上线前关账周期
    recommended_chart: quote_card / case card
    caveat: 仅代表该客户案例
  - id: ev-poc-plan
    claim_or_metric: 4 周、单一业务线付费 POC
    source: 销售建议方案
    source_status: assumed
    comparison_baseline: 全量替换系统
    recommended_chart: timeline
    caveat: POC 范围需客户确认
  - id: ev-security-controls
    claim_or_metric: 权限、审计、数据范围控制
    source: 待补安全资料
    source_status: to_verify
    comparison_baseline: 财务流水敏感数据风险
    recommended_chart: table
    caveat: 不得编造认证或合规条款
speaker_plan:
  qa_risks:
    - 数据安全与权限：财务流水高度敏感 → 用附录页（slide 12）正面回应
    - ROI 是否成立：准备“按你们的人力成本现场算”的话术，而非给死数字
    - 试点样本太少：坦诚是早期客户，给出可验证的 POC 作为对冲
    - 与现有 ERP 冲突：强调并存、不改造
  timing: 讲 15 分钟 + Q&A 5 分钟；钩子+Problem 控制在 5 分钟内
visual_intent:
  tone: 专业、克制、可信（财务受众，避免炫技与浮夸营销感）
  density: 中低——每页一个观点，数字主导
  rhythm: 钩子页强、Problem 收紧、Benefit 页用对比制造峰值、收尾留白
  readability: 大字号、强对比；关键数字必须一眼可读
asset_plan:
  catalog:
    - id: asset-brand-logo-vendor
      type: logo
      status: to_fetch
      source: 我方品牌资产待提供
      rights_or_permission: 待补
      used_on: [1, 11]
      fallback: 无品牌资产时使用文字品牌占位
    - id: asset-channel-list
      type: chart_data
      status: provided
      source: 产品渠道清单
      rights_or_permission: 内部产品事实，可用于销售提案
      used_on: [3, 5]
      fallback: 改为渠道类型分组，不展示具体 logo
    - id: asset-product-flow-diagram
      type: icon
      status: to_generate
      source: 根据产品机制生成流程图
      rights_or_permission: 自生成
      used_on: [4]
      fallback: 纯文字三步流程
    - id: asset-product-diff-screenshot
      type: screenshot
      status: placeholder
      source: 产品差异标注截图待补
      rights_or_permission: 待确认是否可对外展示
      used_on: [4, 6]
      fallback: 用抽象流程图或 before/after 信息图替代
    - id: asset-erp-coexist-diagram
      type: icon
      status: to_generate
      source: 根据并存架构生成示意图
      rights_or_permission: 自生成
      used_on: [5]
      fallback: 用三层文字信息图
    - id: asset-roi-calculator-template
      type: chart_data
      status: placeholder
      source: ROI 三档测算模板待补客户人力成本
      rights_or_permission: 内部测算模板
      used_on: [8]
      fallback: 只展示公式和待补变量，不给固定回本金额
    - id: asset-customer-logo-home
      type: logo
      status: provided
      source: 家居电商授权素材
      rights_or_permission: 已授权具名用于销售提案
      used_on: [9]
      fallback: 授权撤回时改为匿名案例并移除 logo
    - id: asset-customer-quote-home
      type: document
      status: placeholder
      source: 客户原话待补
      rights_or_permission: 待授权
      used_on: [9]
      fallback: 不展示 quote，只展示案例事实
    - id: asset-poc-timeline
      type: icon
      status: to_generate
      source: 根据 POC 计划生成时间线
      rights_or_permission: 自生成
      used_on: [10]
      fallback: 纯文本四周计划
    - id: asset-security-checklist
      type: document
      status: placeholder
      source: 安全、权限、合规资料待补
      rights_or_permission: 待补
      used_on: [12]
      fallback: 标注“安全资料待补”，不编造认证
  have: [具名家居客户 logo 与案例数据, 渠道清单, 试点实测数据]
  todo: [美妆客户具名授权（待补）, 客户侧人力成本口径（待补）, 我方品牌 logo 矢量]
constraints:
  language: 中文
  duration: 20 分钟（含 Q&A）
  slide_count: 12（含 1 页附录）
  editability: 需可改——销售会按不同客户替换数字与 logo
  portability: 现场投屏为主；导出 PDF 备用
  brand_assets: 待提供我方 VI；客户 logo 仅用于案例页
must_keep:
  - 第 1 页的痛点钩子与第 11 页的呼应金句
  - 所有收益数字标注“试点实测”来源
  - 明确的 POC CTA
must_avoid:
  - 功能罗列式目录页
  - 贬低客户现有方案的措辞
  - 任何编造的 ROI 金额或客户名
references_consulted:
  - scenario-playbooks.md
  - narrative-frameworks.md
  - data-viz-guide.md
  - content-spec-guide.md
  - speaker-notes-template.md
  - downstream-adapter-protocol.md
  - presentation-checklist.md
open_questions:
  - 美妆试点客户能否具名？（影响 slide 9 是否放第二个案例）
  - 客户财务团队平均人力成本？（影响 slide 8 ROI 测算口径）
  - 是否有我方现成 VI/品牌色，还是交由下游探索？
```

---

## Adapter-specific Appendix — `huashu-design`

> 本附录通过运行时读取 `huashu-design` 的 `SKILL.md` 后翻译生成，使用其真实词汇（design spec / 品牌资产协议 / 三方向视觉探索）。字段以届时读到的版本为准。

- **请求模式**：用户无明确视觉风格 → 触发其「设计方向顾问」，做**三方向视觉探索**。
- **design spec**：
  - 目标受众：客户方财务高管（VP/CFO），偏好可信、克制、信息清晰。
  - 核心信息：手工三方对账成本高且有风险；本方案可验证地降本控险；下一步是低门槛 POC。
  - 情感基调：专业、稳重、值得托付（财务数据敏感），**反 AI slop**，避免通用 SaaS 紫渐变 trope。
  - 输出尺寸：16:9 横版幻灯片，12 页；现场投屏 + PDF 导出。
- **三方向锚点**（差异化探索）：
  1. **保守专业版**：接近金融机构质感，深色克制配色，强调可信与合规——契合 CFO。
  2. **强叙事版**：以痛点—收益的对比节奏驱动版式，数字做视觉峰值，叙事感强。
  3. **视觉冲击版**：大数字 + 大留白的极简冲击，钩子页与收益页拉满张力。
- **品牌资产协议**：我方 VI 待补（标 `待补`，勿臆造品牌色）；客户 logo 仅限案例页（slide 9），需确认授权范围。
- **交互/动效**：以静态高保真为主；如需动效，仅在收益对比页用克制的数字增长动画，避免削弱可信感。
- **不替下游决定**：最终配色、字体、版式由 huashu-design 在三方向探索中产出；本 brief 只给约束与锚点。

---

## 交付前自检（最弱环）

> 不逐项打勾——12 问只作扫描，输出落到"这份 brief 最可能在哪翻车 + 怎么救"。

**最可能翻车处 1：slide 8 的 ROI 页（口径待补）。** 对 CFO 这是决策支点，却恰恰是唯一没数的页——现场若算不出可信回本，整条"收益"叙事会塌。
→ 修复：会前向销售要到该客户财务团队人力成本区间，brief 内先给"高/中/低"三档测算模板占位；现场用对方自报数代入，而非临时心算。

**最可能翻车处 2：收益证据全部来自单一试点（slide 6–7）。** 财务高管会立刻质疑样本量，"3 天→2 小时"可能被当成孤例营销话术。
→ 修复：所有收益数字显式标"试点实测、单客户"，并把 slide 10 的 POC 重新定位成"用你们自己的数据复现这个结果"的对冲，把样本风险转成行动理由。

**扫描通过项（简列）**：钩子（slide 1）、结论式标题链、骨架可一句话说清、CTA 明确（slide 10）、Q&A 四类高风险已备、页数/时长匹配、未编造（待补项均入 open_questions）。

**未解决但不编造**：美妆客户具名、ROI 客户侧口径、我方 VI——均已在 `open_questions` 标 `待补`。

---

# 样例 B：lite 档（内部周会，5 分钟）

## 0. 模拟输入（用户给的原始材料）

> 用户消息："帮我做个团队周会 PPT，周三站会用，5 分钟过一下我们组这周进展，别搞太复杂。"
>
> 附带素材（节选）：本周上线了对账模块灰度；订单同步延迟 bug 修复；下周要联调支付回调；卡在等 DBA 加索引（已等 3 天）。

**Skill 的推断**：场景=内部周会；听众=本组同事+组长；目标动作=同步进度、暴露阻塞、要到 DBA 支持；时长=5 分钟；语言=中文；下游未指定。
**tier 判定**：`lite`（内部周会、<10 分钟、低风险）——不产 evidence/speaker/Q&A 满配结构。

---

## Direction Snapshot + Timing Brief（确认点）

**Direction Snapshot**
- 场景：内部周会 / 站会。
- 听众：本组同事 + 组长。
- 目标动作：同步进度，并让组长当天协调 DBA 加索引。
- 成功标准：会后阻塞项有明确负责人和完成时间。
- brief 档位：`lite`，因为这是 5 分钟内部同步。
- 推荐叙事骨架：状态 → 阻塞 → 需要支持。
- 待补：无。

**Timing Brief**
- 总时长预估：5 分钟。
- 正式讲述 / Q&A：讲述 4 分钟，留 1 分钟确认支持动作。
- 建议页数：5 页。
- 可压缩版本：若只有 2 分钟，保留“本周已完成、唯一阻塞、需要支持”三页。
- 超时风险：在已完成事项上展开太多，会稀释 DBA 阻塞的紧迫性。

**确认问题**：我会按这个方向和时长生成 lite brief。方向/时长对吗？要改听众、目标、时长，还是直接继续？

> 模拟用户确认：“继续。”

---

## 摘要（人读）

- **一句话主张**：本周交付按计划推进，唯一风险是 DBA 加索引已阻塞 3 天，需组长当场协调。
- **听众听完应记住**：进度正常，但有一个需要立刻拉通的外部阻塞。
- **听众听完应做**：组长今天指派或催办 DBA 加索引。
- **推荐叙事骨架**：状态 → 阻塞 → 需要支持。理由：站会就该 5 分钟讲完，骨架越轻越好。
- **推荐时长策略**：5 分钟内讲完，4 分钟同步 + 1 分钟确认支持动作。
- **状态**：信息完整。

## Timing Brief（时长策略）

- **总时长预估**：5 分钟。
- **正式讲述 / Q&A**：4 分钟讲述 + 1 分钟确认支持动作。
- **建议页数**：5 页。
- **可压缩版本**：2 分钟版本保留“本周已完成、唯一阻塞、需要支持”三页。
- **超时风险**：已完成事项讲太细会削弱阻塞页的优先级。

## Slide Title Chain

| 页码 | 叙事阶段 | 结论式标题 | 本页作用 | 备注 |
| --- | --- | --- | --- | --- |
| 1 | 状态 | 对账模块本周已进入灰度，按计划推进 | 开场给确定性 | 一句带过，不展开 |
| 2 | 状态 | 订单同步延迟 bug 已修复并验证 | 第二个已完成项 | —— |
| 3 | 进行中 | 下周主线是支付回调联调 | 给出下周焦点 | —— |
| 4 | 阻塞 | DBA 加索引已等 3 天，正卡住灰度放量 | 暴露唯一真阻塞 | 本页是重点 |
| 5 | 需要支持 | 请组长今天协调 DBA，本周内完成加索引 | 明确 ask | CTA 具体、可当场答应 |

## Handoff Contract（精简）

```yaml
brief_tier: lite
run_mode: interactive
output_language: zh
handoff_mode: universal_only
adapter_resolution:
  requested: none
  resolved: none
  status: none
deck_intent:
  scenario: 内部周会 / 站会
  audience: 本组同事 + 组长
  desired_action: 组长当天协调 DBA 加索引
constraints:
  language: 中文
  duration: 5 分钟
  slide_count: 5
runtime_plan:
  total_duration: 5 分钟
  talk_time: 4 分钟
  qa_time: 1 分钟（确认支持动作）
  slide_count_target: 5
  cut_if_short_on_time: [2, 3]
slide_plan:
  - slide: 4
    title: DBA 加索引已等 3 天，正卡住灰度放量
    job: 暴露唯一真阻塞并制造协调必要性
    content_spec:
      primary_message: 如果索引本周不完成，灰度放量和支付回调联调都会顺延
      on_slide_copy:
        headline: DBA 加索引已阻塞 3 天
        body_blocks:
          - 加索引未完成 → 灰度放量推迟到下周
          - 支付回调联调会跟着顺延
      primary_visual:
        type: timeline
        data_refs: []
        asset_refs: []
      split_if: []
  - slide: 5
    title: 请组长今天协调 DBA，本周内完成加索引
    job: 明确 ask
    content_spec:
      primary_message: 今天需要明确 DBA 负责人和完成时间
      on_slide_copy:
        headline: 今天需要一个明确协调动作
        body_blocks:
          - 请组长协调 DBA owner
          - 本周内完成索引并恢复灰度放量
      primary_visual:
        type: none
        data_refs: []
        asset_refs: []
      split_if: []
references_consulted:
  - scenario-playbooks.md
  - presentation-checklist.md
open_questions: []
```

## 交付前自检（最弱环）

**最可能翻车处：slide 4 的阻塞若只说"在等 DBA"而不给影响面，会被当成例行汇报、催不动。**
→ 修复：把阻塞量化成后果——"加索引不完成，灰度放量推迟到下周、支付联调跟着顺延"，让 ask 有紧迫性。
