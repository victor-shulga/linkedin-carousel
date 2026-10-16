# linkedin-carousel

A **Claude Code skill** that turns raw text into a finished LinkedIn carousel
(1080×1350, 4:5) in the Victor Shulga brand, built slide by slide in a new Figma file.

You paste a draft or a topic. Claude splits it into slides, writes every slide into Figma
through the Figma MCP, screenshots each one inline so you can check it in the chat, and
gives you the Figma link for final edits and PNG export.

## What you get

→ a new Figma file with the full carousel: cover, content slides, closing slide

→ white canvas, coral accents, Inter Tight + Inter type, author block and bowtie mark on every slide

→ a screenshot of each slide in the chat before you open Figma

→ a short note on what is worth tweaking by hand

## Install

```bash
npx skills add victor-shulga/linkedin-carousel
```

Then in Claude: "зроби карусель з цього тексту", "10 слайдів про холодний аутріч",
"make a carousel from this".

## Requirements & integrations

| Integration | Used for | Required? | Auth/setup |
|---|---|---|---|
| Figma MCP (`use_figma`) | creating the file and drawing every slide | Yes | connect the official Figma connector in Claude, edit access to your drafts |
| Claude Code or claude.ai | running the skill | Yes | `npx skills add` or «Upload a skill» |

The brand (colors, fonts, photo, wordmark) is baked into the skill. To use it for another
brand, swap the files in `skills/linkedin-carousel/assets/` and the Brand block in `SKILL.md`.

## License

MIT
