# ExplainLoop

**Turn articles into explanatory GIFs with an AI agent.**

ExplainLoop is an [Agent Skill](https://agentskills.io/) for making short, silent animations from an article, URL, pasted text, or a selected passage. The agent identifies a relationship worth animating, writes an editable SVG scene, and renders a GIF. The renderer is deterministic; the interpretation and art direction come from the agent and the source text.

中文：**把文章重点变成看得懂的动态图。** 这是面向 Codex、Claude Code 等 Agent 的 Skill，不是输入文章后直接运行的独立 Web 服务。

![A fictional email becomes a calendar event](demo/08-email-16x9.gif)

The animation above uses an [original fictional sample](demo/sample-article.md). Its [editable scene](assets/examples/showcase/08-email-16x9.scene.mjs) is included.

## What it supports

- Select 1–3 meaningful claims or relationships from the full article or a section you specify.
- Keep the source status and qualifiers visible in the scene metadata; avoid invented product UI, numbers, and outcomes.
- Choose from 9 style presets, 10 background treatments, and 30 semantic components such as email, calendar, message, task, timeline, and chart.
- Render 30 fps GIFs with editable `.scene.mjs` source. Default output is 1600×900; 4:3, square, portrait, and matching custom sizes are supported.
- Check batch style consistency, preview key frames, and inspect exported GIF metadata.

These are guided capabilities of the Skill. The command-line renderer accepts a completed scene file; it does not read an article and design a scene by itself.

## Gallery

| Example | Output | Scene source |
| --- | --- | --- |
| Email to calendar, landscape | [1600×900 GIF](demo/08-email-16x9.gif) | [16:9 scene](assets/examples/showcase/08-email-16x9.scene.mjs) |
| The same sequence, recomposed for portrait | [900×1600 GIF](demo/08-email-9x16.gif) | [9:16 scene](assets/examples/showcase/08-email-9x16.scene.mjs) |
| Paths converge into one result | [1600×900 GIF](demo/background-ribbon-field-motion.gif) | [motion scene](assets/examples/backgrounds/ribbon-field-motion.scene.mjs) |

![Six of the ten available background treatments](demo/backgrounds-new.png)

The [background guide](references/backgrounds.md) explains when each treatment helps and when to reject it. All gallery scenes are editable SVG-based examples; their visible content is illustrative unless cited otherwise.

## Install

Clone the repository and link its root into your agent's skill directory. From the directory where you want to keep the clone:

```bash
git clone https://github.com/GraySilver/explainloop.git
cd explainloop
mkdir -p "$HOME/.codex/skills"
ln -s "$PWD" "$HOME/.codex/skills/explainloop"
```

For Claude Code, link the same folder into `"$HOME/.claude/skills/explainloop"` instead. If that destination already exists, back it up before linking. Restart the agent if it does not discover the new Skill immediately.

Example request:

> Use `explainloop` to turn the section “How routing works” in this article into two 16:9 explanatory GIFs. Keep the same visual style in both, and include editable scene source.

## Render an included scene

Install Node.js 20+, [librsvg](https://wiki.gnome.org/Projects/LibRsvg), and [FFmpeg](https://ffmpeg.org/) so `node`, `rsvg-convert`, `ffmpeg`, and `ffprobe` are on `PATH`. Install a Chinese font if you want to reproduce the Chinese examples; font files are not bundled.

From this repository's root:

```bash
SKILL_ROOT="$PWD"
node "$SKILL_ROOT/scripts/render.mjs" \
  --scene "$SKILL_ROOT/assets/examples/showcase/08-email-16x9.scene.mjs" \
  --out "$PWD/email-demo.gif" --output-size 1600x900
node "$SKILL_ROOT/scripts/inspect.mjs" "$PWD/email-demo.gif"
```

Run the included checks with `node scripts/test.mjs`. The renderer writes temporary frames beside the requested output and removes them after rendering.

## Project structure

```text
explainloop/
  SKILL.md                 Agent instructions
  references/              Content, design, format, and quality guidance
  scripts/                 Scene rendering, preview, inspection, and tests
  assets/examples/         Editable scenes
  assets/icons/            Licensed Lucide subset
  assets/previews/         Background, style, and component previews
  demo/                    Selected public GIFs and an original sample article
```

The repository root is the installable `explainloop` Skill. Its description still names article-to-GIF tasks so agents can discover it accurately.

## License and sources

Original project code, instructions, and example artwork are licensed under [MIT](LICENSE). The bundled Lucide icons retain their [ISC and MIT notices](assets/icons/LICENSE) and [provenance record](assets/icons/PROVENANCE.md). Design references are credited in [sources and licenses](references/sources-and-licenses.md); their artwork is not bundled. Fonts are not redistributed.
