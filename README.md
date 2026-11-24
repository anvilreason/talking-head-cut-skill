# 口播精剪 Skill（Talking-Head Cut Skill）

> **把 AI 剪口播从“能看但充满机械感”拉到“直接可发的高留存成片水准”。**
>
> 一套经过大量真实竖屏口播 A/B 波形实测打磨的 AI 剪辑工作流 Skill——覆盖**波形级呼吸感气口精剪**、**自然中文整句字幕**、**手机端防遮挡安全区**与**高密度交互 MG 动效**。开箱即用，直接复制即可赋能 ChatCut、Claude Code、Codex、Cursor 或任意 AI 剪辑 Agent。

![Version](https://img.shields.io/badge/version-v4.1.0-black)
![License](https://img.shields.io/badge/license-MIT-blue)
![Format](https://img.shields.io/badge/format-Agent%20Skill%20(SKILL.md)-green)

---

## 为什么需要这个 Skill？

大多数人用 AI 剪口播，剪完还是忍不住拖回剪映手动补几十刀，核心原因只有 4 个：
1. **气口发松又机械**：长停顿切了，但句间 `300ms - 650ms` 换气口没切净；或者盲信 ASR 时间戳一刀切下去，把字头吞了。
2. **口癖与废话不敢下手**：“呃、就是、然后你才能够”和过渡套话全留着，观众前 3 秒就划走。
3. **字幕碎片化**：一句话没说完强行切 2 到 3 个字，专有名词错一堆。
4. **MG 动效踩坑**：一上来全铺文字剧透、用假图标敷衍，或者把标题和评分条顶在屏幕最上方——一发到手机上，**直接被状态栏和抖音右上角搜索放大镜盖得严严实实**。

**`talking-head-cut-skill` 就是把专业人工精剪的隐性经验，全部拆解成 AI 听得懂、能严格执行的量化标准。**

---

## 核心能力一览

| 模块 | 你能直接拿走什么标准 |
| :--- | :--- |
| **1. 三段式防翻车闭环** | 强制按「`口播精剪复核` → `整句字幕与视觉规划` → `批量做 MG 与 SFX + 逐帧验收`」推进，拒绝 AI 瞎改一通全返工 |
| **2. 波形级呼吸感气口精剪** | `1.15x - 1.20x` 黄金语速、`80% - 88%` 有效发声密度、开场 `120ms` 零等待、常规句间 `110ms - 130ms`、全片 6 到 10 处 `310ms - 410ms` 戏剧呼吸，清零 `>= 500ms` 死空白，剪接点淡入 `<= 1 帧` 防吞字消音 |
| **3. 自然中文整句字幕** | 严格按中文语义意群整句断句（杜绝半句截断）、`1080×1920` 竖屏 `40px` 单行清晰规格、专有名词 100% 纠错 |
| **4. 手机端安全区 + 高留存 MG** | **竖屏顶部 `y = 0 - 260px` 绝对留空**（完整避开状态栏与右上角搜索图标）、真实官方 Logo、全程露脸透明悬浮、严格「说到哪词才跳哪词」、红黑榜强视觉区分、累积评分 HUD、`1.2 - 1.8 秒` 利落掉血条、`-14 dB` 到 `-16 dB` 关键提示音 SFX |

---

## 30 秒直接复制使用

### 方式一：直接复制 `SKILL.md`（最快，适合所有 AI 工具）

1. 打开本仓库根目录的 [`SKILL.md`](./SKILL.md)（或点开 [Raw 纯文本链接](https://raw.githubusercontent.com/anvilreason/talking-head-cut-skill/main/SKILL.md)）。
2. 全选复制，直接粘贴给 **ChatCut**（保存为你的 Workflow Skill）或任意支持 System Prompt / Skill 的 AI 剪辑 Agent。
3. 以后剪口播时直接说：**“按 `talking-head-cut` Skill 帮我精剪这条口播并做全片动效”**。

### 方式二：一行命令安装到本地 Agent Skills 目录（适合 Claude Code / Codex / Antigravity / Cursor）

```bash
git clone https://github.com/anvilreason/talking-head-cut-skill.git ~/.claude/skills/talking-head-cut
```

或使用 `curl` 仅拉取核心 `SKILL.md`：

```bash
mkdir -p ~/.claude/skills/talking-head-cut && \
curl -fsSL https://raw.githubusercontent.com/anvilreason/talking-head-cut-skill/main/SKILL.md \
  -o ~/.claude/skills/talking-head-cut/SKILL.md
```

### 方式三：导入到 ChatCut 作为可复用 Workflow Skill

1. 克隆本仓库到本地，或复制 [`SKILL.md`](./SKILL.md) 全文。
2. 在 ChatCut 对话中告诉 Agent：
   > “帮我把这份 `SKILL.md` 保存为我的 ChatCut Workflow Skill，名字叫 `口播精剪 Skill`。”
3. 保存后，在任意新项目中直接调用即可。

---

## 仓库目录结构

```text
talking-head-cut-skill/
├── SKILL.md                                 # 核心 Skill 指令文件（可直接复制/导入）
├── references/
│   ├── pacing-and-waveform-guide.md         # 7 条气口量化黄金法则 & 4 大 AI 剪辑病灶对照
│   └── mobile-safe-zone-and-mg.md           # 1080×1920 竖屏防遮挡安全区蓝图 & 逐帧验收清单
├── CHANGELOG.md                             # 完整版本迭代日志（v2.0 → v4.1）
├── README.md                                # 使用说明
└── LICENSE                                  # MIT 开源协议
```

---

## 迭代记录

查看完整演进过程与每次升级细节，请阅读 [`CHANGELOG.md`](./CHANGELOG.md)。

- **`v4.1.0`**：新增抖音真机实测 `1080×1920` 竖屏顶部 `y = 0 - 260px` 防遮挡安全区红线，打包公开发布标准 Skill。
- **`v4.0.0`**：新增三段式人工确认闭环、自然中文整句字幕铁律、高留存 MG 动效规范与 SFX 提示音标准。
- **`v3.0.0`**：升级 `1.15x - 1.20x` 语速与呼吸感模型、波形级防吞字底线与语义二次瘦身法则。
- **`v2.0.0`**：首版 1000Hz 波形对齐实测，沉淀 7 条气口剪辑量化黄金法则。

---

## License

MIT License — 欢迎自由复制、修改并在你的视频工作流中直接使用。如果对你有帮助，欢迎点一个 Star。
