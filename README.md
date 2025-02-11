# Command Reference for wiz

## CLI 用法

```bash
wiz git <子命令> [选项]
```

<br>

## 可执行文件用法

Windows:

```bash
wiz-win-x64.exe git <子命令> [选项]
```

Mac(M 系列):
```bash
wiz-macos-arm64 git <子命令> [选项]
```

Mac(Intel 系列):
```bash
wiz-macos-x64 git <子命令> [选项]
```

<br>

## 选项

| 选项                          | 说明                                      |
| ----------------------------- | ----------------------------------------- |
| `-t, --token [token]`         | 指定授权者的 GitLab Access Token          |
| `-p, --projectId [projectId]` | 指定选择的项目 ID                         |
| `-u, --userId [userId]`       | 指定自动 approve 对应 author ID 的所有 MR |

<br>

## 子命令

| 子命令    | 说明                                             |
| --------- | ------------------------------------------------ |
| `approve` | 执行 approve 操作                                |
| `deploy`  | 快速部署到 `develop`、`test`、`pre`、`main` 环境 |

<br>

## 配置文件说明

`.wizrc.json` 配置文件可放置于 `homedir()` 或 `process.cwd()` 目录下。`process.cwd()` 目录下的配置优先级更高。建议配置文件存在 `homedir()` 即可。配置包含 GitLab 和 Jenkins 相关的访问信息。以下是各字段的说明。

### 配置字段说明

| 字段                         | 类型     | 说明                                        |
| ---------------------------- | -------- | ------------------------------------------- |
| `gitlabUrl`                  | `string` | GitLab 服务器的 URL 地址                    |
| `gitlabAccessToken`          | `string` | 用于访问 GitLab API 的个人 Access Token     |
| `gitlabApproveAccessToken`   | `string` | 用于自动 approve 操作的 GitLab Access Token |
| `jenkinsUrl`                 | `string` | Jenkins 服务器的 URL 地址                   |
| `jenkinsUserName`            | `string` | Jenkins 账号用户名                          |
| `jenkinsApiToken`            | `string` | Jenkins API Token，用于认证 API 请求        |
| `jenkinsJobNamesMap`         | `object` | Jenkins 环境与对应 Job 名称的映射关系       |
| `jenkinsJobNamesMap.develop` | `string` | `develop` 环境对应的 Jenkins Job 名称       |
| `jenkinsJobNamesMap.test`    | `string` | `test` 环境对应的 Jenkins Job 名称          |
| `jenkinsJobNamesMap.pre`     | `string` | `pre` 环境对应的 Jenkins Job 名称           |
| `jenkinsJobNamesMap.main`    | `string` | `main` 生产环境对应的 Jenkins Job 名称      |

### 配置示例

```json
{
	"gitlabUrl": "https://yout-gitlab-domain",
	"gitlabAccessToken": "your-gitlab-access-token",
	"gitlabApproveAccessToken": "your-gitlab-approve-access-token",
	"jenkinsUrl": "https://yout-jenkins-domain",
	"jenkinsUserName": "your-jenkins-username",
	"jenkinsApiToken": "your-jenkins-api-token",
	"jenkinsJobNamesMap": {
		"develop": "dev/job/project-dev",
		"test": "test/job/project-test",
		"pre": "pre/job/project-pre",
		"main": "prod/job/project-prod"
	}
}
```
