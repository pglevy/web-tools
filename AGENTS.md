# Agent Guidance for web-tools

This file provides context and instructions for AI agents working in this repository.

## What this project is

A collection of standalone, single-file HTML tools hosted on GitHub Pages. Each tool lives in the root of the repo as a self-contained `.html` file. No build process, no framework, no dependencies beyond optional CDN-loaded libraries.

Live at: https://pglevy.github.io/web-tools/

## Design and output quality

When building or updating tools, activate the `frontend-design` skill located at `.kiro/skills/frontend-design/SKILL.md`. This skill provides detailed guidance for producing distinctive, production-grade UI that avoids generic AI aesthetics. The goal is tools that feel genuinely designed, not templated.

Key things the skill emphasizes:
- Bold, intentional aesthetic direction (not default purple gradients and Inter font)
- Distinctive typography, cohesive color, meaningful motion
- Memorable visual identity specific to each tool's purpose

## Technical constraints

Every tool must be:
- A single `.html` file with inline CSS and JS
- No React, no build step
- Dependencies loaded from a CDN (cdnjs or jsDelivr) if needed
- A few hundred lines — small enough that any agent can read and understand it in full

## Existing patterns to follow

Looking at the tools already in this repo:
- Use semantic HTML with a `<meta name="description">` tag
- System font stack (`-apple-system, BlinkMacSystemFont, 'Segoe UI'...`) is acceptable as a baseline, but the frontend-design skill should push beyond this
- Include "Copy to clipboard" buttons where output text is involved
- Mobile-responsive with `@media` queries
- Lucide icons loaded inline as SVG (not as a CDN dependency) for lightweight iconography

## Hosting and file placement

- Finished tools go in the root directory as `tool-name.html`
- Work-in-progress files go in `gitignore/tools-in-progress/`
- Update `README.md` when adding a new tool (add it to the Tools list with a description and live link)

## Source guidance (external reference)

The following is adapted from Simon Willison's *[Useful patterns for building HTML tools](https://simonwillison.net/2025/Dec/10/html-tools/)*. It's included here as background context on the philosophy behind this project.

> ### The anatomy of an HTML tool
>
> These are the characteristics I have found to be most productive in building tools of this nature:
> 
> 1. A single file: inline JavaScript and CSS in a single HTML file means the least hassle in hosting or distributing them, and crucially means you can copy and paste them out of an LLM response.
> 2. Avoid React, or anything with a build step. The problem with React is that JSX requires a build step, which makes everything massively less convenient.
> 3. Load dependencies from a CDN. The fewer dependencies the better, but if there's a well known library that helps solve a problem, load it from cdnjs or jsDelivr.
> 4. Keep them small. A few hundred lines means the maintainability of the code doesn't matter too much: any good LLM can read them and understand what they're doing.
>
> The end result is a few hundred lines of code that can be cleanly copied and pasted into a GitHub repository.
>
> ### Take advantage of copy and paste
>
> One of the most useful input/output mechanisms for HTML tools comes in the form of copy and paste.
>
>I frequently build tools that accept pasted content, transform it in some way and let the user copy it back to their clipboard to paste somewhere else.
>
> Copy and paste on mobile phones is fiddly, so I frequently include “Copy to clipboard” buttons that populate the clipboard with a single touch.
>
> Most operating system clipboards can carry multiple formats of the same copied data. That’s why you can paste content from a word processor in a way that preserves formatting, but if you paste the same thing into a text editor you’ll get the content with formatting stripped.
>
> These rich copy operations are available in JavaScript paste events as well, which opens up all sorts of opportunities for HTML tools.