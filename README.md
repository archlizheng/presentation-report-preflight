# Presentation Report Preflight（汇报型演示前置策划 Skill）

> 在任何 PPT/HTML 生成动作之前，先把"这场汇报到底要怎么打"想清楚。
>
> 这是一个**上游策划 Skill**：它不画 PPT，而是把一个主题、一份源文档、一份旧 deck、一个 PDF、一堆数据或笔记，转成一份结构化、可交接的 **Presentation Strategy Brief（演示策略简报）**，再交给下游的幻灯片生成 skill 执行。

> 🇬🇧 English version: [README.en.md](./README.en.md)

---

## 安装

本仓库根目录即一个标准 skill（含 `SKILL.md`），可用开源的 [`skills` CLI](https://github.com/vercel-labs/skills)（支持 Claude Code、Codex、Cursor、OpenCode 等）一键安装：

```bash
# 安装到当前项目
npx skills add archlizheng/presentation-report-preflight

# 安装到用户级（全局，跨项目可用）
npx skills add archlizheng/presentation-report-preflight -g

# 只装给指定 agent（如 Codex / Claude Code）
npx skills add archlizheng/presentation-report-preflight -a codex
npx skills add archlizheng/presentation-report-preflight -a claude-code
```

安装后，CLI 会自动检测 skill、拷贝文件到对应 agent 的 skills 目录，无需手动配置。常用管理命令：

```bash
npx skills list          # 查看已安装的 skill
npx skills update         # 更新全部 skill
npx skills remove presentation-report-preflight   # 卸载
```

> 也可以直接 `git clone` 本仓库，把整个目录放进你的 skills 目录（如 `~/.codex/skills/` 或 `~/.claude/skills/`）。

---

## 它解决什么问题

大多数"AI 做 PPT"的失败，不在于不好看，而在于**没想清楚就开始排版**：

- 听众是谁、要他们做什么、成功标准是什么——没定义就开做；
- 每页标题是"主题"而不是"结论"，连起来读不成一个故事；
- 数字没有来源、没有对比基准，甚至是编造的；
- 时长没规划，现场要么讲不完要么没东西讲；
- 直接丢给下游生成 skill，下游只能自己瞎猜文案、图表和素材。

本 Skill 把这些**前置决策**固化成一份简报：场景、听众、目标、叙事骨架、时长策略、结论式标题链、逐页内容蓝图（content_spec）、证据计划、演讲者备注、Q&A 风险、视觉意图、约束，以及一份**通用交接契约（Universal Handoff Contract）**。任何合格的幻灯片生成 skill 都能直接据此执行。

---

## 核心特性

| 能力 | 说明 |
| --- | --- |
| **先方向后内容** | 先定场景/听众/目标/时长，再谈版式；先定叙事骨架，再排页。 |
| **结论式标题链** | 每页标题是一句可独立读懂的结论，连起来就是全篇摘要。 |
| **逐页 content_spec** | 每页给出主张、上屏文案、视觉蓝图、数据/素材引用、讲述要点，下游无需再发明内容。 |
| **分档输出（lite/full）** | 5 分钟站会用精简档，融资路演/晋升答辩用完整档，按"汇报权重"匹配深度。 |
| **逐页密度（spec_density）** | 在 lite/full 之外再加一轴：核心页 `full`、常规页 `compact`，长 deck 不会把契约撑爆。 |
| **来源状态（source_status）** | 每条证据标 `verified / user_reported / assumed / to_verify`——绝不把自报/推算数字伪装成已验证。 |
| **运行时下游解析** | 下游 skill 名只是示例，运行时实际匹配可用 skill；找不到就降级为通用契约，绝不猜私有字段。 |
| **运行模式（run_mode）** | `interactive` 保留确认门；`autonomous`（headless / 被其它 skill 调用）跳过确认、记录假设，不阻塞。 |
| **语言解耦** | 契约 YAML key 恒为英文（机器稳定），人读层随 `output_language` 切换。 |
| **可校验契约** | 提供 JSON Schema，契约结构与枚举值可被机器实际校验，而非"散文级约定"。 |
| **最弱环自检** | 不输出"12 项全绿"，而是指认 1–2 个最可能现场翻车的薄弱点 + 具体修复动作。 |

---

## 目录结构

```
presentation-report-preflight/
├── SKILL.md                              # 主入口：规则、工作流、输出格式
├── agents/
│   └── openai.yaml                       # 接口元信息（显示名、默认提示词）
└── references/
    ├── scenario-playbooks.md             # 12 类汇报场景的打法、结构、禁忌
    ├── narrative-frameworks.md           # 13 种叙事骨架 + 选型决策树
    ├── data-viz-guide.md                 # 图表选型、数字故事、配色规范
    ├── content-spec-guide.md             # 逐页内容蓝图 schema 与写法
    ├── speaker-notes-template.md         # 演讲者备注 / 节奏 / Q&A 模板
    ├── presentation-checklist.md         # 交付前自检（自检的单一事实源 SSOT）
    ├── downstream-adapter-protocol.md    # 下游 skill 运行时解析与降级协议
    ├── handoff-contract.schema.json      # 通用交接契约的机器可校验 JSON Schema
    └── example-brief.md                  # 端到端范例（full + lite 两份，回归基准）
```

> `references/` 按需加载——SKILL.md 里的"Reference routing"表会指明当前任务该读哪几份，不必一次性全读。

---

## 工作流概览

```
Phase 0  识别输入 / run_mode / 下游目标 / 输出语言 / 分档
Phase 1  无审讯式信息推断（能推断的不问，缺关键项才批量问一次）
Phase 2  载入场景剧本（scenario-playbooks）
Phase 3  选定叙事骨架（narrative-frameworks）
Phase 3.5 方向 + 时长确认门（interactive 模式生效）
Phase 4  生成结论式标题链
Phase 4.5 标题链确认门（两拍交付）
Phase 4.7 逐页 content_spec（content-spec-guide）
Phase 5  数据与证据计划（含 source_status）
Phase 6  演讲者备注与 Q&A（speaker-notes-template）
Phase 7  下游交接（通用契约 + 运行时解析的 adapter 附录）
Phase 8  交付前自检（指认最弱环 + schema 校验）
```

---

## 输出物：Presentation Strategy Brief

一份 `presentation-strategy-brief.md`，结构为：

1. **摘要（人读）**——一句话主张、听众应记住/应做、推荐骨架、时长策略、状态。
2. **Timing Brief（时长策略）**——总时长、讲述/Q&A 拆分、页数、节奏、压缩版本、超时风险。
3. **Slide Title Chain**——逐页结论式标题表。
4. **Universal Handoff Contract（权威 YAML）**——机器可校验的单一事实源。
5. **Adapter-specific Appendix**——仅当指定且运行时解析到下游 skill 时追加。
6. **交付前自检（最弱环）**——最可能翻车的 1–2 处 + 修复。

人读层在前供用户审阅，权威 YAML 在后供下游执行。

### 校验契约

契约可用提供的 schema 实际校验（需 `pyyaml` + `jsonschema`）：

```python
import yaml, json, re
from jsonschema import Draft202012Validator

schema = json.load(open("references/handoff-contract.schema.json"))
brief  = open("presentation-strategy-brief.md").read()
contract = next(b for b in re.findall(r"```yaml\n(.*?)```", brief, re.S)
                if "brief_tier:" in b)
Draft202012Validator(schema).validate(yaml.safe_load(contract))
```

`full` 档与 `lite` 档有不同必填字段，schema 已做分档条件校验。

---

## 如何使用

在支持 skill 的环境中触发，例如：

> 用 presentation-report-preflight 把我这份旧 deck/这个主题/这份源文档，做成一份演示策略简报，之后交给 huashu-design 生成 HTML。

Skill 会：先推断方向并（在交互模式下）请你确认 → 给出标题链请你过目 → 展开完整契约 → 指出最弱环。如果你想要速度，加一句"先出片 / 别问 / 直接给"即可跳过确认门。

---

## 设计原则

1. **运行时解析 > 写死**：下游名、语言、是否交互都在运行时决定，不进正文常量。
2. **单一事实源 + 可校验**：自检集中在一处；契约从"散文约定"升级为机器可校验 schema。
3. **状态显性化 > 隐性假设**：编造、缺数据、缺确认都变成契约里的枚举字段，逼模型每次填、并自动暴露。

---

## 适用场景

销售提案、融资路演、产品发布、年度/季度汇报、晋升答辩、项目复盘、技术分享、培训授课、咨询/战略汇报、内部周会、客户案例……每类都在 `scenario-playbooks.md` 里有专属打法与禁忌。

---

## 许可

MIT License，详见 [LICENSE](./LICENSE)。
