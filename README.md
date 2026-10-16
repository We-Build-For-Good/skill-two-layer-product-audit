# Two-Layer Product Audit: Diagnosis vs Specification Protocol

> **An open-source AI engineering protocol from [We Build for Good](https://webuildforgood.com)**  
> *Separate forensic diagnosis from engineering commitments.*

---

## Overview

`two-layer-product-audit` is an operational auditing protocol for AI assistants (Claude Code, Cursor, Antigravity, OpenAI Codex).

It ensures that product audits combine both **white-box source code inspection** and **rendered visual/UX passes**, while enforcing a strict human gate between identifying problems and writing code to fix them.

---

## The Two Layers

1. **White-Box Source Truth**: Investigates backend schemas, API security, TypeScript types, and unhandled errors in the codebase.
2. **Rendered Experience Pass**: Uses browser automation to capture screenshots at 375px mobile, 768px tablet, and 1280px desktop, verifying font sizes, tap targets, contrast, and layout shifts.

---

## Installation

### For Claude Code
```bash
git clone https://github.com/webuildforgood/skill-two-layer-product-audit.git ~/.claude/skills/two-layer-product-audit
```

### For Cursor
```bash
mkdir -p .cursor/skills
git clone https://github.com/webuildforgood/skill-two-layer-product-audit.git .cursor/skills/two-layer-product-audit
```

### For Antigravity / Open Agent Skills
```bash
mkdir -p .agents/skills
git clone https://github.com/webuildforgood/skill-two-layer-product-audit.git .agents/skills/two-layer-product-audit
```

---

## License

MIT License. Developed and maintained by [We Build for Good](https://webuildforgood.com).
