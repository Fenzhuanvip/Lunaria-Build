# Lunaria-Build

私人内部 CI 构建控制面，仅用于 Fenzhuanvip/Lunaria 私有仓库的 HarmonyOS HAP 构建与构件发布。

## 项目性质
- 私人项目，仅内部构建，不对外发布或开源分发；
- 构建产物通过 publish-private 动作上传至私有仓库 Release；
- CI 运行记录保留由 GitHub Actions 仓库级保留策略（retention days）管理。

## 工作流说明
| 工作流 | 用途 |
|--------|------|
| build.yml | 构建 HarmonyOS HAP，下载命令行工具并做 SHA256 哈希校验 |
| run.yml | 执行预置命令白名单（已移除任意 shell 执行） |
| cleanup.yml | 构建完成后提示，不再主动删除 CI 运行记录 |

## 安全建议
- GH_PAT 建议使用细粒度 PAT，仅赋予 `Fenzhuanvip/Lunaria` 仓库 `Contents: read` 权限；
- build.yml 中 `CLT_SHA256` 需替换为实际下载包的 SHA256 哈希值；
- run.yml 的命令白名单如需扩展，请通过仓库 PR 修改。
