# content-pipeline-skill

<<<<<<< HEAD
**English:** [README.en.md](./README.en.md)

---

=======
>>>>>>> origin/docs/bilingual-readme
单文件 Claude Code Skill：用 **`/pipeline` 命令族** 驱动 **Research → Ideate → Write → Queue** 四阶段，把选题做成带研究文件、钩子角、正文草稿与 `content-queue.json` 状态机的可审队列（流程与数据模型见 `SKILL.md`）。

## When to use

- 创作**原创**内容且需要调研、选角度、从零起草并进入审阅队列（与 `SKILL.md` frontmatter `when_to_use` 及「Use pipeline」小节一致）。
- 需要从话题或 URL 出发，生成 `research/YYYYMMDD-{slug}.md`（或 URL 分支跳过 Stage 1 但仍进入后续阶段），再写入队列。
- 要维护 `content-queue.json` 中的 `seed → researched → drafted → approved → published → archived` 生命周期，并用 `/pipeline status|review|approve|adapt|publish|clean` 管理。

## When NOT to use

- **已有素材**、只需直接写作或轻改的场景：`SKILL.md`「Don't use pipeline」列出——引用他人帖子、回复评论、润色现稿；明确说明这些会「浪费 4–5x token 且无收益」。
- 不需要研究 / 角度生成 / 队列入库，只要一次性短文输出时，不必走完整管线命令。
- 无法提供 `SKILL.md` 约定的 `./content-queue.json` 与 `./research/` 路径（或等价项目布局）时，应先调整项目结构再启用技能。

## Quick Start

1. 将 `SKILL.md` 安装到 `~/.claude/skills/content-pipeline/`（或项目 `.claude/skills/`）。
2. 在仓库根准备 `./content-queue.json` 与 `./research/`（初始空队列可参考 `SKILL.md` 内 JSON 样例）。
3. 使用 `trigger` 字段所示 **`/pipeline …`** 命令启动各子流程；参数解析规则见 `SKILL.md` Commands 表。

## 典型场景

- 「从 Twitter / Web 调研 → 选最高分 hook → 产出 thread 草稿 → 入队待审」。
- 先用 `/pipeline seed` 收集灵感，再对高优先级条目跑完整 `/pipeline <topic>`。
- 已发布条目用 `/pipeline clean` 将 30 天前 `published` 项归档（逻辑见 `SKILL.md`）。

## 仓库结构（贡献者）

| 路径 | 说明 |
|------|------|
| `SKILL.md` | 全部命令、队列字段、阶段细节与设计原则；修改行为仅改此文件。 |
| `LICENSE` | 许可证。 |
