# Public design references and asset provenance

Research sources inform original style recipes and component behavior; they are not templates to trace or rebrand.

- [Carbon Motion](https://www.carbondesignsystem.com/building-blocks/foundations/motion/overview): productive and expressive motion, easing, focus.
- [Carbon Typography](https://www.carbondesignsystem.com/building-blocks/foundations/typography/overview): type scale and hierarchy for reading context.
- [Carbon Spacing](https://www.carbondesignsystem.com/building-blocks/foundations/spacing/overview): consistent spacing rhythm within and between components.
- [Carbon Data Visualization](https://www.carbondesignsystem.com/building-blocks/data-visualization/overview): chart-family choice for comparisons, flows, and measured data.
- [Material Motion](https://m2.material.io/design/motion/understanding-motion/): show relationships, feedback, and outcomes through movement.
- [Apple Motion](https://developer.apple.com/design/human-interface-guidelines/motion): purposeful, brief motion and state communication.
- [Datawrapper chart typography](https://www.datawrapper.de/blog/text-in-data-visualizations): direct labels, units, annotations, and efficient eye travel.
- [WCAG 2.2 text contrast](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum) and [non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast): minimum contrast for text and essential graphic elements.
- [Fluent Design Tokens](https://fluent2.microsoft.design/design-tokens/): semantic separation of colors, typography, spacing, and motion.
- [Fluent Iconography](https://fluent2.microsoft.design/iconography/): semantic icon size and use.

The scene-brief and anti-template checks in `references/design-directions.md` adapt ideas from [Anthropic's frontend-design skill](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md) and [Impeccable's craft floor](https://github.com/pbakaus/impeccable/blob/main/skill/reference/craft-floor.md). The family-selection table is informed by the searchable, use-case-first structure of [UI/UX Pro Max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill/blob/main/.claude/skills/ui-ux-pro-max/SKILL.md). All guidance here is written for this GIF workflow; no upstream skill text, scripts, style data, or screenshots are bundled. The upstream skill repositories currently publish [Apache-2.0](https://github.com/anthropics/skills/blob/main/skills/frontend-design/LICENSE.txt), [Apache-2.0](https://github.com/pbakaus/impeccable/blob/main/LICENSE), and [MIT](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill/blob/main/LICENSE) licenses respectively. Recheck upstream licenses before copying any future assets or code.

Bundled icon SVGs are selected from [Lucide](https://lucide.dev/license), package `lucide-static` version 1.67.0, under ISC (a small inherited Feather subset is MIT). Preserve `assets/icons/LICENSE` and `assets/icons/PROVENANCE.md` when copying or distributing the skill. Do not copy a brand logo from an icon pack as if it were a generic UI element.

Optional external illustration sources, fetched only when a scene needs one and after checking its current license:

- [Open Doodles](https://www.opendoodles.com/about) says its illustrations are CC0.
- [Open Peeps](https://www.openpeeps.com/) says its library is CC0.

When using an external asset, record its URL, license, retrieval date, and whether it was modified alongside the scene source. Prefer user-provided assets for depictions of specific people, products, places, or events. A public style guide does not grant rights to an article's images or screenshots.
