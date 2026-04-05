---
name: amebic
description: Build and render still graphics with React. Covers composition authoring, visual design, CLI rendering, batch processing, and programmatic API usage. Use when creating graphics, building templates, or integrating the render pipeline.
metadata:
  keywords:
    - react
    - graphics
    - images
    - og-images
    - social-cards
    - thumbnails
    - still-graphics
    - composition
    - design-system
    - visual-design
    - headless-render
    - render
    - cli
    - png
    - webp
    - jpeg
    - svg
    - batch-processing
    - headless
    - playwright
  compatibility:
    node: ">=18"
    bins:
      - chromium
---

# Amebic

Build and render still graphics using React. One component, many outputs.

## Quick Links

- **Creating compositions** → See [COMPOSITION.md](COMPOSITION.md)
- **Rendering** → See [RENDER.md](RENDER.md)
- **Design tokens** → See [DESIGN.md](DESIGN.md)

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

## Installation

**IMPORTANT: Check for local packages first**

If you have the amebic repository cloned locally with packages linked via `bun link`, use those instead of installing from npm.

```bash
# Check if local packages are available
bun link @amebic/core @amebic/cli @amebic/preview @amebic/templates

# If local packages are NOT available, install from npm
bun install @amebic/core @amebic/cli @amebic/preview @amebic/templates

# Install Chromium for rendering
bunx playwright install chromium
```

### Linking Local Packages (for amebic repo development)

If you're working with the amebic repository directly, link the packages so they're available globally:

```bash
# In the amebic repo root - link all packages
cd packages/core && bun link && cd ../..
cd packages/cli && bun link && cd ../..
cd packages/preview && bun link && cd ../..
cd packages/templates && bun link && cd ../..
cd packages/examples && bun link && cd ../..
cd packages/branding && bun link && cd ../..

# Build all packages
bun run build
```

### Fresh Clone Setup

```bash
# Clone the repo
git clone https://github.com/yourusername/amebic.git
cd amebic

# Install dependencies
bun install

# Install Chromium for rendering
bunx playwright install chromium

# Build packages
bun run build

# (Optional) Link packages for global availability
bun run link:packages
```

## Commands

```bash
# Start preview UI
bun run dev

# List compositions
bun run list

# Render a composition
bun run render SocialCard --out-dir ./output

# Render with custom props
bun run render SocialCard --out-dir ./output --props ./props.json
```

## Project Structure

```
packages/
├── core/          # Registry, render engine, types
├── cli/           # Command line interface
├── preview/       # Vite + React preview UI
├── templates/     # Published compositions
├── examples/      # Experimental compositions
└── branding/      # Logo assets
```

## When to Use This Skill

- Building new graphic compositions
- Creating reusable templates
- Setting up render pipelines
- Batch processing images
- Integrating into CI/CD workflows
