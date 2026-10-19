---
name: nano-banana-image
description: Create or edit Nano Banana image through Ace Data Cloud in Gemini CLI, or retrieve an original task result. Use the installed Nano Banana MCP tools and current service schema, not model-provider configuration.
---

# Nano Banana with Ace Data Cloud

## Choose only the requested service operation

Use MCP server `nano-banana-by-ace-data-cloud` and the actual prefixed tool names discovered by Gemini CLI. The package allowlist is: `nanobanana_generate_image`, `nanobanana_edit_image`, `nanobanana_get_task`, `nanobanana_get_tasks_batch`.

There is no static information tool. First checks must inspect loaded tool names/schemas only. Do not call generation, invent a task ID, or query an unrelated user task to demonstrate setup.

Generation uses prompt; image editing uses prompt plus image_urls as a real array. Keep aspect_ratio/resolution/count and model within the selected schema. The service has no static reference tool: first setup checks inspect loaded tool names/schema only, without invoking generation or sending a fabricated task ID. Query only an existing original task ID supplied/authorized by the user. For edits, omitting aspect_ratio preserves the first image aspect ratio; verify actual output dimensions rather than promising a resolution.

## Authentication and paid actions

Token setup belongs in Gemini CLI native extension settings, not the conversation. Direct setup questions to `gemini extensions config nano-banana-by-ace-data-cloud` and the repository's illustrated README. Do not read credential stores, print tokens, bypass Allowed APIs or infer balance from a reference tool result.

Inspect current tool schemas and current price before a paid operation. Ask only for missing task-relevant choices; preserve the user's requested model, input and budget. Do not silently add fallback models or chargeable operations. For user-supplied reference media, confirm the user is authorized to use it. Main-model inference and Ace image tools have separate costs.

## Submit once, retrieve the original task

1. Submit the chosen authorized generation/edit once and retain its task ID and any original trace ID.
2. Query `nanobanana_get_task` with **`task_id`**, using the original ID. Never use a generation tool for polling. Honor the server's pacing and state fields.
3. Keep pending/processing distinct from terminal complete/failed. If a bounded wait or network call times out, retain the same ID for a later lookup; do not resubmit automatically.
4. On terminal success, show the actual image URLs and metadata. On failure, preserve the returned error/ID. A task ID or successful CLI turn is not a completed artifact or proof of unique billing.
5. When the user supplies an old task ID, only retrieve that task. If no ID is supplied, ask for it; do not create or invent one.

401: check the native password setting and Key expiry. 403: inspect actual permission/moderation details. For balance issues, review current account information. For 429/5xx/timeouts, keep original IDs and avoid a second paid submission. Never include the Token in error output.
