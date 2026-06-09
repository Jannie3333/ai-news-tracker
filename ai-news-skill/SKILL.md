---
name: ai-news
description: >
  AI行业情报 + 竞品内容研究。触发场景：
  (1) 用户问"今天有什么新闻"、"最新AI消息"、"有什么模型要发布"、"AI有什么泄露"、"这周AI圈发生了什么"等——执行【模式A：热点情报】；
  (2) 用户说"帮我研究[产品名]相关的关键词/竞争文章"、"找找关于[产品]的谷歌排名文章"、"分析竞争对手文章结构"、"给我内容选题灵感"等——执行【模式B：内容研究】；
  (3) 用户同时要"新闻+内容研究"——两个模式都执行。
  只要涉及AI行业动态、模型发布预测泄露、或产品关键词内容竞品分析，都应主动使用此skill。
---

<!--
  ╔══════════════════════════════════════════════════════╗
  ║  可配置项：把下面的 {{PRODUCT_NAME}} 替换成你的产品名  ║
  ║  例如：iMini AI → Canva → Midjourney → 任意产品      ║
  ╚══════════════════════════════════════════════════════╝
-->

## 模式A：AI热点情报

### 目标
抓取海外AI行业最新动态，重点是：近期/即将发布的模型、泄露消息、社区预测。

### 执行（并行搜索）

同时发出以下 WebSearch：

1. `AI model release leak upcoming reddit [当前年月]`
2. `image generation video generation AI model announce release this week`
3. `GPT Claude Gemini Sora Kling Flux new model release leak rumor`
4. `AI model release prediction next two weeks`
5. `AI model leaked insider information [当前年]`

同时 WebFetch：`https://huggingface.co/papers`（提取最新论文标题，判断技术方向）

### 输出格式（中文）

---
**🔥 未来两周内可能发布的模型**

每个模型单独列出：
- **名称**（含版本号）— 类型（文生图/文生视频/LLM/多模态）
- 预计时间 | 置信度：🟢高 / 🟡中 / 🔴低（未经证实）
- 依据来源（社区预测 or 官方信号）+ 链接

**💧 模型泄露 & 内部消息**
- 泄露内容摘要 + 来源链接
- 暂无则写"暂无"

**📣 今日最重要3–5条AI动态**
- **[模型/公司]** 一句话描述 → 来源链接

**🧭 本周AI行业竞争焦点**（3句话）
---

---

## 模式B：内容竞品研究

### 目标
围绕指定产品，搜索相关高流量关键词，找到谷歌排名靠前的优质文章，
分析其内容结构和选题思路，给用户提供可直接使用的创作参考。

### 产品信息（替换这里）

```
产品名：{{PRODUCT_NAME}}
产品定位：{{PRODUCT_DESCRIPTION}}
核心功能关键词：{{PRODUCT_KEYWORDS}}
```

**使用示例：**
```
产品名：iMini AI
产品定位：AI 创作平台（图像/视频/LLM/Canvas 画布）
核心功能关键词：AI image generator, AI video generator, multi-model chat, background remover

产品名：Canva
产品定位：在线设计工具
核心功能关键词：graphic design, social media templates, photo editor, presentation maker
```

> 💡 用户可随时说"把产品改成 XXX"，skill 自动切换，无需重新配置。

### 执行步骤

**Step 1 — 关键词搜索（并行）**

围绕 {{PRODUCT_NAME}} 的功能，发出以下 WebSearch：

```
"{{PRODUCT_NAME}} alternative [当前年]"
"best [产品核心功能] tool [当前年]"
"[产品核心功能] comparison [当前年]"
"{{PRODUCT_NAME}} review reddit"
"how to [产品核心使用场景] tutorial"
"{{PRODUCT_NAME}} vs [主要竞品] [当前年]"
```

同时搜索竞品博客方向：
```
"[竞品博客域名] [核心功能关键词] best practices"
"[功能关键词] ultimate guide [当前年]"
```

**Step 2 — 抓取排名靠前的文章**

对 Step 1 搜索结果中排名前5的文章，逐一 WebFetch，提取：
- 文章标题 & URL
- H1/H2/H3 标题结构（完整骨架）
- 开篇钩子（前100字的切入方式）
- 核心论点 & 差异化卖点
- CTA 或结尾策略
- 文章字数估算
- 内链/外链引用策略

**Step 3 — 综合输出（中文）**

---
**🔍 {{PRODUCT_NAME}} 内容竞品研究报告**

**① 高价值关键词矩阵**
| 关键词 | 搜索意图 | 竞争难度 | 推荐体裁 |
|--------|---------|---------|---------|
| ...    | ...     | 低/中/高 | How-to/Best类/vs对比 |

**② 排名文章结构分析**（每篇单独列）

**文章：[标题](URL)**
- 体裁：How-to / Best类 / vs对比 / 评测
- 骨架：
  - H2: ...
  - H2: ...（含H3小节）
- 开篇方式：[痛点切入 / 数据开头 / 场景代入 等]
- 核心差异点：这篇文章胜出的原因
- 字数：约 xxxx 字

**③ 选题灵感 & 快速创作建议**

列出3–5个可立即执行的文章选题，每个包含：
- 建议标题（SEO格式）
- 核心角度（为什么适合 {{PRODUCT_NAME}}）
- 参考哪篇竞品文章的结构
- 预计字数区间

**④ 通用文章骨架（直接套用）**

提炼出一个骨架模板，可直接用于写 {{PRODUCT_NAME}} 相关文章：

```
H1: [目标关键词] + 卖点/结果
引言（<100字）：痛点 + 解决方案预告

H2: What is [主题]（可选，面向新手）
H2: Why [主题] matters in [当前年]
H2: How to [核心操作] with {{PRODUCT_NAME}}
  H3: Step 1 ...
  H3: Step 2 ...
H2: [Best / Top N] [子话题]
H2: [竞品] vs {{PRODUCT_NAME}}（可选）
H2: FAQ
结尾 CTA（<3行）：引导访问 {{PRODUCT_NAME}}
```
---
