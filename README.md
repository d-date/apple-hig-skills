# apple-hig-skills

Agent skills for Claude Code and Codex based on Apple's [Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/). This repository is a plugin marketplace for both tools.

| Plugin | Skill | Source |
|---|---|---|
| `apple-app-icon` | [`apple-app-icon`](plugins/apple-app-icon/skills/apple-app-icon/SKILL.md) — layered Liquid Glass icons, Icon Composer, shape and masking, design rules, appearances (dark / clear / tinted), platform specifics, specs, and a review checklist | [HIG: App icons](https://developer.apple.com/design/human-interface-guidelines/app-icons) (June 8, 2026) |

## Install

### Claude Code

```sh
claude plugin marketplace add d-date/apple-hig-skills
claude plugin install apple-app-icon@apple-hig-skills
```

Or inside a session: `/plugin marketplace add d-date/apple-hig-skills`, then `/plugin install apple-app-icon@apple-hig-skills`.

Invoke it explicitly with `/apple-app-icon:apple-app-icon`, or just ask something like "review my app icon against the HIG".

### Codex

```sh
codex plugin marketplace add d-date/apple-hig-skills
codex plugin add apple-app-icon@apple-hig-skills
```

Invoke it explicitly with `$apple-app-icon` (or via `/skills`), or let Codex select it from the description.

### Manual

Copy `plugins/apple-app-icon/skills/apple-app-icon/` into `~/.claude/skills/` (Claude Code) or `~/.agents/skills/` (Codex).

## Update

```sh
claude plugin marketplace update apple-hig-skills && claude plugin update apple-app-icon@apple-hig-skills
codex plugin marketplace upgrade apple-hig-skills
```

To refresh the content from Apple, fetch the page data (the HTML page is JS-rendered):

```sh
curl -s https://developer.apple.com/tutorials/data/design/human-interface-guidelines/app-icons.json
```
