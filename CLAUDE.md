# CLAUDE.md

Claude should use [docs/ai-guidelines.md](docs/ai-guidelines.md) as the canonical project guidance for this repository.

Before making changes:

- Read the relevant source or documentation files first.
- Keep edits minimal and directly tied to the user request.
- Preserve the static-site structure: plain HTML pages with Tailwind via **Play CDN** and an **inline `tailwind.config`** in each HTML. There is **no build step, no framework, and no backend**.
- Do not introduce Tailwind CLI, PostCSS, a `package.json`, or a framework unless explicitly asked.
- Use the official palette (`#0A0A0A` background, `#00C853` green accent, `#FFFFFF` text); prefer named tokens in the inline `tailwind.config` over scattered hex values.
- Keep all user-facing content in Spanish.
- Do not modify deployment configuration, generated assets, or unrelated code unless explicitly asked.

## Documentation Ownership

`docs/ai-guidelines.md` is the shared source of truth for AI development policy, security rules, design tokens, role guidance, and reusable workflow rules.

This file is a Claude-specific adapter. Keep it minimal.

Do not duplicate shared policy content here. Do not update this file when changing shared AI policies, role guidance, or skill guidance unless the user explicitly asks to update `CLAUDE.md`.

When shared policy changes are needed, update `docs/ai-guidelines.md` only.
