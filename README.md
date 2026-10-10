# telegram for OpenAgent

Telegram messaging connected to OpenAgent conversations.

Install the release archive through OpenAgent Integrations → Plugins. This is an independent adaptation.

## Plugin settings

Requires a Runtime with the configuration-v1 feature. Open Integrations → Plugins → this plugin to save parameters and credentials. Password fields show only whether a token exists; leave blank to keep it, or explicitly clear and save. OAuth HTTP connectors offer Test, Authorize and local Disconnect here. These operations preserve package data and existing credential files. Running daemons need a restart after changing settings. Actual account operations still require provider-specific acceptance.

## Setup

- Node.js, Telegram bot token saved in plugin settings (channel/.env remains a fallback), desktop channel binding and approved senders.

Run /telegram:setup. Package state belongs in plugin-data/telegram/; private settings and credentials are stored by the Runtime in plugin-settings/telegram.json. Never place secrets in plugin.json or commit them. Refresh the plugin after changing credentials.

Run /telegram:start in a local desktop conversation. channel_bind saves that owner and workspace. Approved inbound peers get separate durable child conversations; replies use the upstream reply tool. Use channel_unbind from the owner to stop dispatch. Access state is plugin-data/telegram/channel/access.json. Remote messages cannot change access policy or resolve OpenAgent approvals; resolve approvals in the desktop. Pending dispatch failures are logged by the adapter. Delivery deduplication retains the latest 1000 dispatched message IDs; crash recovery has at-least-once semantics.

## Verification

bun test tests

Bundled tests cover immutable artifacts, config conversion and peer isolation, deduplication, owner binding and failed dispatch recovery. Runtime acceptance also verifies a real staged installation, slash-command catalog and integration_status. External account authentication, real provider operations and macOS permissions require the prerequisites above; package tests do not claim those credentials are available.

## 中文

将 Telegram 消息连接到 OpenAgent 会话。 安装发布包后运行 /telegram:setup 查看配置要求。凭据和状态保存在当前 OpenAgent 数据目录的 plugin-data/telegram/ 下，修改后刷新插件。在本机管理会话运行 /telegram:start 完成绑定；远程消息不能更改访问权限。

Upstream source and exact revision are recorded in provenance.json. Bundled source remains available for inspection.
