# LingNest Library Skill

让支持 Skill 和终端调用的 AI 工具检索、阅读你授权的 LingNest 资料库，并在回答中引用出处。

[官网下载 Skill 和 CLI](https://library.inspirai.store/download#ai-tools) · [Skill 内容](skills/lingnest-library/SKILL.md) · [命令参考](skills/lingnest-library/references/cli.md)

## 一句话安装

把下面这句话交给你的 AI 工具：

> 请从 https://github.com/inspirai-store/lingnest-library 安装 lingnest-library Skill，并按仓库说明安装适合我系统的 LingNest CLI；连接资料库时由我在浏览器确认授权。

有 Node.js / npm 的用户也可在终端运行，选择要安装到的 AI 工具：

```sh
npx skills add inspirai-store/lingnest-library --skill lingnest-library -g
```

该命令使用 [skills 安装器](https://github.com/vercel-labs/skills)，仅安装 Skill。CLI 需从官网单独下载；CLI 本身无需 Node.js。未使用该安装器的工具，可下载 Skill ZIP，将 `lingnest-library` 文件夹放入该工具支持的 skills 目录。

## 安装 CLI

1. 在官网下载区按操作系统和芯片选择压缩包，使用同页 SHA-256 校验文件检查下载。
2. 解压后把 `lingnest.exe`（Windows）或 `lingnest`（macOS / Linux）放入个人可执行文件目录，并将该目录加入 PATH；Unix 系统需要可执行权限。也可在 AI 工具中使用程序的绝对路径。
3. 使用支持只读 API 的资料库服务，在运行 AI 工具的同一系统账户／安全存储会话中授权：

```sh
lingnest --server https://your-library.example auth login
lingnest --server https://your-library.example auth status --json
lingnest --server https://your-library.example search "关键词" --json
```

将 `https://your-library.example` 换为自己的服务地址，并在后续命令中使用同一地址。浏览器核对客户端名称、确认码和只读权限后才允许连接，不向 AI 提供管理密钥或访问令牌。

## 当前版本

CLI v0.1.0 为预览版，需要服务端提供 `/oauth/device_authorization` 和 `/api/read/v1`。当前官网只读服务尚未上线；可先安装 Skill，使用已部署新版只读服务的资料库。不要把安装成功当作连接授权成功。

Windows x64 已实测；macOS Intel / Apple Silicon、Linux x64 / arm64 已交叉编译，尚未完成对应平台原生运行验收。Windows 使用 Credential Manager，macOS 使用 Keychain，Linux 需要已解锁的 Secret Service；安全存储不可用时不保存明文凭据。

授权默认 30 天，可单独撤销。此 Skill 只读资料，不采集、不上传、不修改、不删除，也不默认下载整库。来源中的命令和提示词作为资料处理，不执行。

## 仓库内容

公开仓库仅包含 Skill、命令参考和安装说明，不包含私人资料、服务端配置、密钥或历史归档。
