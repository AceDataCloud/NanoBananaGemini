# NanoBananaGemini

This repository owns the Nano Banana Gemini CLI manifest, native sensitive Token setting, workflow skill, commands and bilingual onboarding. The existing NanoBananaMCP owns the server; reuse its hosted endpoint without duplicating/changing shared code. Do not add hooks, trust bypass, hidden fallbacks or automatic paid generation.

Run `python3 -m unittest discover -s tests`, `python3 scripts/package_extension.py --output /tmp/nano-banana-by-ace-data-cloud.tar.gz`, the official `gemini extensions validate` and isolated lifecycle smoke checks. Ordinary CI must use test discovery. Keep English/Chinese guidance aligned, preserve real screenshot sources and license, do not commit .env, keys or private user transcripts. Publish changes through the bot PR; do not merge automatically.

Generation uses prompt; image editing uses prompt plus image_urls as a real array. Keep aspect_ratio/resolution/count and model within the selected schema. The service has no static reference tool: first setup checks inspect loaded tool names/schema only, without invoking generation or sending a fabricated task ID. Query only an existing original task ID supplied/authorized by the user. For edits, omitting aspect_ratio preserves the first image aspect ratio; verify actual output dimensions rather than promising a resolution.
