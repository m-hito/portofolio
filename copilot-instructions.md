# Copilot instructions for this repository

- Project type: Single-file static portfolio site (index.html contains HTML, CSS, and JS). No build step.

Build / test / lint
- No build step. Preview locally by opening index.html in a browser.
- Alternative quick server: `npx serve .` from the repo root.
- No test or lint scripts detected in package.json. To run a single test (if added): add an npm script `test:single` and run `npm run test:single`.

High-level architecture
- Single-file site: index.html holds markup, styles, and scripts — edit within that file.
- Theme system: controlled by `data-theme` on `<html>` and CSS custom properties (variables). Themes: cyan, magenta, lime, amber, white.
- Theme variables: `--p`, `--s`, `--a` and `--p-r`, `--s-r`, `--a-r` (RGB triplets). Hover/accent uses `--hover-glow` and `--hover-glow-rgb`.
- Theme persistence: localStorage key `xmvcz-theme` stores the selected theme.
- Sections of interest: Hero, Projects (#projects-section), Project cards (`.project-card`), Video panel (`.video-panel` / `.video-wrap`), Info panel (`.info-panel`).
- Projects: each card embeds a Vimeo iframe (16:9 via `.video-wrap` padding-bottom:56.25%) and has expandable details. At ≥860px cards switch to side-by-side layout (video left, info right).

Key conventions and patterns
- Everything lives in index.html — prefer small, surgical edits inside that file rather than splitting files unless adding a build step.
- Theme naming: short variable keys (`--p`, `--s`, `--a`) with `-r` suffix for RGB; use these consistently when adding UI elements.
- Glow/border values use `--glow` and `--border` derived per theme; prefer them for consistent visuals.
- Look for `xmvcz-theme` in JS to find theme-selection logic and persistence.
- Project expansion/controls: preserve data attributes and CSS class names when editing cards (e.g., `.toggle-chip`, `.project-card`, `.video-wrap`).
- Vimeo embeds: preserve `iframe` attributes and sizes; video container uses `.video-wrap iframe` positioning.

Existing AI / assistant configs
- package.json lists `@anthropic-ai/claude-agent-sdk` as a dependency only; no CLAUDE.md present in the repo.

MCP servers
- This is a static web project; consider Playwright for browser tests or screenshots. Would you like Playwright MCP configured?

Summary
- Created copilot-instructions.md summarizing preview commands, architecture, and repo-specific conventions. Want adjustments or more coverage (e.g., JS entrypoints, CSS vars to change)?

## Author intent (portfolio)

- This repo is a personal portfolio for a Roblox / game developer (xmvcz).
- Highlight: combat systems, VFX, Roblox experience, and technical skills.
- Keep the design: dark, minimal, focused on 3–5 strong projects.
- Do NOT add complex build tools; keep everything in index.html.
- Prefer semantic HTML (header, main, section, footer).
- Do not rewrite the entire index.html unless explicitly asked; prefer incremental edits.

## Copilot behavior

- Before large edits, propose the plan as comments or in Copilot Chat.
- When modifying CSS, only touch the minimal selectors needed.
- When updating JS, keep existing function names and data attributes.
- When adding new sections (About, Skills, Contact), follow the existing class naming style.
