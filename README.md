# Remotion + Claude Code

Create videos entirely through AI-powered conversation. This repo is a pre-configured [Remotion](https://www.remotion.dev/) project wired up with [Claude Code](https://claude.ai/code) — custom agents, MCP tools, and best-practice rules — so you can go from prompt to rendered video without touching a timeline editor.

Part of the [Agent Lab](https://www.skool.com/agent-lab) course on vibemarketing with AI.

## Quick Start

```bash
git clone https://github.com/agent-lab-skool/remotion
cd remotion
bun install
```

Then open two terminals:

```bash
# Terminal 1 — Remotion Studio (live preview at http://localhost:3000)
bun dev

# Terminal 2 — Claude Code
claude
```

Tell Claude to make a video. That's it.

## What's Included

```
├── src/
│   ├── index.ts          # Remotion entry point
│   ├── Root.tsx           # Composition registry (add new videos here)
│   └── HelloWorld.tsx     # Starter example
├── .claude/
│   ├── agents/            # Custom Claude Code subagents
│   │   ├── composition-designer.md   # Builds & modifies compositions
│   │   └── render-debugger.md        # Diagnoses render failures
│   └── skills/
│       └── remotion-best-practices/  # Rules Claude follows to write correct Remotion code
├── CLAUDE.md              # Project instructions Claude reads automatically
├── public/                # Your assets go here (fonts, images, videos)
└── out/                   # Rendered output (gitignored)
```

## What Claude Can Do

- **Create compositions** — Describe what you want and Claude writes the React component, registers it, and renders a preview
- **Animate anything** — Springs, easing curves, staggered reveals, color transitions, particle systems
- **Use transitions** — Fades, slides, wipes, flips between scenes via `@remotion/transitions`
- **Handle media** — Downloads real logos/photos, loads custom fonts, embeds video/audio
- **Debug renders** — If something breaks, Claude reads the error, checks the docs, and fixes it
- **Render on command** — Stills for quick previews, full MP4s when you're happy

## Useful Commands

```bash
bun dev                    # Open Remotion Studio
bun run render             # Render HelloWorld to out/video.mp4
bun run render:still       # Render a single frame to out/still.png

# Render any composition
bunx remotion render src/index.ts <CompositionId> out/<name>.mp4
bunx remotion still src/index.ts <CompositionId> out/<name>.png --frame=<N>
```

## How It Works

Remotion lets you write videos as React components. Every frame is a function of `useCurrentFrame()` — no keyframes, no timeline, just code. Claude Code understands the Remotion API through the embedded rules and MCP documentation tools, so it writes correct, renderable code on the first try (most of the time).

Your compositions live in `src/`, assets in `public/`, and rendered output in `out/`. The `.gitignore` is set up so your personal creations stay local — this repo stays a clean template.

## Requirements

- [Bun](https://bun.sh/) (package manager + runtime)
- [Claude Code](https://claude.ai/code) (CLI access)
- Node.js 18+ (for Remotion rendering)
