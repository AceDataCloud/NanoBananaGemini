# Nano Banana by Ace Data Cloud

This independent Nano Banana extension loads service-specific tools and a `nano-banana-image` workflow skill. It is not endorsed by the service owner or Google and does not change Gemini CLI's main model/login.

There is no static information tool. First checks must inspect loaded tool names/schemas only. Do not call generation, invent a task ID, or query an unrelated user task to demonstrate setup.

Use the native password setting `Ace Data Cloud Nano Banana API Token` for credentials; never ask for a Key in chat or expose it. For the requested paid operation, check current price, model and parameters and stay within the user's authorized budget. Submit once, retain the task ID, query the same ID with `nanobanana_get_task` using parameter `task_id`, and do not regenerate to poll or retry. Task-query permission does not grant generation permission. Return only actual terminal media URLs; pending, connection and green CLI status are not final output or unique-billing evidence.

Generation uses prompt; image editing uses prompt plus image_urls as a real array. Keep aspect_ratio/resolution/count and model within the selected schema. The service has no static reference tool: first setup checks inspect loaded tool names/schema only, without invoking generation or sending a fabricated task ID. Query only an existing original task ID supplied/authorized by the user. For edits, omitting aspect_ratio preserves the first image aspect ratio; verify actual output dimensions rather than promising a resolution.
