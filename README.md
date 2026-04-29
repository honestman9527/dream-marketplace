# dream-marketplace

`dream-marketplace` 是个人 Claude Code 插件市场路由仓库。这个仓库只维护 marketplace 索引，不再存放插件本体；每个插件放在一个独立仓库中，便于版本管理、安装和后续扩展。

## 在线安装

添加个人 marketplace：

```powershell
claude plugin marketplace add honestman9527/dream-marketplace
```

安装 Novel Studio：

```powershell
claude plugin install ns@dream-marketplace
```

在 Claude Code 交互界面中也可以使用：

```text
/plugin marketplace add honestman9527/dream-marketplace
/plugin install ns@dream-marketplace
/reload-plugins
```

## 当前插件

| 插件 | 独立仓库 | 用途 | 安装名 |
| --- | --- | --- | --- |
| NS | `honestman9527/novel-studio` | 小说创作工作室，支持多小说项目、长期记忆、脑暴、设定、大纲、正文、调研和插画提示词 | `ns@dream-marketplace` |

NS 安装后可用的 Claude Code 技能入口：

```text
/ns:ns
/ns:ns-brainstorm
/ns:ns-memory
/ns:ns-architect
/ns:ns-research
/ns:ns-draft
/ns:ns-illustration
```

## 维护方式

新增插件时：

1. 为插件创建独立仓库，例如 `honestman9527/plugin-name`。
2. 在插件仓库根目录放置 `.claude-plugin/plugin.json`。
3. 在本仓库的 `.claude-plugin/marketplace.json` 中新增一条 `plugins[]` 记录，`source` 指向插件独立仓库：

```json
{
  "name": "plugin-name",
  "source": {
    "source": "github",
    "repo": "honestman9527/plugin-name"
  },
  "description": "Short plugin description"
}
```

4. 运行校验：

```powershell
claude plugin validate .
```

5. 提交并推送本仓库。用户可通过下面命令刷新 marketplace：

```powershell
claude plugin marketplace update dream-marketplace
```

## 仓库结构

```text
dream-marketplace/
  .claude-plugin/
    marketplace.json
  README.md
```
