# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a personal notes repository, not a software project - there is no code to build, lint, or test. Content is written in Chinese.

- `GitLearn.md` - 目录索引, linking to the topic files below.
- `01-状态与日志查询.md` through `07-Git配置.md` - Git command reference notes split by topic (状态查询, 文件操作, 分支管理, 提交与历史, 标签管理, 远程仓库, Git配置), written as Markdown bullet lists and tables.
- `MarkDown.md` - Markdown syntax reference (headings, lists, tables, code blocks).

When adding new Git commands, put them in the matching numbered topic file; create a new numbered file only for a genuinely new topic, and update the index in `GitLearn.md`.

## Conventions

- Notes use `# 一级标题` per topic, with commands listed as `* 描述 \`git command\`` bullet items; options are documented in tables (选项 / 全称 / 说明).
- When editing or adding notes, follow the existing style: concise Chinese descriptions, command in backticks, one command per bullet.
- Git operations here are safe to perform - this repo is itself used for practicing Git workflows. Commits are typically short messages in Chinese or English (e.g. `添加远程仓库相关指令`).
