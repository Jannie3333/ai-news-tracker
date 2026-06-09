# AI News & Content Research Skill

A Claude Code skill with two modes:

**Mode A — AI Industry Intelligence**
Searches Reddit, X/Twitter, HuggingFace for the latest AI model releases, leaks, and predictions. Focuses on what's dropping in the next two weeks.

**Mode B — Content Competitor Research**
Searches Google top-ranking articles around any product's keywords, analyzes article structure and angles, outputs actionable blog topic ideas and reusable content templates.

## Setup

1. Download `ai-news-skill/SKILL.md`
2. In the file, replace the placeholders:
   - `{{PRODUCT_NAME}}` → your product name (e.g. `Canva`, `Figma`, `Notion`)
   - `{{PRODUCT_DESCRIPTION}}` → one-line product description
   - `{{PRODUCT_KEYWORDS}}` → comma-separated core feature keywords
3. Place the `ai-news-skill/` folder in your Claude Code skills directory
4. Restart Claude Code

## Usage

**Trigger Mode A** (news):
> "今天有什么新闻" / "what AI models are releasing soon" / "any model leaks today"

**Trigger Mode B** (content research):
> "帮我研究 Canva 相关的竞品文章" / "find top Google articles about [product]" / "give me blog topic ideas for [product]"

**Switch product on the fly:**
> "把产品改成 Figma，重新研究一下"

## Product Config Examples

```
# Example 1: AI platform
产品名：iMini AI
产品定位：AI creation platform with image/video/LLM/canvas
核心功能关键词：AI image generator, AI video generator, multi-model chat

# Example 2: Design tool
产品名：Canva
产品定位：Online graphic design platform
核心功能关键词：graphic design, social media templates, photo editor

# Example 3: Writing tool
产品名：Jasper
产品定位：AI writing assistant for marketing teams
核心功能关键词：AI copywriting, blog writer, marketing content
```
