---
name: excalidraw-diagram
description: Create Excalidraw diagram JSON files that make visual arguments. Use when the user wants to visualize workflows, architectures, or concepts. Augmented for high-fidelity native Obsidian workflow.
---

# Excalidraw Diagram Creator (Obsidian v2.0 Augmented)

**Credits:** This skill is an augmented version of the original `excalidraw-diagram` skill by [coleam00](https://github.com/coleam00/excalidraw-diagram-skill).

Generate `.excalidraw.md` files that **argue visually**, natively rendered and validated within Obsidian.

## 🛠️ Obsidian Workflow Mandate (Primary)

This skill is optimized for environments where **Obsidian** and the **Excalidraw plugin** are active.

### 1. File Generation & Extension
Generate all diagrams with the `.excalidraw.md` extension. Use the following Markdown wrapper to ensure the Obsidian plugin parses the JSON correctly:

```markdown
---
excalidraw-plugin: parsed
tags: [excalidraw]
---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==

# Excalidraw Data

## Text Elements
%%
## Drawing
```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://excalidraw.com",
  "elements": [ ... ],
  "appState": { "viewBackgroundColor": "#ffffff", "gridSize": 20 },
  "files": {}
}
```
%%
```

### 2. Native Render & Validate Loop (MANDATORY)
Instead of using external Python/Playwright dependencies, use the **Obsidian CLI** to validate your work:

1. **Open:** `obsidian open path="path/to/diagram.excalidraw.md" vault="vault_name"`
2. **Toggle View:** `obsidian command id="markdown:toggle-preview"` (Ensures Excalidraw rendering is active)
3. **Capture:** `obsidian dev:screenshot path="/tmp/validation.png"`
4. **Audit:** Read the PNG using `read_file` and audit against the quality checklist.

### 3. Binding Integrity (CRITICAL)
**Never manually adjust individual coordinates to fix clipping or alignment.** 
Adjusting the `x/y` of a text element without updating its parent container (or vice-versa) **breaks the containerId binding**.
- **The Symptom:** Text disappears or arrows route through the center of shapes.
- **The Fix:** If a shape needs to be wider, regenerate the JSON ensuring the shape's width is larger and the text remains centered and bound.

---

## 🎨 Customization & Style

**All colors and brand-specific styles live in one file:** `references/color-palette.md`. Read it before generating any diagram and use it as the single source of truth for all color choices — shape fills, strokes, text colors, evidence artifact backgrounds, everything.

---

## 🧠 Core Philosophy: ARGUE, Don't DISPLAY

A diagram isn't formatted text. It's a visual argument that shows relationships, causality, and flow that words alone can't express.

- **The Isomorphism Test**: If you removed all text, would the structure alone communicate the concept? If not, redesign.
- **The Education Test**: Could someone learn something concrete from this diagram, or does it just label boxes? Use **Evidence Artifacts** (real code snippets, JSON formats, event names) to teach.

---

## 🔍 Depth Assessment (Step 0)

Before designing, determine what level of detail this diagram needs:

### Simple/Conceptual
Abstract shapes for philosophies, mental models, or high-level overviews.

### Comprehensive/Technical (Mandatory for Systems)
Use concrete examples. **You MUST include evidence artifacts.**
- **Research Mandate:** Look up actual specifications (JSON formats, API endpoints, event names) before drawing.
- **Multi-Zoom Architecture:** Show the **Summary Flow** (overview), **Section Boundaries** (grouping), and **Detail Inside Sections** (evidence) simultaneously.

---

## 🏗️ Visual Pattern Library

| Pattern | Behavior | Use Case |
|---------|----------|----------|
| **Fan-out** | Spawns multiple outputs | Sources, PRDs, root causes |
| **Convergence** | Combines inputs into one | Aggregation, funnels, synthesis |
| **Tree** | Hierarchy/Nesting | File systems, org charts (Use lines + text) |
| **Timeline** | Sequence of steps | Protocols, lifecycles (Use line + dots) |
| **Spiral/Cycle** | Loops/Improves | Feedback loops, evolution |
| **Cloud** | Abstract state | Context, memory, conversations |
| **Assembly line** | Transforms input | Processing, conversion |

**Lines as Structure:** Use `line` elements + free-floating text labels for trees and timelines instead of boxes. It creates a cleaner, more professional result.

---

## 📐 Design Process

1.  **Assess Depth:** Simple vs. Comprehensive.
2.  **Understand Deeply:** What does it DO? What relationships exist?
3.  **Map Patterns:** Assign visual patterns to concepts.
4.  **Variety Check:** Each major concept must use a different visual pattern.
5.  **Section-by-Section JSON:** Build large diagrams one section at a time. Do NOT generate the entire file in one shot (Claude's output limit is ~32k tokens).
    - Section 1: Entry point / trigger
    - Section 2: Main routing / Hero
    - Section 3: Details / Artifacts
6.  **Render & Validate Loop:** Run the Obsidian render-view-fix loop until perfect.

---

## ✅ Quality Checklist

1.  **Research Done:** Real specs, formats, and names used?
2.  **Evidence Included:** Code snippets or data examples present?
3.  **Minimal Containers:** <30% of text elements are inside boxes? (Prefer free-floating text + hierarchy).
4.  **No Text Overflow:** All text fits inside its container (if used).
5.  **Binding Intact:** Text visible inside shapes and arrows connect to edges.
6.  **Roughness 0:** Clean, crisp modern technical look.
7.  **Isomorphism:** Does the shape mirror the concept's behavior?
