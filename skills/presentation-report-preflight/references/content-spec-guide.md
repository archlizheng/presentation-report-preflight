# Page Content Spec Guide（content-spec-guide.md）

> 用途：供 `presentation-report-preflight` 为每一页生成可执行的内容蓝图。它控制页面信息结构、上屏文案、图表/信息图、图片素材、数据引用、素材兜底、讲述重点和拆页条件；不控制最终字体、精确版式、动画或 DOM。

---

## 目录

- [一、原则](#一原则)
- [二、full 档 schema](#二full-档-schema)
- [三、lite 档精简 schema](#三lite-档精简-schema)
- [四、字段说明](#四字段说明)
- [五、视觉类型 taxonomy](#五视觉类型-taxonomy)
- [六、引用规则](#六引用规则)
- [七、常用页面模式](#七常用页面模式)
- [八、示例](#八示例)
- [九、自检清单](#九自检清单)

## 一、原则

1. **Content before layout**：先定义页面要表达什么、需要什么证据、出现什么素材，再让下游 skill 选择版式。
2. **Executable, not decorative**：`content_spec` 必须足够让下游生成页面，不需要重新发明文案、图表或素材。
3. **One message per slide**：`primary_message` 是本页唯一主张；如果有两个主张，拆页。
4. **Copy is constrained**：写上屏文案的要点和可直接使用的短句，不写大段讲稿。
5. **Evidence is traceable**：所有图表、指标、客户案例和 ROI 都通过 `data_refs` 引用 `evidence_plan[].id`；每条证据带 `source_status`（`verified | user_reported | assumed | to_verify`），`assumed/to_verify` 必须落到本页 `footnotes` 并进入最弱环候选。
6. **Assets are honest**：所有 logo、截图、图片、视频、数据文件都通过 `asset_refs` 引用 `asset_plan.catalog[].id`；未知就标 `TBD/待补`。
7. **Downstream freedom is visual**：下游可以改版式、风格、动效、组件名，但不能改主张、数据值、来源、限制和必需素材。

## 二、full 档 schema

> 父级 `slide_plan` item 带 `spec_density: full | compact`。`full` 用下面完整 schema；`compact` 用第三节精简 schema。核心页（hook/proof/case/cta、带关键数字或必需素材的页）用 full，其余 compact；deck >20 页默认混合。

每个 `slide_plan` item 必须包含完整 `content_spec`：

```yaml
content_spec:
  content_role: hook | setup | proof | explanation | comparison | case | demo | transition | cta | appendix
  primary_message: TBD
  on_slide_copy:
    headline: TBD
    subheadline: TBD
    body_blocks:
      - type: paragraph | bullets | callout | quote | caption | cta
        text: TBD
    footnotes: []
  visual_blueprint:
    primary_visual:
      type: kpi_card | before_after | bar_chart | line_chart | timeline | process | matrix | diagram | table | image_hero | screenshot_walkthrough | logo_wall | quote_card | none
      purpose: TBD
      data_refs: []
      asset_refs: []
      annotation: TBD
    layout_intent:
      composition: TBD
      hierarchy: TBD
      density: low | medium | high
  data_requirements:
    metrics: []
    missing_sources: []
  asset_requirements:
    required: []
    optional: []
    fallback: TBD
  narration:
    talk_time: TBD
    key_talking_points: []
  constraints:
    must_include: []
    must_avoid: []
    split_if: []
    placeholder_policy: honest_placeholder | block_until_provided
```

## 三、lite 档精简 schema

Lite 档不要输出完整蓝图。只有当页面需要防止下游跑偏、包含关键数字、需要素材、或有拆页风险时，加入精简 `content_spec`：

```yaml
content_spec:
  primary_message: TBD
  on_slide_copy:
    headline: TBD
    body_blocks: []
  primary_visual:
    type: kpi_card | before_after | timeline | process | table | none
    data_refs: []
    asset_refs: []
  split_if: []
```

## 四、字段说明

| 字段 | 作用 | 写法 |
| --- | --- | --- |
| `content_role` | 本页在叙事中的内容角色 | 用枚举值，不要自造同义词 |
| `primary_message` | 本页不可变主张 | 一句话，能独立读懂 |
| `on_slide_copy.headline` | 上屏主标题 | 应与结论式标题一致或更短 |
| `subheadline` | 标题下的解释句 | 可为空，但不要重复标题 |
| `body_blocks` | 页面正文模块 | 控制数量；每块只服务主张 |
| `footnotes` | 数据来源/口径/限制 | 数据页必须有，未知标待补 |
| `primary_visual.type` | 主视觉类型 | 从 taxonomy 选 |
| `purpose` | 主视觉为什么存在 | 例如“证明效率收益” |
| `data_refs` | 引用证据 ID | 必须匹配 `evidence_plan[].id` |
| `asset_refs` | 引用素材 ID | 必须匹配 `asset_plan.catalog[].id` |
| `annotation` | 图表/图片旁的解释 | 说明该看哪里，不写废话 |
| `composition` | 构图意图 | 例如“左侧大数字，右侧三步解释” |
| `hierarchy` | 信息层级 | 例如“数字 > 对比基准 > 来源” |
| `density` | 内容密度 | `low/medium/high` |
| `metrics` | 页面需要的指标 | 含值、单位、口径；未知标待补 |
| `missing_sources` | 缺失来源 | 不得用猜测填充 |
| `required` | 没有就会影响页面成立的素材 | 如客户 logo、产品截图、CSV |
| `optional` | 有会更好，没有可兜底的素材 | 如辅助照片、背景图 |
| `fallback` | 素材缺失时怎么办 | 如“用流程图替代截图” |
| `talk_time` | 本页预计讲述时长 | 与 `runtime_plan` 对齐 |
| `key_talking_points` | 讲述重点 | 2-4 条，不写逐字稿 |
| `must_include` | 下游必须保留 | 数据、注释、CTA、授权提示等 |
| `must_avoid` | 下游必须避免 | 编造、过度承诺、装饰图等 |
| `split_if` | 拆页条件 | 如“正文超过 5 bullets” |
| `placeholder_policy` | 占位策略 | `honest_placeholder` 或 `block_until_provided` |

## 五、视觉类型 taxonomy

| 类型 | 用途 | 必备信息 |
| --- | --- | --- |
| `kpi_card` | 强调一个关键数字 | 指标、单位、来源、对比基准 |
| `before_after` | 前后变化 | before、after、变化幅度、统计口径 |
| `bar_chart` | 类别对比 | 类别、数值、单位、排序逻辑 |
| `line_chart` | 趋势变化 | 时间范围、指标、单位、数据源 |
| `timeline` | 里程碑/实施计划 | 时间点、阶段、责任/交付物 |
| `process` | 流程/机制 | 步骤、输入、输出、关键差异 |
| `matrix` | 维度对比/优先级 | 行列维度、判断标准 |
| `diagram` | 系统/架构/关系 | 节点、关系、方向 |
| `table` | 严肃对比/清单 | 列名、行项、排序或分组 |
| `image_hero` | 情绪/场景/产品实物 | 图片来源、授权、裁切意图 |
| `screenshot_walkthrough` | 产品演示 | 截图、标注点、用户路径 |
| `logo_wall` | 渠道/客户/生态背书 | logo 清单、授权/使用范围 |
| `quote_card` | 客户/用户/专家原话 | 原话、归属、是否脱敏 |
| `none` | 文字/过渡/收尾页 | 说明为什么不需要主视觉 |

## 六、引用规则

`evidence_plan` 必须使用稳定 ID：

```yaml
evidence_plan:
  - id: ev-cycle-time
    claim_or_metric: 对账周期 3 天 → 2 小时
    source: 试点客户实测
    source_status: user_reported # verified | user_reported | assumed | to_verify
    comparison_baseline: 客户现状关账 3 天
    recommended_chart: before_after
    caveat: 单一试点，不能表述为所有客户
```

`asset_plan` 必须有 `catalog`：

```yaml
asset_plan:
  catalog:
    - id: asset-customer-logo-home
      type: logo
      status: provided
      source: 客户授权素材包
      rights_or_permission: 已授权具名用于销售提案
      used_on: [9]
      fallback: 如授权撤回，改为“某家居电商”匿名案例
```

引用规则：
- `data_refs` 只能引用 `evidence_plan[].id`。
- `asset_refs` 只能引用 `asset_plan.catalog[].id`。
- 暂无素材但页面可继续：建一个 `status: placeholder` 或 `to_fetch` 的 asset，并写 fallback。
- 没有素材页面就不成立：`placeholder_policy: block_until_provided`，并加入 `open_questions`。

## 七、常用页面模式

### 钩子页

- `content_role: hook`
- 主视觉通常为 `kpi_card` / `image_hero` / `quote_card`
- 只保留一个强句或一个强数字
- `talk_time` 控制在 30 秒-1 分钟

### 证据页

- `content_role: proof`
- 主视觉通常为 `before_after` / `bar_chart` / `kpi_card`
- 必须有来源、对比基准、口径、限制
- `must_avoid` 写清楚不能过度承诺

### 案例页

- `content_role: case`
- 需要客户名/脱敏名、背景、挑战、方案、结果
- logo 或客户照片必须走 `asset_refs`
- 未授权时写匿名 fallback

### 方案解释页

- `content_role: explanation`
- 主视觉通常为 `process` / `diagram` / `screenshot_walkthrough`
- 写清输入、动作、输出；不要堆功能列表

### CTA 页

- `content_role: cta`
- `on_slide_copy.body_blocks` 应包含具体下一步、时间、责任人或决策请求
- `must_include` 必须写行动请求

## 八、示例

```yaml
slide: 6
stage: Benefit
title: 对账周期 3 天 → 2 小时（试点实测）
job: 用速度收益给出第一个硬证据
evidence: 试点客户实测数据
asset_hint: 3 天 vs 2 小时 before/after
visual_hint: 对比强烈、数字主导
speaker_note_focus: 强调这是试点实测，不是营销承诺
content_spec:
  content_role: proof
  primary_message: 试点客户上线后，对账周期从 3 天压缩到 2 小时
  on_slide_copy:
    headline: 对账周期 3 天 → 2 小时
    subheadline: 试点实测显示，系统自动标注差异后，人工只需处理异常项
    body_blocks:
      - type: callout
        text: “速度收益来自流程改变，不是让财务加班更快核对。”
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
      - 强调“实测”与“异常项处理”
  constraints:
    must_include:
      - 试点实测
      - 数据来源脚注
    must_avoid:
      - 表述成所有客户都能保证达到 2 小时
    split_if:
      - 如果要加入产品截图，则拆成截图 walkthrough 页
    placeholder_policy: honest_placeholder
```

## 九、自检清单

输出前检查：

- [ ] full 档每个 `slide_plan` item 都有完整 `content_spec`。
- [ ] 每页都标了 `spec_density`（full/compact）；核心页 full，常规页 compact；>20 页采用混合档。
- [ ] lite 档只在必要页面加入精简 `content_spec`。
- [ ] 每页只有一个 `primary_message`。
- [ ] 每个图表/数字都通过 `data_refs` 指向 `evidence_plan[].id`。
- [ ] 每条证据都带 `source_status`；`assumed/to_verify` 已落到 `footnotes` 且进入最弱环候选。
- [ ] 每个 logo/截图/图片都通过 `asset_refs` 指向 `asset_plan.catalog[].id`。
- [ ] 未知素材、来源、授权、截图和 ROI 都标 `TBD/待补`，没有编造。
- [ ] 下游 skill 能仅凭 `content_spec` 做出每页，不需要重新发明文案、图表或素材。
