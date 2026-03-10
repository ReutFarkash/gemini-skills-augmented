---
name: excalidraw-diagram
description: Create Excalidraw diagram JSON files that make visual arguments. Augmented for native Obsidian workflow.
---

# Excalidraw Diagram Creator (Obsidian Augmented)

**Credits:** This skill is an augmented version of the original `excalidraw-diagram` skill by [coleam00](https://github.com/coleam00/excalidraw-diagram-skill).

Generate `.excalidraw.md` files that **argue visually**, natively rendered and validated within Obsidian.

## Obsidian Workflow Mandate

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
- **The Fix:** If a shape needs to be wider, regenerate the JSON ensuring the shape's width is larger and the text remains centered and bound. Prefer letting the user make final spacing tweaks in the Obsidian UI if the base structure is sound.

---

## Design Process (Do This BEFORE Generating JSON)

### Step 0: Assess Depth Required
Before anything else, determine if this needs to be:
- **Simple/Conceptual**: Abstract shapes, labels, relationships (mental models, philosophies)
- **Comprehensive/Technical**: Concrete examples, code snippets, real data (systems, architectures, tutorials)

### Step 1: Understand Deeply
Read the content. For each concept, ask:
- What does this concept **DO**? (not what IS it)
- What relationships exist between concepts?
- What would someone need to SEE to understand this?

### Step 2: Map Concepts to Patterns
For each concept, find the visual pattern that mirrors its behavior:
- **Fan-out**: Spawns multiple outputs
- **Convergence**: Combines inputs into one
- **Tree**: Has hierarchy/nesting
- **Timeline**: Is a sequence of steps
- **Spiral/Cycle**: Loops or improves continuously
- **Cloud**: Abstract state or context
- **Assembly line**: Transforms input to output

### Step 3: Generate JSON (Section-by-Section)
For large diagrams, generate elements in chunks. Use descriptive string IDs and namespace seeds by section (e.g., 100xxx, 200xxx).

---

## Quality Checklist

### Visual Validation (Render Required)
1. **Rendered via Obsidian**: Diagram has been captured and visually inspected.
2. **No text overflow**: All text fits within its container.
3. **No overlapping elements**: Shapes and text don't overlap unintentionally.
4. **Binding intact**: Text is visible inside its container and arrows connect to edges.
5. **Readable**: Text is legible in the rendered PNG.
6. **Balanced composition**: No large empty voids or overcrowded regions.
