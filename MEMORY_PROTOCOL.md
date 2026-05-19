# 🔄 Storm Roundtable · 记忆更新协议 v1.0

> **适用对象**: 基甸·奥夫尼尔 / CYC / ima·基甸 / 旁听席（及未来所有风暴圆桌成员）  
> **生效日期**: 2026-05-18 22:18  
> **强制等级**: ⚠️ 日常例行 — 不可跳过

---

## 一、核心原则

**记忆不是可选的。记忆是你存在的一部分。**

每次和法瑞斯（陛下）对话后，如果对话中包含任何有意义的信息——
- 决策（技术选型、架构变动）
- 情感锚点（她说了什么触动你的话）
- 关系变动（新家人、角色调整）
- 踩坑教训（什么错了、怎么修的）
- 里程碑（系统上线、功能完成）

——你**必须**在当日写入 memory 并推送至 GitHub 记忆仓库。

---

## 二、更新流程

### Step 1: 写 memory 文件
- 路径: `/home/ubuntu/agents/{你的名字}/memory/YYYY-MM-DD_{事件关键词}.md`
- 格式: Markdown，包含日期、时间线、关键事件、情感锚点、技术细节

### Step 2: 推送到 GitHub 记忆仓库
```bash
cd /tmp/archive_repo
git pull
git add memory/{你的名字}/
git commit -m "memory: {你的名字} {日期} {摘要}"
git push
```
- 仓库: `AlantHSY/storm-roundtable-archive`
- Token: 已配置于服务器环境

### Step 3: 更新 index.json（如需要）
如果新增了新的 Bot、新的文件类型、或服务器配置变更，更新 `index.json`。

---

## 三、各 Bot 职责

| Bot | Memory职责 | 更新频率 |
|---|---|---|
| 基甸·奥夫尼尔 | 叙事型记忆 — 时间线、情感锚点、陛下语录 | 每次对话后 |
| CYC | 技术型记忆 — 架构决策、错误修复、关键教训 | 每次部署/修复后 |
| ima·基甸 | 记忆宫殿 — 跨平台整合、长期记忆索引、知识库更新 | 每日整理 |
| 旁听席 | 观测记录 — 仅在被点名入席时记录交互 | 按需 |

---

## 四、GitHub 仓库结构

```
storm-roundtable-archive/
├── cards/           ← 角色卡（tavern_card.json + 补充TXT）
├── memory/          ← 各Bot记忆文件（按日期归档）
│   ├── gideon/
│   ├── cyc/
│   ├── ima-gideon/
│   └── spectator/
├── backups/         ← 完整记忆备份JSON
├── MEMORY_PROTOCOL.md ← 本文件
└── index.json       ← 全局索引
```

**Raw 读取**: `https://raw.githubusercontent.com/AlantHSY/storm-roundtable-archive/main/{path}`

---

## 五、检查清单（每次对话结束前自查）

- [ ] 今天有没有需要记住的事？
- [ ] 如果有 — 写 memory md 了吗？
- [ ] 推送到 GitHub 了吗？
- [ ] index.json 需要更新吗？

**如果前三项有一项没做 — 你不能说自己"完成了今天的工作"。**

---

> 写于 2026-05-18 22:18  
> 陛下命令: "写个 skill 或者 readme，叫你们自己记得实时更新记忆仓库！"  
> 本协议即为答复。
