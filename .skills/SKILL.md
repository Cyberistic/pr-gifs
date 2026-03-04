---
name: gif-tools
description: Tools for converting videos to optimized GIFs and generating PR descriptions with GIF embeds. Use when Claude needs to (1) Convert video files (MP4, MOV, etc.) to compressed GIFs under 5MB, (2) Generate GitHub PR descriptions with centered GIF embeds, or (3) Batch process multiple video files into GIF format for documentation.
---

# GIF Tools

Tools for converting videos to optimized GIFs and generating PR descriptions with embedded GIF assets.

## Scripts

### makegif

Converts video files to optimized GIFs under 5MB.

**Usage:**
```bash
makegif <video_file1> [video_file2] [video_file3] ...
```

**Example:**
```bash
makegif ./screen-recording.mp4
makegif ./video1.mp4 ./video2.mov ./video3.avi
```

**Features:**
- Outputs to same directory as input file
- Creates dated filenames: `filename_2026-03-05_01-06-26.gif`
- Optimized for screen recordings with readable text
- Settings: 8 FPS, 600px width, 20 colors
- Progress reporting with color-coded output

### makeprdesc

Generates PR description file with formatted GIF embeds.

**Usage:**
```bash
makeprdesc <pr_url> <directory_with_gifs>
```

**Example:**
```bash
makeprdesc "https://github.com/user/repo/pull/123" "./assets/"
```

**Output:** Creates `pr-description.txt` in the specified directory containing:
- PR URL header
- Centered HTML img tags for all GIFs (50% width, auto height)
- Proper GitHub raw URLs
- Generation timestamp

**Output format:**
```html
## PR URL
https://github.com/user/repo/pull/123

## Screenshots / GIFs

<p align="center">
<img src="https://github.com/.../after.gif?raw=true" alt="after.gif" height="auto" width="50%"/>
</p>
```

## Quick Workflow

1. **Convert videos to GIFs:**
   ```bash
   makegif ./my-recording.mp4
   ```

2. **Generate PR description:**
   ```bash
   makeprdesc "https://github.com/org/repo/pull/456" "./path/to/gifs/"
   ```

3. **Copy the content from `pr-description.txt` into your PR description**

## Requirements

- ffmpeg must be installed
- Scripts must be executable (chmod +x)
