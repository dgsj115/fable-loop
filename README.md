# fable-loop

用寓言讲清一个概念，然后**必须考你**是否真懂。

> A Claude Code skill that explains a concept through a fable — then makes you prove you understood it.

## 为什么还要有第六个寓言 skill

生成寓言这件事已经有人做过了，而且不止一遍（`fable-explainer`、`concept-fable`、`studyzy/Fable`、`aeopress/writing-skills.TW` …）。这个 skill **不做那部分**，它直接沿用 Amanda Askell 的原版 prompt，一个字没改。

它加的是后半段，也是没人做的那段：

那些 skill 全都停在"输出故事"就结束了。没人问你到底懂了没有。而寓言这类东西有个众所周知的风险——**你觉得你懂了，其实映射错了，而且你不会发现**。

fable-loop 把这件事变成闭环：

1. **强制复述** — 讲完停下来，问你"这故事在讲什么"，等回答。不许自问自答。
2. **映射偏差诊断** — 拿故事-概念映射表逐条判 ✅/❌/⚠️，具体到哪个人物映射错了，而不是笼统说"理解得不错"。
3. **答不上来就补台阶** — 唯一一个**失败之后有下文**的。诊断失败时不重述答案，而是先分清是"故事没看懂"还是"故事看懂了但接不上概念"，然后把那一跳拆成小台阶，配一张故事↔代码逐句对照表，最后出一道新题验收。
4. **喻体台账** — 记录每个概念用过的喻体和你的复述结果。同一个概念第二次讲必须换喻体，不能拿"地图=过拟合"糊你第二遍。
5. **反向复习** — 只给旧寓言，让你说出概念。优先挑你上次答错的。

第 1 步是全部意义所在。跳过它，这就是第六个寓言生成器。

## 安装

```bash
git clone https://github.com/dgsj115/fable-loop.git ~/.claude/skills/fable-loop
```

零依赖，零脚本，纯 SKILL.md。

## 用法

```
/fable-loop 用寓言讲讲死锁
/fable-loop 计算机网络
/fable-loop 考我
```

## 台账

学习记录写在 skill 目录下的 `fables.md`。该文件已在 `.gitignore` 中，不会进仓库——pull 不会冲突，你的学习记录也不会被公开。

## 难度锚点

默认**大一零基础**。要研究生水平的硬核概念，说一声"研究生水平"即可。

## 致谢

寓言生成部分的 prompt 来自 Anthropic 研究员 **Amanda Askell** 公开分享的版本，版权归她。本仓库只做流程编排，与 Anthropic 无隶属关系。

## License

MIT
