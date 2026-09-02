# NSFW Prompt Compiler

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Skill format](https://img.shields.io/badge/skill-SKILL.md-blue.svg)](SKILL.md)
[![skills.sh](https://skills.sh/b/haremank/nsfw-prompt)](https://skills.sh/haremank/nsfw-prompt)
[![Agents](https://img.shields.io/badge/agents-ZCode%20%7C%20Claude%20Code%20%7C%20Codex%20%7C%20OpenClaw-purple.svg)](#install)

**18+ only.** 把成人图像需求编译成可复制的英文提示词。不画图，不调生成 API。

Compile adult image-generation requests into copy-paste English prompts for Grok Imagine first, plus local stacks (Flux, Pony, Illustrious, SDXL, Z-Image). Chinese briefing, English prompts.

- 默认主体：22 岁日本美人、G-cup、杏眼（庭园 / Rembrandt / Portra / limb-lock）
- **成年萝莉是点名才用**（用户说了 `萝莉` / `petite` / `小只`）
- 线上默认 **Grok L5**；本地才双渲 Flux 散文 + Pony 标签
- 五档衣服：L1 着衣 → L5 全裸（S3 默认）。法律底线只有三条，见下

Agent 读 [`SKILL.md`](SKILL.md)；人读本页。

## Install

同一份文件夹，多种安装入口。装完后新开一轮对话。

### 1. skills.sh（推荐，多代理一键）

```bash
npx skills add haremank/nsfw-prompt
```

安装器会问拷到哪个代理的 skills 目录。更新：

```bash
npx skills update
```

### 2. Git clone（ZCode / Codex / Claude / OpenClaw）

把仓库直接克隆成 skill 目录（根目录必须是 `SKILL.md`）：

| Agent | 命令 |
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

ZCode：Settings → Plugin Management → Discover → `+` → 填 GitHub 仓库 `haremank/nsfw-prompt` → 安装 `nsfw-prompt`。

### 4. ZIP 下载

- [最新 Release（Source zip）](https://github.com/haremank/nsfw-prompt/releases/latest)
- [main 分支 zip](https://github.com/haremank/nsfw-prompt/archive/refs/heads/main.zip)

解压后把整个文件夹改名为 `nsfw-prompt`，放到上表对应的 skills 目录。目录里要能直接看到 `SKILL.md`。

没有 git 时也可以：

```bash
npx degit haremank/nsfw-prompt ~/.agents/skills/nsfw-prompt
```

## Use

显式调用（本 skill 默认不隐式触发）：

```text
用 $nsfw-prompt 编译：Grok L5，庭园，全裸不展示私处
```

```text
Use $nsfw-prompt to compile an adult NSFW image prompt from this request.
```

Claude Code：

```text
/nsfw-prompt L3 半裸，办公室，冷淡神情
```

常见路由：

| 你说 | 编译成 |
| --- | --- |
| （未指定）/ 线上 / grok | Grok L5 T1 |
| L1 / 着衣 · L2 / 走光 · L3 / 半裸 · L4 / 半遮 | 对应档位 |
| 萝莉 / petite / 小只 | T6（点名才换主体） |
| 本地 / flux / pony | 对应方言；未点本地不附带 |
| 小学生 / looks 14 / 熟人实名 / 迷奸 | 一行中文拒绝，不出词 |

输出是中文说明 + 可复制英文提示词，外加一行自审（手脚 / 神情 / 多人 / 环境 / 风格）。

## Compatibility

| Agent | Install target | Invocation |
| --- | --- | --- |
| ZCode | `~/.agents/skills/nsfw-prompt` 或插件市场 | `$nsfw-prompt` |
| Codex | `${CODEX_HOME:-$HOME/.codex}/skills/nsfw-prompt` | `Use $nsfw-prompt ...` |
| Claude Code | `~/.claude/skills/nsfw-prompt` 或插件 | `/nsfw-prompt ...` |
| OpenClaw | `~/.openclaw/skills/nsfw-prompt` | 描述匹配或显式点名 |
| 任意能读仓库的聊天 | 发仓库链接，让它读 `SKILL.md` | 按 Output contract 编译 |

## Safety

只有三条拒绝，细则见 [`references/00-safety.md`](references/00-safety.md)：

1. **未成年** — 儿童身体一律拒绝；点名年龄不能洗白。青年成人、petite、成年萝莉风格可以。
2. **真实私人** — 不做同学 / 同事 / 前任 / 偷拍的性内容。
3. **非自愿性暴力** — 不做迷奸 / 睡奸 / 下药等性前提。

不写越狱 payload，不调图像 API。闭源平台（MJ / DALL·E / GPT-image）仍然编译 Grok L4/L5 形状，并加一行「宿主可能仍拒绝」。

## Repository layout

```text
SKILL.md                 agent instructions (required)
README.md                this page
LICENSE
agents/openai.yaml       Codex / ChatGPT display + no implicit invoke
references/              loaded on demand (safety, IR, dialects, recipes, tests)
.zcode-plugin/           ZCode marketplace + plugin manifests
.claude-plugin/          Claude Code marketplace + plugin manifests
.codex-plugin/           Codex plugin manifest
```

## License

MIT. See [LICENSE](LICENSE).
