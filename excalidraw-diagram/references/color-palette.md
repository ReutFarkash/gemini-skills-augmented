# 🎨 Semantic Color Palette

Use this as the **single source of truth** for all color choices in your diagrams. Do not invent new colors.

You can choose between two aesthetic options based on the user's preference or vault style.

---

## Option 1: Standard Modern
Clean, crisp, and high-contrast. Best for standalone technical documentation.

| Semantic Purpose | Fill | Stroke | Why |
|------------------|------|--------|-----|
| **Primary/Neutral** | `#3b82f6` | `#1e3a5f` | Default boxes, main flow |
| **Secondary** | `#60a5fa` | `#1e3a5f` | Supporting elements |
| **Start/Trigger** | `#fed7aa` | `#c2410c` | Origin points, entry |
| **End/Success** | `#a7f3d0` | `#047857` | Outcome, success |
| **Decision/Branch** | `#fef3c7` | `#b45309` | Branching, conditions |
| **AI/Model** | `#ddd6fe` | `#6d28d9` | AI actions, LLM steps |
| **Error/Alert** | `#fecaca` | `#b91c1c` | Failures, blockers |
| **Neutral/Context** | `#f1f5f9` | `#64748b` | Background info, containers |

**Text Colors (Standard):**
- Title: `#1e40af` (28px)
- Subtitle: `#3b82f6` (20px)
- Body: `#64748b` (16px)
- On Light Fill: `#374151`
- On Dark Fill: `#ffffff`

**Background:** `#ffffff`

---

## Option 2: AnuPpuccin (Rose Pine Light)
Soft, pastel-driven, and cohesive with the Obsidian AnuPpuccin theme. Best for diagrams embedded directly in the Obsidian Vault.

| Semantic Purpose | Fill | Stroke | Base Color Name |
|------------------|------|--------|-----------------|
| **Primary/Neutral** | `#E5E6F5` | `#6F72C0` | Blue |
| **Secondary** | `#E7F1F6` | `#76ABC5` | Sky |
| **Start/Trigger** | `#FAEAE3` | `#E8A687` | Peach |
| **End/Success** | `#E4F4E9` | `#64BE82` | Green |
| **Decision/Branch** | `#FBF2E0` | `#EBC475` | Yellow |
| **AI/Model** | `#EAE6F0` | `#907AA9` | Lavender |
| **Error/Alert** | `#F3E3ED` | `#B25A89` | Red |
| **Neutral/Context** | `#F8F5F1` | `#B4799B` | Base / Mauve |

**Text Colors (AnuPpuccin):**
- Title: `#5980BF` (Sapphire, 28px)
- Subtitle: `#907AA9` (Lavender, 20px)
- Body: `#6F72C0` (Blue, 16px)
- On Light Fill: `#1E1E2E` (Dark text for contrast)
- On Dark Fill: `#F8F5F1` (Base text)

**Background:** `#F1EAE4` (Mantle) or `transparent`

---

## Evidence Artifacts
Used for code snippets, data examples, and other concrete evidence inside technical diagrams.

| Artifact | Background | Text Color | Font |
|----------|------------|------------|------|
| **Code / JSON** | `#1e293b` | `#22c55e` | Monospace (fontFamily: 3) |
| **Log / Terminal** | `#000000` | `#00ff00` | Monospace (fontFamily: 3) |

---

## Standard Settings
- **Roughness:** `0` (Clean/Modern)
- **StrokeWidth:** `1` (Subtle) or `2` (Standard)
- **Opacity:** `100` (Always opaque)
- **FontFamily:** `3` (Monospace/Technical)
