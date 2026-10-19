# Gemini CLI 的 Nano Banana by Ace Data Cloud 扩展

用 Gemini CLI 独立安装 Nano Banana 图片工具与专用 Skill，按原任务 ID 取结果。由 **Ace Data Cloud** 独立提供，不是 Nano Banana 或 Google 官方产品，也不新增主模型服务商选项。

[English](../README.md) · [当前价格](https://platform.acedata.cloud/models?utm_source=gemini-cli&utm_medium=referral&utm_campaign=evergreen&utm_content=nanobananagemini_zh_pricing)

## 1. 原生扩展安装

先安装[官方 Gemini CLI](https://geminicli.com/docs/get-started/installation/)并完成当前模型登录；本包验证 **0.64.0**。Google 已将部分免费/Google One 用户引导到 [Antigravity CLI](https://github.com/google-gemini/gemini-cli#readme)，本包不承诺其兼容。

扩展名称 **nano-banana-by-ace-data-cloud**，发布者 **AceDataCloud/NanoBananaGemini**。从公开仓直接安装正式版本：

```bash
gemini extensions install https://github.com/AceDataCloud/NanoBananaGemini
```

需要固定版本时指定 **v0.1.0**：

```bash
gemini extensions install https://github.com/AceDataCloud/NanoBananaGemini --ref v0.1.0
```

[版本发布](https://github.com/AceDataCloud/NanoBananaGemini/releases/tag/v0.1.0) · [官方目录](https://geminicli.com/extensions/)。目录每日索引与源码/包发布分开，发布和安装成功不代表搜索卡片已经出现。

阅读原生授权提示。它加载 Nano Banana MCP、`nano-banana-image`、`/nano-banana-check`、`/nano-banana-task`，不安装本地服务、没有hooks，不自动生成媒体。

## 2. 注册登录并取 Token

1. [注册或登录 Ace](https://platform.acedata.cloud?utm_source=gemini-cli&utm_medium=referral&utm_campaign=evergreen&utm_content=nanobananagemini_zh_register)。
2. 打开 [Applications](https://platform.acedata.cloud/console/applications?utm_source=gemini-cli&utm_medium=referral&utm_campaign=evergreen&utm_content=nanobananagemini_zh_api_key)，没有 **General application** 则先初始化；检查 Nano Banana 权限与余额。服务 Key 限定对应服务，通用 Key 也受账号/API权限限制。
3. 复制卡片 **API KEY**，或 **Manage Keys → Create** 建专用密钥，建议名称 `Gemini CLI Nano Banana`。

![复制或管理已有脱敏 API Key](../_assets/tutorial/get-api-key-en.png)

4. 按需核有效期、用量与 Allowed APIs。本流程涉及 `/nano-banana/images`, `/nano-banana/tasks`；只开所需接口。提交前核对[当前价格](https://platform.acedata.cloud/models?utm_source=gemini-cli&utm_medium=referral&utm_campaign=evergreen&utm_content=nanobananagemini_zh_before_run)。

![创建独立密钥](../_assets/tutorial/create-api-key-en.png)

这是复用的真实 Ace 脱敏界面，图中 Dify tutorial 为旧示例名称，本扩展请用 `Gemini CLI Nano Banana`。2026-10-18 回读目检，原拍摄日期未注明；[来源](../_assets/tutorial/sources.json)。只复制原始 Token，不带 Bearer、引号或脱敏字符；`platform-...` 管理 Token 不能替代服务 Key，试用额度看当前账号。

## 3. 粘到原生密码项

安装提示 **Ace Data Cloud Nano Banana API Token** 时粘贴原始 Token，不要发进聊天。manifest 为敏感设置，由 CLI 原生秘密存储管理（支持时用系统keychain，否则安全后备存储）。后续更新：

```bash
gemini extensions config nano-banana-by-ace-data-cloud "Ace Data Cloud Nano Banana API Token"
```

专属变量为 `ACEDATACLOUD_NANO_BANANA_TOKEN`，无需手填 MCP 地址/JSON，不改变主模型与Google登录。重启后检查：

```bash
gemini extensions list
gemini mcp list
```

应看到 nano-banana-by-ace-data-cloud 启用、连接；尊重管理员策略，同名settings配置优先。

![官方终端改编参考，非本扩展真实运行](../_assets/tutorial/gemini-cli-reference.png)

**官方截图改编，不是 Nano Banana 实测**。2026-10-17编辑，原素材更新2025-12-01，拍摄日期/版本未标。底部输入、上方看结果；WriteFile/Hello World/2 MCP servers是官方示例，不显示本扩展密码框或安装。[来源与限制](../_assets/tutorial/sources.json)、[Apache说明](../THIRD_PARTY_NOTICES.md)、[验证记录](../VALIDATION.md)。

## 4. 不生成的首用检查

在 Gemini CLI 输入 `/nano-banana-check`，只描述已加载工具名/schema；**Nano Banana 没有静态说明工具，这一步不调用任何媒体或任务工具**。主模型仍可能收推理费。真实任务查询必须使用你自己的已授权旧 ID，不能造一个 ID 测试。

## 5. 执行授权操作，查询同一 ID

生成使用 prompt；编辑为 prompt + image_urls 真实数组。model/aspect_ratio/resolution/count 以当前 schema 为准。编辑省略 aspect_ratio 会保持首图比例；核最终实际像素，不把请求分辨率当结果证明。

按当前模型/schema/价格及用户预算只提交一次，保存原task ID，再用 **`nanobanana_get_task(task_id=ORIGINAL_TASK_ID)`** 查到实际终态；pending/processing不是成功，超时/5xx不自动重生成。

已有任务可输入：

```text
/nano-banana-task YOUR_ORIGINAL_TASK_ID
```

只查该ID，勿造ID或新发生成。返回实际图片URL/状态，再分别核媒体与同请求消费记录；连接、任务ID、绿色回合不证明结果/唯一账单或收入。

## 工具范围

`nanobanana_generate_image`, `nanobanana_edit_image`, `nanobanana_get_task`, `nanobanana_get_tasks_batch`。

底座的其他服务工具不暴露；[原服务源码](https://github.com/AceDataCloud/NanoBananaMCP)拥有实现，本仓不复制服务端。

## 常见问题

| 现象 | 处理 |
|---|---|
| 401/缺Key | 原生config，核服务Key/有效期。 |
| 403 | 读实际权限或内容限制错误，核Allowed APIs。 |
| 无密码提示 | 核扩展设置是否启用，再config；不发Key到聊天。 |
| 无工具 | 重启，查extensions/MCP list与管理员策略；不绕过。 |
| pending/超时 | 原ID继续查询，不自动第二次付费。 |
| 字段/模型错误 | 看当前所选schema，不套其他服务。 |
| 429/5xx/failed | 保留task/trace ID，查原记录后才决定新请求。 |

工具与主模型分别计费；[应用与用量](https://platform.acedata.cloud/console/applications?utm_source=gemini-cli&utm_medium=referral&utm_campaign=evergreen&utm_content=nanobananagemini_zh_usage)的consumption为Credits，美元换算用当前套餐价/数量。没有来源注册、付费或营收结果声明。

## 更新与卸载

```bash
gemini extensions update nano-banana-by-ace-data-cloud
gemini extensions uninstall nano-banana-by-ace-data-cloud
```

[验证](../VALIDATION.md) · [目录交接](../docs/GALLERY_SUBMISSION.md)。代码MIT，官方截图派生Apache-2.0并保留许可，商标属于各权利人。
