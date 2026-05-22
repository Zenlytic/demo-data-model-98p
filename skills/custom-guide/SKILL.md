---
name: custom-guide
description: Use when creating visual outputs that should follow the workspace's custom brand guide and bundled brand assets.
enabled: true
assets:
- file_name: Archive.zip
  name: Archive
  description: Zip archive containing the custom guide assets that should be extracted before use.
  file_type: application/zip
---

# Custom Guide

Use this skill when you need the workspace's custom branding, logos, screenshots, or other bundled visual assets.

## Required asset workflow

Before using any asset from this skill, first extract `/data_model/skills/custom-guide/assets/Archive.zip` into a temporary working directory.

Use a workflow like:

```bash
mkdir -p /mnt/data/tmp/custom-guide-assets
python3 << 'EOF'
import zipfile
src = '/data_model/skills/custom-guide/assets/Archive.zip'
dst = '/mnt/data/tmp/custom-guide-assets'
with zipfile.ZipFile(src) as z:
    members = [m for m in z.namelist() if not m.startswith('__MACOSX/') and not m.endswith('/')]
    z.extractall(dst, members)
print('Extracted', len(members), 'files to', dst)
EOF
```

After extraction:
- Use the extracted files from `/mnt/data/tmp/custom-guide-assets/`
- Ignore `__MACOSX` entries and other archive metadata files
- Inspect the extracted files before deciding which ones to use
- Re-extract the archive whenever a fresh sandbox session may not already contain the unpacked files

## Current expected assets

At the time this skill was updated, `Archive.zip` contains these primary files:
- `Screenshot_2026-03-03_at_12.59.05_PM.png`
- `Zenlytic_Logo_Black_1200.png`
- `Zenlytic_Logo_White_Transparent_1200.png`

Do not assume those are the only files forever; treat the zip archive as the source of truth.

## Usage guidance

- Use the screenshot as visual brand reference material when matching look and feel
- Use the black logo on light backgrounds
- Use the white transparent logo on dark backgrounds
- Prefer the extracted assets over recreating logos manually

## Notes

- The archive is the canonical packaged asset source for this skill
- If you need to reference a file in an artifact workflow, extract first, then use the extracted copy from `/mnt/data/tmp/custom-guide-assets/`
