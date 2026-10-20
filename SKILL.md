---
name: two-layer-product-audit
description: "Product and code auditing protocol that enforces two distinct layers: (1) white-box source truth, and (2) rendered visual experience pass with screenshots and UX measurements. Mandates a strict human decision gate between the Diagnosis (the claims) and the Implementation Spec (the commitments) before an AI writes code."
license: MIT
metadata:
  author: We Build for Good
  version: "1.1.0"
---

# Two-Layer Product Audit: Diagnosis vs Specification Protocol

When AI agents audit an application, they typically fall into one of two traps:

1. **The Code-Only Trap**: They grep source files, find database optimizations and TypeScript typing flaws, but remain completely blind to the fact that the mobile login button is 11 pixels high, unclickable, and hidden beneath a cookie banner.
2. **The Scope-Inflation Trap**: They find twenty minor imperfections and immediately start refactoring code, rewriting features that the human founder never intended to change.

The `two-layer-product-audit` protocol solves both failures. It mandates two forensic layers of investigation and inserts a human decision gate between the **Diagnosis** and the **Implementation Specification**.

---

## Principle 1: The Two Forensic Layers

Every product audit must execute both layers:

### Layer 1: White-Box Source Truth (Engineering)
* Inspect the repository directly: schema migrations, API routes, authentication logic, security headers, bundle sizes, and error-handling branches.
* Find root causes rather than surface symptoms.

### Layer 2: Rendered Experience Pass (The Human Reality)
* Inspect the actual rendered DOM across three responsive viewports: Mobile (375px), Tablet (768px), and Desktop (1280px).
* Measure physical usability constraints:
  * Body text is readable on mobile (16px is a common baseline), and form inputs are at least 16px, or iOS Safari zooms in when they are focused.
  * Touch targets are at least 24px by 24px (WCAG 2.2 AA, 2.5.8); aim for 44px by 44px (Apple's guideline, WCAG AAA).
  * Few competing choices above the mobile fold (a heuristic, not a standard).
  * Text contrast passes WCAG AA (4.5:1, or 3:1 for large text).
* [skill-visual-sensory-audit](https://github.com/We-Build-For-Good/skill-visual-sensory-audit) automates the overflow, broken-image, request and tap-target checks at all three widths.
* Capture real screenshots of the primary user journey at every step.

---

## Principle 2: The Load-Bearing Gate (Diagnosis vs Spec)

This protocol enforces two separate documents, in strict sequence, with a human decision between them:

```
[ Forensic Audit (Diagnosis) ]
             |
             v
   [ Human Decision Gate ]  <--- The human accepts, modifies, or rejects findings
             |
             v
[ Implementation Spec (Commitments) ]
```

* **The Audit (The Diagnosis)**: A prioritized list of findings citing exact line numbers and screenshot evidence. It makes zero code changes and writes zero tickets.
* **The Gate**: The human operator reviews the diagnosis and decides what is genuinely worth fixing. Some findings will be rejected as low priority.
* **The Specification (The Commitments)**: Only accepted findings are converted into numbered, bounded execution packets.

Never allow an AI to generate the implementation spec in the same turn as the audit. An audit is an opinion; a spec is an economic commitment.

---

## Principle 3: Bounded Implementation Packets

When the human approves findings, the AI converts them into atomic execution packets:

* **Numbered & Self-Contained**: e.g. `Packet 01: Fix mobile viewport tap target on checkout CTA`.
* **Bounded Scope**: Each packet must be executable within a single work session.
* **Always Deployable**: Every completed packet must leave the application in a green, fully testable, and deployable state.
