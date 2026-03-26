# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a knowledge repository for AI/ML learning — it contains notes, guides, curated resources, and reference materials (no application code, no build/test/lint commands).

## Structure

- **`prompts/`** — Prompt engineering guides and templates, organized by use case. The main guide (`prompt-engineering-guide.md`) introduces the C-R-A-F-T framework (Context, Requirement, Acceptance Criteria, Files/Scope, Tech Constraints). Frontend-specific prompt templates live in `prompts/frontend/`.
- **`transformer-architecture/`** — Notes explaining the Transformer architecture pipeline (tokenization, embedding, positional encoding, attention, feedforward, softmax).
- **`resources.md`** — Curated collection of AI tools, articles, and references (many sections still placeholder).
- **`README.md`** — Overview of the repo, links to popular LLMs, and current LLM trends.

## Content Guidelines

- All content is Markdown. When adding new material, follow the existing structure: use headings, tables, and code blocks for clarity.
- Prompt templates should follow the C-R-A-F-T framework pattern established in `prompts/prompt-engineering-guide.md`.
- New topic areas should get their own directory with a `README.md` (like `transformer-architecture/`).
