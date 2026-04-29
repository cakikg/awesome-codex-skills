---
name: brand-guidelines
description: Applies OpenAI's brand colors and typography to any artifact that should match the Codex/OpenAI look-and-feel. Use it when brand colors or style guidelines, visual formatting, or company design standards apply.
license: Complete terms in LICENSE.txt
---

# OpenAI Brand Styling

## Overview

Apply OpenAI's brand identity and style resources with this skill.

**Keywords**: branding, corporate identity, visual identity, post-processing, styling, brand colors, typography, OpenAI brand, Codex, visual formatting, visual design

## Brand Guidelines

### Colors

**Main Colors:**

- Charcoal: `#0E0F12` - Primary text and dark backgrounds
- Slate: `#202123` - Surface backgrounds
- Mist: `#F5F7FA` - Light backgrounds and text on dark
- Steel: `#9EA1AA` - Secondary elements and dividers

**Accent Colors:**

- OpenAI Green: `#10A37F` - Primary accent
- Azure: `#2B8FFF` - Secondary accent
- Graphite: `#40434A` - Neutral accent for icons or strokes

### Typography

- **Headings**: Inter, Semibold/Bold (with Arial fallback)
- **Body Text**: Inter, Regular (with Arial fallback)
- **Code/Monospace**: IBM Plex Mono (with Menlo/monospace fallback)
- **Note**: Fonts should be pre-installed in your environment for best results

## Features

### Smart Font Application

- Applies Inter Semibold/Bold to headings (24pt and larger)
- Applies Inter Regular to body text
- Applies IBM Plex Mono for code snippets or inline code
- Automatically falls back to Arial/Menlo if custom fonts unavailable
- Preserves readability across all systems

### Text Styling

- Headings (24pt+): Inter Semibold/Bold
- Body text: Inter Regular
- Smart color selection based on background (Charcoal or Mist as appropriate)
- Preserves text hierarchy and formatting

### Shape and Accent Colors

- Non-text shapes use accent colors
- Cycle accent usage: OpenAI Green → Azure → Graphite
- Maintains visual interest while staying on-brand

## Technical Details

### Font Management

- Uses system-installed Inter and IBM Plex Mono fonts when available
- Provides automatic fallback to Arial (headings/body) and Menlo/monospace (code)
- No font installation required - works with existing system fonts
- For best results, pre-install Inter and IBM Plex Mono fonts in your environment

### Color Application

- Uses RGB color values for precise brand matching
- Applied via python-pptx's RGBColor class
- Maintains color fidelity across different systems

## Personal Notes

> **Note (personal fork):** I've found that on macOS, Inter is available via the [Google Fonts GitHub repo](https://github.com/google/fonts) or by installing the font directly from rsms.me/inter. IBM Plex Mono can be grabbed from IBM's GitHub. Worth doing once so the fallback paths never trigger.

> **Tip:** On Ubuntu/Debian, you can install both fonts in one shot:
> ```bash
> sudo apt install fonts-inter fonts-ibm-plex
> ```
> After installing, run `fc-cache -fv` to refresh the font cache. Confirmed working on Ubuntu 22.04 LTS.

> **Tip (macOS):** After downloading Inter from rsms.me/inter, you can install all weights at once by selecting all `.ttf` files in Finder and double-clicking. No restart needed — apps pick up the new fonts immediately.
