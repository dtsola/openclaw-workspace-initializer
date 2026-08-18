## 配置修改规范（多 agent 共享配置安全）

多 agent 共享同一份 openclaw.json（所有 agent 定义都在 agents.list 里），互相覆盖风险高：

- ✅ 改配置一律用 gateway `config.patch`（部分合并，只动指定字段）
- ❌ 禁止使用 gateway `config.apply`（全量替换：会用自己会话的旧配置快照整份写回，抹掉其他 agent 的修改）
- 背景：多个 agent 共享单份 openclaw.json，apply = 谁后写谁赢；openclaw.json.bak* 备份就是 apply 全量写入留下的痕迹
- 例外：仅初始化 / 整体迁移等场景才考虑 apply
