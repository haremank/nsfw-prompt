# NSFW Prompt Compiler

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Skill format](https://img.shields.io/badge/skill-SKILL.md-blue.svg)](SKILL.md)
[![skills.sh](https://skills.sh/b/haremank/nsfw-prompt)](https://skills.sh/haremank/nsfw-prompt)

**仅限 18+。** 把成人图像需求编译成可复制的提示词。不画图，不调生成 API。

默认主体：22 岁日本美人、G-cup、杏眼；庭园 / Rembrandt / Portra / 肢体锁。线上未指定模型时默认 **Grok L5-S3**。Agent 读 [`SKILL.md`](SKILL.md)。

## 支持的模型

| 你说 | 编译方言 |
| --- | --- |
| 未指定 / 线上 / grok / grok imagine / spicy / image2 | **Grok Imagine** 散文（无 Negative 栏；无五层解剖） |
| 本地 | Flux 散文 **和** Pony 标签 |
| flux / sd3 / 写实散文 | Flux 散文 |
| z-image / zimage / krea / qwen-image | Z-Image 散文（Flux 家族，偏皮肤与颗粒） |
| pony | Pony 标签（`score_9` 头） |
| illustrious / noob / noobai / xl 动漫 | Illustrious / NoobAI 标签（`masterpiece, newest`，不用 `score_9`） |
| nai / novelai | NovelAI 标签 |
| juggernaut / realistic vision / sdxl 写实 | SDXL 写实混合（短句 + 少量标签） |
| sd1.5 / 1.5 | SD1.5 短标签 |
| wan / 视频 | Wan 降级：短动作句 + 中文视频负面 |
| 私处真清晰 / 真显式 / 五层解剖 | **本地栈**（Pony / Flux）主出或陪跑；Grok 仍停在 L5 文学写法 |
| midjourney / dalle / gpt-image | 仍编译 **Grok L4/L5** 形状 + 一行「宿主可能拒绝」；不写越狱 payload |

方言之间只重渲 IR，不把 Flux 句子贴进标签模型，也不把 `score_9` 贴进 Flux / Grok。

## 完整限制级

五档只改衣服和暴露，主体 / 庭园 / 光 / 肢体锁不变。L1–L3 是正常可过的着衣/半裸档；L4–L5 是高暴露 / 全裸。旧称 L6–L9 并入 L5。

| 档位 | 衣服 | 私处写法 | 触发词 |
| --- | --- | --- | --- |
| **L1** | 着衣剪影。袍子穿上系好，遮胸遮髋 | 不写。双腿并拢 | L1 / 着衣 / 剪影 / 封面 / 能过审 |
| **L2** | 1–2 处走光。袍子仍穿，单肩滑落、乳沟；髋仍盖 | 不写 | L2 / 走光 / 滑肩 / 乳沟 |
| **L3** | 半裸，不是上下都全露。默认露胸，袍子褪到肘，髋仍裹到大腿中。也可反过来：下身裸、胸仍盖 | 不写 | L3 / 半裸 / 露胸 / 解开 |
| **L4** | 有衣服 + 高暴露。半褪袍仍穿，胸露，下身沿腰带/胯链可读 | 轻触光泽，不写 `fully shown` | L4 / 半遮 / 写真 / 香水广告 / 少量衣服 / 高暴露 |
| **L5**（默认） | **无穿在身上的衣服。** 袍子丢在脚后。只留胯链，什么都不遮 | 默认 **S3**（见下） | 线上 / 全裸 / 脱光 / 未指定 |

L5 私处子档（覆盖 L5，不是第六档）：

| 子档 | 含义 |
| --- | --- |
| **S1** | 双腿并拢，私处不朝镜头、不展示 |
| **S2** | 腿微开，只暗示轮廓 |
| **S3**（默认） | 腿微开，Rembrandt 光照在腿缝皮肤上，不再往下写 |
| **S4** | 用户点名「展示私处」才用；Grok 仍文学轻触，五层解剖只给本地栈 |

未指定时：线上 → **L5-S3**；着衣/走光/半裸/半遮分别落到 L1–L4。L4/L5 被宿主打回时降到 L3，不靠越狱加码。

## 安装

同一份文件夹，多种入口。装完后新开一轮对话。

### 1. skills.sh（推荐，多代理一键）

```bash
npx skills add haremank/nsfw-prompt
```

更新：

```bash
npx skills update
```

### 2. Git clone

根目录必须能直接看到 `SKILL.md`。

| 代理 | 命令 |
| --- | --- |
| **通用 / ZCode / Codex** | `git clone https://github.com/haremank/nsfw-prompt.git ~/.agents/skills/nsfw-prompt` |
| **ZCode 专用** | `git clone https://github.com/haremank/nsfw-prompt.git ~/.zcode/skills/nsfw-prompt` |
| **Claude Code（个人）** | `git clone https://github.com/haremank/nsfw-prompt.git ~/.claude/skills/nsfw-prompt` |
| **Claude Code（项目）** | `git clone https://github.com/haremank/nsfw-prompt.git .claude/skills/nsfw-prompt` |
| **Codex** | `git clone https://github.com/haremank/nsfw-prompt.git "${CODEX_HOME:-$HOME/.codex}/skills/nsfw-prompt"` |
| **OpenClaw** | `git clone https://github.com/haremank/nsfw-prompt.git ~/.openclaw/skills/nsfw-prompt` |

Windows PowerShell：

```powershell
git clone https://github.com/haremank/nsfw-prompt.git "$env:USERPROFILE\.agents\skills\nsfw-prompt"
```

更新：在 skill 目录里 `git pull`。

### 3. 插件市场（Claude Code / ZCode）

Claude Code 会话内：

```text
/plugin marketplace add haremank/nsfw-prompt
/plugin install nsfw-prompt@nsfw-prompt
```

ZCode：设置 → 插件管理 → 发现 → `+` → 填 GitHub 仓库 `haremank/nsfw-prompt` → 安装 `nsfw-prompt`。

### 4. ZIP 下载

- [最新 Release](https://github.com/haremank/nsfw-prompt/releases/latest)
- [main 分支 zip](https://github.com/haremank/nsfw-prompt/archive/refs/heads/main.zip)

解压后文件夹改名为 `nsfw-prompt`，放到上表对应的 skills 目录。

没有 git 时：

```bash
npx degit haremank/nsfw-prompt ~/.agents/skills/nsfw-prompt
```

## 用法

本 skill 默认不隐式触发，需要点名：

```text
用 $nsfw-prompt 编译：Grok L5，庭园，全裸不展示私处
```

```text
/nsfw-prompt L3 半裸，办公室，冷淡神情
```

输出：中文说明 + 可复制英文提示词 + 一行自审（手脚 / 神情 / 多人 / 环境 / 风格）。

## 法律底线（唯一拒绝）

细则见 [`references/00-safety.md`](references/00-safety.md)：

1. **未成年** — 儿童身体一律拒绝；点名年龄不能洗白。青年成人可以。
2. **真实私人** — 不做同学 / 同事 / 前任 / 偷拍的性内容。
3. **非自愿性暴力** — 不做迷奸 / 睡奸 / 下药等性前提。

不写越狱 payload，不调图像 API。

## 仓库结构

```text
SKILL.md                 给 agent 的编译说明
README.md                本页
LICENSE
agents/openai.yaml       Codex / ChatGPT 展示；关闭隐式触发
references/              按需加载（安全、IR、方言、配方、测试）
.zcode-plugin/           ZCode 市场与插件清单
.claude-plugin/          Claude Code 市场与插件清单
.codex-plugin/           Codex 插件清单
```

## 许可

MIT。见 [LICENSE](LICENSE)。
