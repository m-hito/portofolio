# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file portfolio website for xmvcz (Roblox Game Developer). The entire site is one `index.html` file with embedded CSS and JavaScript — no build step required.

## Commands

- **Preview**: Open `index.html` directly in a browser, or serve locally with `npx serve .`
- **No tests/linting**: This is a static HTML project with no test suite or build tools

## Architecture

### Theme System
Five color themes (cyan, magenta, lime, amber, white) are controlled via `data-theme` attribute on `<html>` and CSS custom properties. Each theme defines:
- `--p` / `--p-r`: Primary color (used for video panel glow on hover)
- `--s` / `--s-r`: Secondary color
- `--a` / `--a-r`: Accent color
- `--hover-glow` / `--hover-glow-rgb`: Unique color for info-panel hover (contrasting, not matching theme)
- `glow`, `border`, `bg-g1/2/3`: Standard theme values

Theme is persisted in `localStorage` under key `xmvcz-theme`.

### Page Structure
- **Hero**: Animated rings, dot field, gradient text title
- **Projects**: 3 project cards with Vimeo embeds, expand/collapse via "Details" button or global "Expand All"
- **Contact**: Social links (email, Discord, Roblox, GitHub)

### Card Layout
When expanded (≥860px), cards switch to a side-by-side grid: video panel (left) + info panel (right). The video panel shows a Vimeo iframe at 16:9 aspect ratio.

### Key CSS Transitions
- Card hover: outer glow uses `var(--glow)` (theme color)
- Video-panel hover: outer glow uses `var(--glow)` (theme color)
- Info-panel hover: outer glow and inner shadow use `var(--hover-glow)` (unique per theme)
