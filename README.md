# apple-app-icon-skill

An agent skill that condenses Apple's [Human Interface Guidelines: App icons](https://developer.apple.com/design/human-interface-guidelines/app-icons) — layered Liquid Glass icons, Icon Composer, shape and masking, design rules, appearances (dark / clear / tinted), platform specifics, and specs — plus a review checklist.

Based on the HIG revision of June 8, 2026.

## Install

### Claude Code

Personal (all projects):

```sh
git clone https://github.com/d-date/apple-app-icon-skill ~/.claude/skills/apple-app-icon
```

Project only (commit it to share with your team):

```sh
git clone https://github.com/d-date/apple-app-icon-skill .claude/skills/apple-app-icon
```

Claude Code picks it up automatically. Invoke it explicitly with `/apple-app-icon`, or just ask something like "review my app icon against the HIG".

### Codex

Personal (all projects):

```sh
git clone https://github.com/d-date/apple-app-icon-skill ~/.agents/skills/apple-app-icon
```

Project only:

```sh
git clone https://github.com/d-date/apple-app-icon-skill .agents/skills/apple-app-icon
```

Restart Codex to load it. Invoke it explicitly with `$apple-app-icon` (or via `/skills`), or let Codex select it from the description.

## Update

```sh
git -C <install-path> pull
```

To refresh the content from Apple, fetch the page data (the HTML page is JS-rendered):

```sh
curl -s https://developer.apple.com/tutorials/data/design/human-interface-guidelines/app-icons.json
```
