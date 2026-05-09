# AGW 官方插件仓库


这是 [AGW (AIGateway)](https://github.com/silestar/AIGateway) 的官方插件索引仓库。AGW 通过读取本仓库中的 `plugins.json` 文件，为用户提供官方及社区维护的插件列表。

## 仓库结构

```text
agw-plugins/
├── README.md # 本文件
├── plugins.json # 插件索引（核心文件，AGW 读取此文件获取插件列表）
├── plugin-a/
│ ├── README.md # 插件详情介绍
│ ├── icon.png # 插件图标（建议 128x128）
│ └── versions.json # 版本信息 + 下载地址
└── plugin-b/
├── README.md
├── icon.png
└── versions.json
```

## 插件安装

在 AGW 中配置以下信息后，即可在插件页面浏览和安装本仓库中的插件：

```yaml
# AGW config.yaml
plugin:
  plugin_registry_url: "https://raw.githubusercontent.com/你的用户名/agw-plugins/main"
  use_registry_auth: false
```

## 插件发布流程

### 1. 准备插件包

确保你的插件符合 AGW 插件规范，包含 `manifest.json` 和可执行文件，打包为 ZIP。

### 2. 上传到 GitHub Release

1. 在你的插件仓库中创建新的 Release
2. 填写版本号（如 `v1.0.0`）
3. 上传 ZIP 包作为附件
4. 发布 Release

### 3. 在本仓库添加插件记录

1. Fork 本仓库
2. 创建插件目录：`插件名称/`
3. 添加 `versions.json`，填写下载信息
4. 添加 `README.md`，介绍插件（可选）
5. 添加 `icon.png`，作为插件图标（可选）
6. 更新 `plugins.json`，新增一条插件索引记录
7. 提交 Pull Request

### 4. 审核通过

PR 合并后，AGW 用户即可在插件市场中看到你的插件并安装。

## plugins.json 格式

```json
{
  "name": "AGW 官方插件仓库",
  "description": "由 AGW 社区维护的官方插件集合",
  "updated_at": "2026-05-09T12:00:00Z",
  "plugins": [
    {
      "name": "插件唯一标识",
      "display_name": "插件显示名称",
      "description": "简短描述",
      "author": "作者",
      "category": "分类",
      "icon_url": "图标 URL",
      "detail_url": "README.md 的 raw URL",
      "versions_url": "versions.json 的 raw URL"
    }
  ]
}
```

### 分类说明

| 分类 | 说明 |
| --- | --- |
| `security` | 安全相关（TLS 伪装、认证扩展等） |
| `filter`  | 内容过滤（敏感词过滤、格式转换等） |
| `channel_type` | 渠道类型扩展（新增 AI 服务商支持） |
| `billing` | 计费相关 |
| `general`  | 通用/未分类 |

## 版本管理

每个插件的 `versions.json` 格式：

```json
{
  "name": "插件唯一标识",
  "versions": [
    {
      "version": "1.0.0",
      "min_agw_version": "0.1.0",
      "changelog": "更新日志",
      "download_url": "ZIP 包的下载地址（GitHub Release 附件）",
      "sha256": "文件的 SHA256 校验值（可选）",
      "file_size": 1024000,
      "published_at": "2026-05-01T00:00:00Z"
    }
  ]
}
```

## 贡献指南

欢迎提交插件！请确保：

1. 插件符合 AGW 插件规范（包含合法的 `manifest.json`）
2. 插件 ZIP 包通过 GitHub Release 托管
3. `versions.json` 信息完整准确
4. `plugins.json` 更新无误
5. 插件无恶意代码

## 许可证

本仓库中的索引文件和文档采用 [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0)。各插件的许可证由其作者自行声明，建议在插件目录下的 README.md 中明确标注。
