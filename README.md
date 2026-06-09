# AI News Tracker – Blog Hot Topic Skill

A Claude Code skill for tracking trending AI topics and automating blog keyword research. Designed to surface high-potential, low-competition keywords from current AI news and model releases.

## What It Does

- Monitors Google Trends and AI industry news for rising keywords
- Filters out already-written topics to avoid duplicates
- Recommends keywords with search volume estimates and trend direction
- Matches each keyword to a relevant product feature angle for natural content integration

## Usage

This is a `.skill` file for [Claude Code](https://claude.ai/code).

### Install

1. Open Claude Code
2. Run `/install ai-news.skill` or drag the `.skill` file into your workspace
3. The skill will be available as a slash command

### Trigger

Use the skill when you want keyword suggestions for a new blog post:

```
/ai-news-tracker
```

Or ask naturally:
```
推荐今天适合写的 AI 博客关键词
```

## Output Format

Each keyword recommendation includes:

- Keyword difficulty (KD) and estimated monthly search volume
- Trend status: rising / peak approaching / stable
- Reason it's trending now
- Suggested article format: How-to / Best-of / vs Comparison
- Relevant product feature angle for content integration

## Requirements

- Claude Code CLI
- Active internet connection (for trend research via WebSearch)