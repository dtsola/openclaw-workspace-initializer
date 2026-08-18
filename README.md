# OpenClaw Workspace Initializer 🏠

> 给每个 OpenClaw agent 一个「家」：标准目录结构 + WORKSPACE.md 规范 + 多 agent 配置安全。
> OpenClaw workspace initialization & standardization — the agent home your agents deserve.

![license](https://img.shields.io/badge/license-MIT-green)

## 为什么需要它

OpenClaw agent 每次会话都是全新启动。没有工作区规范，你的 agent 会：
- ❌ 把文件乱扔在根目录，越攒越乱
- ❌ 忘记自己的记忆系统（`memory/`），每次醒来都失忆
- ❌ 在多 agent 共享配置时，用 `config.apply` 整份覆盖 openclaw.json，**抹掉其他 agent 的修改**

这个 skill 一次性解决：**目录结构 + 持久化规范 + 配置安全**。

## 安装

```bash
# ClawHub（推荐）
clawhub install openclaw-workspace-initializer

# 或从 GitHub 手动安装
git clone https://github.com/<your-name>/openclaw-workspace-initializer
# 把 SKILL.md 和 templates/ 放到你的 skills 目录
```

## 使用

1. 把 skill 放到 OpenClaw 的 skills 目录
2. 首次进入（或重置）一个工作区时，agent 会自动：
   - 创建 `projects/ tasks/ outputs/ knowledge/ scripts/ memory/ tmp/`
   - 写入 `WORKSPACE.md` 目录规范（重启后依然生效）
   - 检测多 agent 场景，把「config.patch ✅ / config.apply ❌」安全规范持久化进 `AGENTS.md`
   - 在 `memory/` 记录初始化日志

## 与其他方案的区别

| | openclaw-workspace-starter | **openclaw-workspace-initializer** |
|---|---|---|
| 目录结构 | 基础模板 | 完整规范体系（7 目录 + 命名规范 + 行为规则） |
| 持久化规范 | 无 WORKSPACE.md 规范 | ✅ WORKSPACE.md 重启后持续生效 |
| 多 agent 配置安全 | ❌ | ✅ config.patch / 禁 config.apply（实战踩坑沉淀） |
| 模板独立 | 内嵌 | ✅ templates/ 可单独复用 |

**实战验证**：本规范来自 7 个 agent 共享单份 openclaw.json 的真实生产环境，`config.apply` 覆盖事故（openclaw.json.bak* 痕迹）是血泪教训。

## 目录结构

```
openclaw-workspace-initializer/
├── SKILL.md                    # 技能主体（工作流 Step 1-5）
├── templates/
│   ├── WORKSPACE.md            # 目录规范模板
│   └── AGENTS-config-safety.md # 多 agent 配置安全规范
├── README.md
└── LICENSE
```

## License

MIT — 随便用，署名可选。

---

**需要定制？** OpenClaw 多 agent 部署 / 工作区规范化 / agent 记忆系统搭建，欢迎联系：[你的联系方式]
