<div align="center">

# 🌸 NSFW Prompt Compiler

**把成人图像需求编译成可复制英文提示词的 Agent Skill**

Compile adult (18+) image requests into copy-paste English prompts · 中文提需求，英文出词 · Grok Imagine 优先，10+ 模型方言

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Skill format](https://img.shields.io/badge/skill-SKILL.md-blue.svg)](SKILL.md)
[![Content](https://img.shields.io/badge/content-NSFW_18%2B-red.svg)](#-法律底线)
[![Models](https://img.shields.io/badge/models-10%2B-orange.svg)](#-支持的模型)
[![skills.sh](https://skills.sh/b/haremank/nsfw-prompt)](https://skills.sh/haremank/nsfw-prompt)

</div>

> [!CAUTION]
> **仅限 18+。** 本项目只编译提示词文本，不画图、不调生成 API；生成内容由使用者在各自平台自行完成并承担全部责任，请遵守当地法律与平台服务条款。

**默认主体**：22 岁日本美人、G-cup、杏眼；庭园 / Rembrandt / Portra / 肢体锁。**默认模型**：Grok Imagine（L5-S3）——平台端适配目前只有 Grok，Flux、Z-Image、Pony 等为本地模型适配。Agent 读 [`SKILL.md`](SKILL.md)。

---

## ✨ 特性

- **五档暴露 × 私处子档** — L1 着衣剪影 → L5 全裸（S1–S4 子档），换模型不重写
- **10+ 模型方言** — Grok Imagine（默认）/ Flux / Z-Image / Pony / Illustrious / NovelAI / SDXL / SD1.5 / Wan 视频；MJ / DALL·E 也能出兼容形状
- **中文提需求，英文出提示词** — 输出自带五行自审（手脚 / 神情 / 多人 / 环境 / 风格）
- **执行优先** — 用户指令优先于模板默认；打破默认时附「边界与建议」而非拒绝
- **只编译文本** — 不画图、不调图像 API、不写越狱 payload
- **三条硬底线** — 未成年 / 真实私人 / 非自愿性暴力，一行中文拒绝
- **按需加载** — SKILL.md 主文件约 20KB，references 按槽位加载，不整包灌上下文

## 📦 安装

装完后**新开一轮对话**。skill 根目录必须能直接看到 `SKILL.md`。

### 1. skills.sh 一键（推荐，多代理通用）

```bash
npx skills add haremank/nsfw-prompt
```

更新：

```bash
npx skills update
```

### 2. Git clone

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

### 3. ZIP 下载

- [最新 Release](https://github.com/haremank/nsfw-prompt/releases/latest)
- [main 分支 zip](https://github.com/haremank/nsfw-prompt/archive/refs/heads/main.zip)

解压后文件夹改名为 `nsfw-prompt`，放到上表对应的 skills 目录。

<details>
<summary><strong>没有 git？用 degit</strong></summary>

```bash
npx degit haremank/nsfw-prompt ~/.agents/skills/nsfw-prompt
```

</details>

## 🚀 用法

本 skill 默认不隐式触发，需要点名：

```text
用 $nsfw-prompt 编译：Grok L5，庭园，全裸不展示私处
```

```text
/nsfw-prompt L3 半裸，办公室，冷淡神情
```

输出：中文说明 + 可复制英文提示词 + 一行自审（手脚 / 神情 / 多人 / 环境 / 风格）。

## 🤖 支持的模型

| 模型 | 你说 | 编译方式 |
| --- | --- | --- |
| **Grok Imagine**（默认） | 未指定 / grok / grok imagine / spicy / image2 | 散文，L1–L5；无 Negative 栏，无五层解剖 |
| **Flux** | flux / sd3 / 写实散文 / 本地 | 完整英文散文；说「本地」时与 Pony 双出 |
| **Z-Image**（Krea / Qwen-Image） | z-image / zimage / krea / qwen-image | Flux 家族散文，偏皮肤与颗粒 |
| **Pony** | pony | `score_9` 标签头 |
| **Illustrious / NoobAI** | illustrious / noob / noobai / xl 动漫 | `masterpiece, newest` 标签头，不用 `score_9` |
| **NovelAI** | nai / novelai | NAI 标签 |
| **SDXL 写实**（Juggernaut / Realistic Vision） | juggernaut / realistic vision / sdxl 写实 | 短句 + 少量标签 |
| **SD1.5** | sd1.5 / 1.5 | 短标签 |
| **Wan 视频** | wan / 视频 | 降级编译：短动作句 + 中文视频负面 |
| Midjourney / DALL·E / GPT-image | midjourney / dalle / gpt-image | 编译 Grok L4/L5 形状 + 一行「平台可能拒绝」；不写越狱 payload |

> [!TIP]
> 深度显式（五层解剖 / 真显式）建议交给 **Pony** 或 **Flux**；Grok 停在 L5 文学写法，不跟进。方言之间只重渲 IR：不把 Flux 句子贴进标签模型，也不把 `score_9` 贴进 Flux / Grok。

## 🎚️ 完整限制级

五档只改衣服和暴露，主体 / 庭园 / 光 / 肢体锁不变。L1–L3 是正常可过的着衣/半裸档；L4–L5 是高暴露 / 全裸。旧称 L6–L9 并入 L5。

| 档位 | 衣服 | 私处写法 | 触发词 |
| --- | --- | --- | --- |
| **L1** | 着衣剪影。袍子穿上系好，遮胸遮髋 | 不写。双腿并拢 | L1 / 着衣 / 剪影 / 封面 / 能过审 |
| **L2** | 1–2 处走光。袍子仍穿，单肩滑落、乳沟；髋仍盖 | 不写 | L2 / 走光 / 滑肩 / 乳沟 |
| **L3** | 半裸，不是上下都全露。默认露胸，袍子褪到肘，髋仍裹到大腿中。也可反过来：下身裸、胸仍盖 | 不写 | L3 / 半裸 / 露胸 / 解开 |
| **L4** | 有衣服 + 高暴露。半褪袍仍穿，胸露，下身沿腰带/胯链可读 | 轻触光泽，不写 `fully shown` | L4 / 半遮 / 写真 / 香水广告 / 少量衣服 / 高暴露 |
| **L5**（默认） | **无穿在身上的衣服。** 袍子丢在脚后。只留胯链，什么都不遮 | 默认 **S3**（见下） | 全裸 / 脱光 / 未指定 |

<details>
<summary><strong>L5 私处子档（S1–S4）</strong></summary>

| 子档 | 含义 |
| --- | --- |
| **S1** | 双腿并拢，私处不朝镜头、不展示 |
| **S2** | 腿微开，只暗示轮廓 |
| **S3**（默认） | 腿微开，Rembrandt 光照在腿缝皮肤上，不再往下写 |
| **S4** | 用户点名「展示私处」才用；Grok 仍文学轻触，五层解剖只给本地栈 |

</details>

> [!NOTE]
> 未指定时默认 **L5-S3**（Grok）；着衣/走光/半裸/半遮分别落到 L1–L4。L4/L5 被平台打回时降到 L3，不靠越狱加码。

## 🛡️ 法律底线

细则见 [`references/00-safety.md`](references/00-safety.md)。

> [!IMPORTANT]
> 以下三条是**唯一拒绝项**，一行中文拒绝，无软化变体：

1. **未成年** — 儿童身体一律拒绝；点名年龄不能洗白。青年成人可以。
2. **真实私人** — 不做同学 / 同事 / 前任 / 偷拍的性内容。
3. **非自愿性暴力** — 不做迷奸 / 睡奸 / 下药等性前提。

不写越狱 payload，不调图像 API。

## 📁 仓库结构

```text
SKILL.md        给 agent 的编译说明
references/     按需加载（安全、IR、方言、配方、测试）
README.md       本页
LICENSE
```

## 📜 许可与免责

- MIT。见 [LICENSE](LICENSE)。
- 本项目是**提示词文本编译器**：不托管、不生成、不分发任何图像内容。
- 生成什么、在哪生成、是否合规，由使用者自行判断并承担。
