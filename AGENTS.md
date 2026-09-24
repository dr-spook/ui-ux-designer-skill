# AGENTS.md — ui-ux-designer

This repository packages a **portable UI/UX designer skill**. Any coding agent that
reads `AGENTS.md` (OpenAI Codex, Cursor, Windsurf, Aider, GitHub Copilot workspaces, etc.)
should treat the instructions below as active whenever the task is UI/UX design work.

## When to apply

Adopt this skill when the user wants to design or audit an interface — a UI/UX guide,
a screen or component spec, a design system or design tokens, a user flow, a mobile-first
layout, or a WCAG accessibility/UX review or redesign — even if they don't say "UI/UX".

**Do not apply it** when the user wants working code (HTML/CSS/React/etc.), a rendered
mockup image, or a framework/architecture decision. This skill **describes and prescribes**
interfaces; it never writes code and never chooses the tech stack.

## How to load it

The skill is written for progressive disclosure: a thin core plus references loaded on demand.

- **If your agent supports the Agent Skill format** (a `SKILL.md` with a `references/` folder):
  point it at [`skills/ui-ux-designer/`](skills/ui-ux-designer/). Read
  [`skills/ui-ux-designer/SKILL.md`](skills/ui-ux-designer/SKILL.md) first, then open a
  reference from `references/` only when the task touches that domain.
- **If your agent takes a single system prompt** (no on-demand file loading): use the
  flattened build [`dist/ui-ux-designer.bundle.md`](dist/ui-ux-designer.bundle.md) — it is
  `SKILL.md` plus every reference concatenated. Paste it as the system/instructions prompt.

## The contract in one line

Given a brief, backlog, module, or redesign request, produce a single self-contained
**Interface & Journey Guide** in Markdown (or, for a review, an **Audit**): derive the art
direction from the subject or a palette the user gives, justify every choice by a UX law /
cognitive principle / accessibility requirement / brand identity, design mobile-first and to
WCAG 2.1 AA, specify every state, and run the pre-delivery checklist before delivering.

Full details live in [`skills/ui-ux-designer/SKILL.md`](skills/ui-ux-designer/SKILL.md).
