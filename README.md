# Amebic Agent Skills

AI Agent Skills for the [Amebic](https://github.com/amebic/amebic) graphics toolkit. Build and render still graphics using React — one component, many outputs.

## Installation

Install via the [skills.sh](https://skills.sh) CLI:

```bash
npx skills add amebic/skills --skill amebic
```

Or install all skills from this repository:

```bash
npx skills add amebic/skills
```

### Manual Installation

For **Claude Code**:
```bash
git clone https://github.com/amebic/skills.git
cp -r skills/amebic ~/.claude/skills/
```

For **Cursor**:
```bash
git clone https://github.com/amebic/skills.git
cp -r skills/amebic ~/.cursor/skills/
```

For **OpenAI Codex**:
```bash
git clone https://github.com/amebic/skills.git
cp -r skills/amebic ~/.agents/skills/
```

## Available Skills

### `amebic` — Amebic Graphics Toolkit

Build and render still graphics with React. Covers composition authoring, visual design, CLI rendering, batch processing, and programmatic API usage.

**Use when:**
- Creating social media images (OG cards, Twitter images)
- Building app icons and favicons
- Designing marketing banners and hero images
- Setting up render pipelines
- Batch processing graphics

**Documents:**
- `SKILL.md` — Overview, installation, commands
- `COMPOSITION.md` — Creating graphics, design patterns, hooks
- `RENDER.md` — CLI usage, programmatic API, troubleshooting

## Skill Structure

```
amebic/
├── SKILL.md           # Main skill entry point with metadata
├── COMPOSITION.md     # Creating compositions guide
└── RENDER.md          # Rendering guide
```

## Requirements

- Node.js 18+
- Chromium (for rendering): `bunx playwright install chromium`

## What is Amebic?

Amebic lets you define graphics as React components and render them to multiple image formats and sizes:

```tsx
import { useComposition, registerComposition } from "@amebic/core";

export const MyGraphic = ({ title }) => {
  const { width, height } = useComposition();
  return (
    <div style={{ width, height, background: "#333", color: "#fff" }}>
      {title}
    </div>
  );
};

registerComposition(MyGraphic, {
  defaultProps: { title: "Hello" },
  outputs: [
    { name: "og", width: 1200, height: 630 },
    { name: "thumb", width: 400, height: 400 },
  ],
});
```

## License

MIT
