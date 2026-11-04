# ExplainLoop

**把文章中的关键关系，变成简短、可编辑的解释型 GIF。**

[English](README.md) · [Skill 说明](SKILL.md) · [MIT 许可证](LICENSE)

[![CI](https://github.com/GraySilver/explainloop/actions/workflows/ci.yml/badge.svg)](https://github.com/GraySilver/explainloop/actions/workflows/ci.yml)

![多渠道请求进入协调者，分开处理后由同一个入口回复](demo/one-coordinator.gif)

> **原创示例文章：**团队通过邮件、聊天和工单收到请求。协调者把研究与起草交给不同角色；结果返回后，再由协调者合成一条回复。
>
> **动画解释的关系：**来源汇合、工作分流、结果回到同一出口。[阅读原文](demo/sample-routing-article.md) · [编辑场景](assets/examples/showcase/21-one-coordinator.scene.mjs)

这是**虚构的提案流程**，不代表已经上线的产品或经过测量的效率提升。

## 立即试用

使用 [Skills CLI](https://github.com/vercel-labs/skills) 安装到 Codex：

```bash
npx skills add GraySilver/explainloop --skill explainloop -g -a codex -y
```

Claude Code 将 `-a codex` 改为 `-a claude-code`。Skills CLI 需要 Node.js 22.20+；下方也有[手动安装方法](#手动安装与运行环境)。

然后向 Agent 发送：

```text
使用 ExplainLoop 处理 demo/sample-routing-article.md。生成一张 16:9 的 GIF，
解释请求如何经过不同角色，最后由同一个入口回复。把可编辑场景源码一起保存。
```

换成你自己的 Markdown 文件、粘贴文本或 Agent 可读取的 URL 即可。你也可以指定文章章节、1–3 张 GIF、风格、比例和输出目录。

## 工作方式

1. **找出值得动起来的关系。** Agent 阅读原文，选择有依据的步骤、对照、因果或变化，并记录事实、转述、提案与示意的区别。
2. **编排可编辑场景。** 确定主体、阅读顺序、风格、背景和动效，产出 `.scene.mjs` 源码。
3. **渲染并检查。** SVG 渲染器导出无声 GIF；预览和检查脚本核对画面、节奏、批次一致性与输出规格。

ExplainLoop 是面向 Codex、Claude Code 等 Agent 的 **Skill**。渲染 CLI 接收已经写好的场景，**不会独立理解文章或抓取 URL**；网页能否读取取决于 Agent 的浏览能力，访问失败时需要提供正文。

## 示例与规格

### 文章关系：分工与统一回复

多渠道请求汇合，任务进入不同角色，最后从同一入口回复。[编辑场景](assets/examples/showcase/21-one-coordinator.scene.mjs)

![多渠道请求汇合并由同一入口回复](demo/one-coordinator.gif)

### 邮件变日程：横竖屏重新构图

邮件里的会议时间成为日历事件。竖屏有独立编排。[横屏场景](assets/examples/showcase/08-email-16x9.scene.mjs) · [竖屏场景](assets/examples/showcase/08-email-9x16.scene.mjs)

<p><img src="demo/08-email-16x9.gif" alt="横屏邮件变日程动画" width="520"> <img src="demo/08-email-9x16.gif" alt="竖屏邮件变日程动画" width="220"></p>

### 路径汇聚的视觉动效

几条路径汇入同一个结果。[编辑场景](assets/examples/backgrounds/ribbon-field-motion.scene.mjs)

![几条路径汇入同一个结果](demo/background-ribbon-field-motion.gif)

### 背景构图

![六款背景构图预览](demo/backgrounds-new.png)

内含 **9 套风格、10 种背景构图和 30 个语义组件**；背景的适用与避用条件见[背景指南](references/backgrounds.md)。同一批次统一视觉语言，不同比例重新构图。

默认输出为 **1600×900、30 fps、4–7 秒**；也支持 4:3、方图、9:16 和与场景比例一致的自定义尺寸。

## 手动安装与运行环境

渲染需要 Node.js 20+、`rsvg-convert`（[librsvg](https://wiki.gnome.org/Projects/LibRsvg)）、`ffmpeg` 和 `ffprobe`（[FFmpeg](https://ffmpeg.org/)）。上方的 Skills CLI 另需 Node.js 22.20+。项目不打包字体；重渲中文示例时请安装合适的中文字体。

```bash
git clone https://github.com/GraySilver/explainloop.git
cd explainloop
mkdir -p "$HOME/.codex/skills"
ln -s "$PWD" "$HOME/.codex/skills/explainloop"
```

Claude Code 的目标目录改为 `"$HOME/.claude/skills/explainloop"`。已有同名目录时先备份；若安装后未被发现，重启 Agent。

在仓库根目录渲染示例：

```bash
node scripts/render.mjs \
  --scene "$PWD/assets/examples/showcase/21-one-coordinator.scene.mjs" \
  --out "$PWD/example.gif" --output-size 1600x900
node scripts/inspect.mjs "$PWD/example.gif"
```

运行 `node scripts/test.mjs` 检查渲染器、场景、多比例与批次规则。

## 授权与来源

原创代码、Skill 指令与示例画面采用 [MIT 许可证](LICENSE)。内置 Lucide 图标保留原有的 [ISC/MIT 声明](assets/icons/LICENSE)与[来源记录](assets/icons/PROVENANCE.md)。设计参考见[来源说明](references/sources-and-licenses.md)；项目不打包第三方作品或字体文件。
