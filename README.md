# Vibe Frontend Design

> Don't fight AI with words when you can tune with sliders.

A Claude Code skill that solves the most common VibeCoding frustration: **AI-generated frontend that's "almost right" but has awkward spacing, alignment, and typography.**

Instead of endlessly prompting "make the padding smaller" or "reduce the font size", this skill teaches Claude to generate an **interactive HTML prototype with adjustable sliders** — so you can tune every visual parameter in real-time and apply exact values back to your code.

## The Problem

AI coding tools produce frontend that's functional but visually rough:
- Spacing feels inconsistent or too loose/tight
- Font sizes don't feel balanced
- Alignment is slightly off
- Border radius, shadows, gaps aren't quite right

Trying to fix these by describing changes in natural language is slow, imprecise, and frustrating. You say "smaller padding" — AI makes it too small. You say "a bit bigger" — now it's back to where you started.

## The Solution

```
You: "帮我做一个 HTML 页面可交互原型，把所有视觉参数变成可调节的滑杆"

Claude: *generates an interactive HTML page with live sliders*

You: *drag sliders until everything looks perfect*

You: "这是调好的参数：{ title-fs: 22px, card-pad: 14px, ... }，请应用到实际代码中"

Claude: *applies exact values to your codebase*
```

![Concept](./assets/concept.png)

## Installation

```bash
# With npx (recommended)
npx skills add bert995/vibe-frontend-design

# Or manually copy SKILL.md to your skills directory
cp SKILL.md ~/.claude/skills/vibe-frontend-design/SKILL.md
```

## How It Works

### 1. Identify What Feels Off

| Category | Parameters |
|----------|-----------|
| Spacing | padding, margin, gap, section spacing |
| Typography | font-size, line-height, letter-spacing, font-weight |
| Alignment | text-align, justify-content, align-items |
| Sizing | width, height, max-width, border-radius |
| Visual | opacity, box-shadow, border-width |

### 2. Generate Slider Prototype

Claude creates a self-contained HTML file with:
- **Live preview** of your actual component/layout
- **Slider panel** with one slider per parameter (real-time updates)
- **Export button** to copy all values as CSS variables or JSON

### 3. Tune in Browser

Open the HTML file, drag sliders until satisfied. Start with spacing (biggest impact), then typography, then fine details.

### 4. Apply Back

Paste exported values to Claude. It applies them to your actual code — CSS variables, Tailwind config, or component styles.

## Example

See [`examples/card-tuner.html`](./examples/card-tuner.html) for a working prototype that demonstrates the slider tuning approach on a card component.

## Prompt Templates

**Full page tuning (Chinese):**
> 帮我做一个可交互 HTML 原型，把这个页面的间距、字体大小、行高、圆角等视觉参数全部做成滑杆，实时预览效果

**Full page tuning (English):**
> Create an interactive HTML prototype with all visual parameters as adjustable sliders with live preview

**Single component:**
> Turn this card component into an interactive prototype with sliders for all padding, margin, font-size, and border-radius values

**After tuning:**
> Here are the tuned parameters: [paste exported values]. Please apply them to the actual code.

## Tips

- **Scope small** — tune one section/component at a time, not the entire page
- **Wide ranges** — set slider min/max generously (e.g., font-size 8-72px)
- **Fix structure first** — if the layout is wrong, fix component hierarchy before tuning visual details
- **Use `oninput`** — sliders must update on drag, not on release

## Credits

Inspired by a technique shared on Xiaohongshu about making VibeCoding produce pixel-perfect frontend. The core insight: let humans do what humans are good at (visual judgment) and let AI do what AI is good at (writing code).

## License

MIT
