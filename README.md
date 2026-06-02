# sales-script-jp

TikTok Shop Japan 卖货脚本操盘手 — Claude Code Skill。

梨花・マリナ 2 个账号的 Tame-guchi(タメ口)日语卖货脚本撰写 / 数据复盘 / 自我进化一体化工具。

---

## 功能

| 模式 | 触发词 | 用途 |
|---|---|---|
| **A** 写脚本 | `写tts脚本` / `tts卖货脚本` | 3 阶段交互(诉求 → 切入点 → 5 变量)生成脚本 |
| **B** 看今日数据 | `tts今天数据` | 扫描飞书表,>3 单即时告警 |
| **C** 周度复盘 | `tts本周复盘` | 周日 Top 3 自动汇总 |
| **D** 喂入爆款 | (B/C 模式后粘贴脚本) | 自动沉淀进 winning-patterns + 钩子/CTA 库 |
| **E** 评分 | `X 分` / `X 分,理由...` | 单条脚本评分写入日志 |
| **F** 库存追加 | `加入钩子库` / `加入CTA库` | 口头追加钩子/CTA 到弹药池 |
| **P** 前置检查 | (自动) | 每次激活先 nag 一次"该看数据了" |

---

## 文件结构

```
sales-script-jp/
├── SKILL.md                            # 入口 & 流程编排(模式 A-F + 强制规则 R1-R40+)
├── README.md                           # 本文件
└── references/
    ├── formulas.md                     # 公式骨架稳定层(3 大诉求 × 10 子类)
    ├── hooks-library.md                # 钩子弹药池(21 条 + 4 反例,6 类)
    ├── cta-library.md                  # CTA 弹药池(20 条 + 6 反例,5 类)
    ├── winning-patterns.md             # 爆款档案进化层(14 条爆款 + 5 真出单)
    ├── winning-patterns-template.md    # 新爆款条目模板
    └── state.json                      # 运行时状态(日期戳 / 周维度去重池)
```

---

## 知识库分层

- **稳定层** `formulas.md`:公式骨架,只读不写
- **弹药池** `hooks-library.md` + `cta-library.md`:0-3s 钩子 + 13-20s CTA,带 9 字段元数据 + 7 级验证状态
- **进化层** `winning-patterns.md`:模式 D 自动累积追加,永不删除旧条目
- **运行时** `state.json`:日期戳 + 周维度去重池

---

## 数据源

飞书电子表格『电商类账号数据统计表』 — 列结构:
A=发布日期 / B=账号名(梨花|玛丽娜) / C=视频链接 / D=带品 / E=播放量 / F=完播率 / G=橱窗点击率 / H=CTOR / I=出单数 / J=复盘

---

## 安装

把整个 `sales-script-jp` 目录放到 Claude Code 的 skills 目录:

```bash
~/.claude/skills/sales-script-jp/
```

依赖:
- [`lark-cli`](https://github.com/larksuite/lark-cli) — 读飞书表
- 同目录 `lark-shared` skill 用于认证

---

## 版本

- **v1.7.0**(2026-06-02):新增 hooks-library + cta-library 弹药池 + 模式 F 库存追加
- v1.6.0(2026-05-15):R34-R37 梨花 IP 风格落盘
- v1.5.0(2026-05-14):R31-R33 マリナ IP 风格落盘
- v1.4.0(2026-05-07):R8-R30 整合(本地化优先 + 真出单 vs 自评区别)
- v1.3.0(2026-05-06):R8-R12 SNS 化精修
- v1.2.0(2026-04-30):R5 周维度去重 + R8 自创比喻禁止
- v1.0.0(2026-04-27):初版

详细规则演进见 `references/winning-patterns.md` 末尾「L2/L3 落盘历史」。
