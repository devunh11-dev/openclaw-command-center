# Second Content Package — 2026-10-31

## Working title
Stop Wasting AI Video Credits: Add a 2-Stage Quality Gate

## Audience
Solo creators, small businesses, and AI-assisted YouTube creators who use AI tools to script, narrate, edit, or generate video and want to reduce avoidable re-renders before spending more time or generation credits.

## Core promise
Show a practical two-stage quality gate: lock the brief before production, then inspect the exported MP4 with FFprobe before upload. Explain exactly what can be automated and what still needs a human review.

## Research notes
- FFprobe is part of FFmpeg. Its official documentation says it gathers multimedia-stream information and prints it in human- and machine-readable formats; it can inspect container format and stream types. JSON output and selected entries make it suitable for a repeatable technical preflight/postflight check.
- GitHub Actions workflows are YAML files stored in `.github/workflows`. GitHub documents event triggers such as repository pushes and pull requests. A workflow can also be manually dispatched when configured.
- Existing Automation Empire workflow: `.github/workflows/content-pipeline.yml` on branch `integration/secure-js-tool-plan-20261009`. It currently runs on content Markdown changes and pull requests, plus manual dispatch. It checks required content-package headings. It does NOT inspect MP4 files, upload videos, or publish.
- Practical distinction: the pre-render checklist catches avoidable brief/configuration mistakes before generation. FFprobe checks the completed export after rendering; it cannot prevent the initial render cost. It can help catch technical problems before another export or upload.
- GitHub Actions runner allowances and billing depend on repository/account plan. Do not claim unlimited or universally free runner minutes. FFmpeg/FFprobe is open-source software; verify the local install and the account's runner allowance before enabling additional jobs.
- vidIQ was not used because the connected balance check returned 0 available credits. Exa and Firecrawl were used for research; no paid video/image generation or paid research credits were requested.

### Sources
1. FFprobe official documentation: https://ffmpeg.org/ffprobe.html
2. GitHub Actions workflow events: https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows
3. GitHub Actions workflow syntax: https://docs.github.com/actions/using-workflows/workflow-syntax-for-github-actions
4. Current Automation Empire workflow: https://github.com/devunh11-dev/openclaw-command-center/blob/integration/secure-js-tool-plan-20261009/.github/workflows/content-pipeline.yml
5. Existing first content brief (reviewed to avoid repeating the same overview): https://github.com/devunh11-dev/openclaw-command-center/blob/integration/secure-js-tool-plan-20261009/content/2026-10-01-ai-automation-first-video.md

## Script draft

### Opening and hook (0:00–0:35)
**Presenter — user's approved digital twin; cloned voice for narration**

Ever wait for an AI video to finish rendering, only to discover it is the wrong shape, the audio is missing, or the export is cut off?

That is not always an AI problem. A lot of the time, it is a workflow problem.

Today I’m showing you a two-stage quality gate: check the brief before production, then inspect the finished video file before you upload it. The goal is simple: fewer avoidable re-renders, fewer surprises, and no guessing.

### Why a quality gate matters (0:35–1:10)
AI can help with the script, voice, visuals, captions, and editing. But if the instructions are unclear, a tiny mistake can travel through the whole pipeline.

If you change the script after the voice is recorded, you may need another voice pass. If you choose the wrong aspect ratio, you may need another export. If you discover the audio is missing at upload time, you have already wasted the time it takes to get there.

So split the checks into two stages.

### Stage one: before you render (1:10–2:25)
Before you spend time or generation credits, lock five things.

First: the promise. Can you explain what the viewer will learn in one sentence? Does the opening deliver that promise quickly?

Second: the script. Is the hook approved? Are the main steps in the right order? Is the call to action included? If the script is still changing, it is not ready for production.

Third: the presenter and voice. Use the approved Automation Empire digital twin and cloned voice for presenter-led videos. Confirm the right look and voice are selected before generating anything.

Fourth: the format. A normal long-form YouTube video is usually planned in a horizontal layout; a Short is planned vertically. Set the target canvas before you build scenes, not after.

Fifth: the assets. Are the B-roll, logos, music, screenshots, and fonts cleared for use? Are the right files attached? Are captions planned?

Put those checks in the content brief or tracker. Do not mark a package ready to render until the script, presenter, format, and assets are locked. That does not guarantee a great video, but it prevents avoidable setup mistakes.

### Stage two: inspect the exported MP4 with FFprobe (2:25–3:55)
Now the video has rendered. Before you upload it, inspect the actual file.

FFprobe is a command-line tool included with FFmpeg. It reads a media file and reports information about its container and streams. It can return structured JSON, which makes the output easier to check consistently.

Here is a simple example:

```bash
ffprobe -v error \
  -show_entries format=duration:stream=codec_type,width,height \
  -of json "final.mp4"
```

Look at the result.

Do you have a video stream? Are the width and height what you expected? Is there an audio stream? Is the duration within the target range?

For a vertical Short, the height should be greater than the width. For a horizontal long-form video, the width should be greater than the height. Compare those values with the format you selected in stage one.

This is a technical check, not a creative review. FFprobe cannot tell you whether the hook is interesting, whether the captions are readable, or whether the thumbnail is honest. It tells you whether the file has the basic media properties you expected.

### What GitHub Actions already automates (3:55–4:50)
Here is where the automation layer comes in.

The Automation Empire repository already has a GitHub Actions workflow. When a content Markdown file changes, or a pull request includes one, the workflow checks that the package contains the required sections: a working title, a script draft, and a production checklist. It can also be run manually.

That catches a missing brief section before the team moves into production.

Important: the current workflow checks the Markdown package. It does not inspect a rendered MP4, connect to HeyGen, or publish to YouTube. The next technical improvement would be a separate media-check job that runs only when a video file or a permitted build artifact is available to the runner. Keep large video files in Drive or your media store rather than committing them to Git by default.

### Human review still matters (4:50–5:35)
After the automated checks pass, watch the actual video.

Check the first ten seconds. Listen for clipped words or uneven audio. Read the captions on a phone-sized screen. Confirm that the thumbnail and title describe what the video really delivers. Check that you have rights to every visual and audio asset.

Then make the publishing decision yourself. A green technical check is not permission to publish. Keep the final upload behind an explicit approval step.

### Close and CTA (5:35–5:55)
The system is simple: lock the brief before production, inspect the export after rendering, and let a human approve the final result.

That is how you make an AI content workflow more reliable without buying another tool for every problem.

Follow Automation Empire for practical AI workflows that save repetitive work without handing your quality control to a robot.

## Title and metadata

### Primary title
Stop Wasting AI Video Credits: Add a 2-Stage Quality Gate

### Alternate titles
- Before You Render: The AI Video Checklist That Saves Rework
- Check Every AI Video Before You Upload (FFprobe + GitHub Actions)

### Description
A video can render successfully and still miss the brief. In this Automation Empire tutorial, I show a two-stage quality gate for AI-assisted video production:

1. Lock the script, presenter/voice, format, and assets before rendering.
2. Inspect the exported MP4 with FFprobe before upload.
3. Use GitHub Actions to catch missing sections in the content brief.
4. Keep the final creative and publishing review with a human.

FFprobe checks technical media details such as container and stream information. It does not judge storytelling, caption readability, rights, or whether the video delivers its promise. GitHub Actions runner limits depend on your account and repository plan.

Example command:
`ffprobe -v error -show_entries format=duration:stream=codec_type,width,height -of json "final.mp4"`

Sources:
- https://ffmpeg.org/ffprobe.html
- https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows
- https://docs.github.com/actions/using-workflows/workflow-syntax-for-github-actions

Subscribe to Automation Empire for useful, original AI automation workflows.

### Hashtags
#AIAutomation #YouTubeAutomation #FFmpeg #FFprobe #GitHubActions #ContentCreator #VideoWorkflow #AutomationEmpire

### Search tags
AI video workflow, AI content automation, FFmpeg tutorial, FFprobe tutorial, GitHub Actions automation, YouTube creator workflow, video quality check, MP4 metadata, AI creator tools, content production checklist

### Chapters
00:00 The re-render problem
00:35 Why a quality gate matters
01:10 Stage one: before you render
02:25 Stage two: inspect the MP4 with FFprobe
03:55 What GitHub Actions already checks
04:50 Human review still matters
05:35 The two-stage workflow

## Short 1 — Pre-render checklist

### Working title
Don't Hit Render Until These 5 Things Are Locked

### Hook
Before you hit render, lock these five things.

### Script (30–40 seconds)
Before you hit render, lock five things: the promise, the script, the presenter and voice, the video format, and the assets.

If the script changes after narration, you may need another pass. If you choose the wrong format, you may need another export. If an asset is missing, the whole edit can stall.

Put the checks in your content tracker. Only move the package to production when the brief is actually ready.

That is how you cut avoidable rework. The full two-stage quality gate is on Automation Empire.

### Short description
A five-point pre-render check can prevent avoidable production rework: promise, script, presenter/voice, format, and cleared assets. This is a workflow checklist, not a guarantee of performance.

### Short hashtags
#AIAutomation #VideoWorkflow #YouTubeShorts #ContentCreator #AutomationEmpire

### Visual direction
9:16 vertical. Start with the user's approved digital twin close to camera. Five quick blue-and-gold checklist cards animate beside the presenter. Use the cloned voice, crisp captions, and a final full-screen “READY TO RENDER?” check. No new generation is included in this package.

## Short 2 — Post-render MP4 check

### Working title
This One Command Checks Your Video File Before Upload

### Hook
Your MP4 can look fine in a preview and still miss the export spec.

### Script (35–45 seconds)
Your MP4 can look fine in a preview and still miss the export spec.

Use FFprobe. It reads the media file and reports details about its container and streams.

Run this:

```bash
ffprobe -v error -show_entries format=duration:stream=codec_type,width,height -of json "final.mp4"
```

Check the duration, width, height, and whether an audio stream exists. Compare those values with the format you planned.

It will not judge your hook or captions, but it can catch technical misses before upload. Save this command, and watch the full Automation Empire walkthrough.

### Short description
Use FFprobe to inspect an exported MP4's duration and stream details before upload. It is a technical check, not a substitute for watching the video.

### Short hashtags
#FFprobe #FFmpeg #VideoEditing #AIAutomation #YouTubeTips #AutomationEmpire

### Visual direction
9:16 vertical. Open on the user's approved digital twin pointing to a large MP4 tile. Cut to a clean terminal capture with the command highlighted in gold; animate width, height, duration, and audio-stream checks as blue status cards. End on “CHECK THE FILE. THEN WATCH IT.” Use the cloned voice and readable captions. No new generation is included in this package.

## Thumbnail concepts

### Variant A — “CHECK BEFORE RENDER”
- Composition: user's own approved face/digital twin on the right, expressive surprised-but-credible look; large readable text on the left.
- Exact hook text: CHECK BEFORE RENDER
- Visual: one MP4 tile with a red warning mark on one side and a gold/blue check on the other; subtle terminal/code texture behind it.
- Palette: midnight navy (#07152B), electric blue (#1777FF), gold (#F5C542), white.
- Title pairing: primary title.
- Why test it: communicates the problem and the fix in one glance.

### Variant B — “NO MORE RE-RENDERS”
- Composition: user's own approved face/digital twin on the left, pointing toward three large quality cards: SCRIPT, FORMAT, AUDIO.
- Exact hook text: NO MORE RE-RENDERS
- Visual: a vertical-versus-horizontal frame comparison and one clear gold checkmark; keep the background uncluttered.
- Palette and typography: same blue/gold identity and same bold condensed headline treatment as Variant A.
- Title pairing: alternate title “Before You Render: The AI Video Checklist That Saves Rework”.
- Why test it: emphasizes the time/rework pain rather than the technical tool.

Both are concepts only. Use the user's actual face/twin; do not substitute a stock person. Keep the thumbnail promise truthful and readable at phone size.

## Production plan
- Main video: 16:9, target 5:45–6:00, user's approved digital twin for intro/outro and cloned voice for narration; record real screen capture of the FFprobe command and the existing GitHub workflow file.
- B-roll: a simple pipeline diagram, pre-render checklist, terminal output, and horizontal/vertical frame comparison. Prefer screen captures and simple motion graphics over paid generated footage.
- Short 1: 9:16, 30–40 seconds, checklist-first hook.
- Short 2: 9:16, 35–45 seconds, command-first hook.
- Thumbnail: develop both concepts with the user's face after approval; no image generation was run.
- Reuse the same voice/brand package; adapt framing and captions separately for vertical clips.

## Production checklist
- [ ] Approve the working title and script before any generation.
- [ ] Verify the FFprobe command on a sample MP4 and show real output; do not fabricate terminal results.
- [ ] Show the current GitHub Actions workflow accurately; distinguish existing Markdown validation from proposed MP4 validation.
- [ ] Confirm the chosen presenter look and cloned voice; no new HeyGen generation until cost/credit availability is confirmed.
- [ ] Capture screen footage without exposing credentials, private tokens, or personal account data.
- [ ] Check video duration, dimensions, video stream, and audio stream with FFprobe after render.
- [ ] Watch the full export; check hook, pacing, audio, captions, title promise, thumbnail readability, and asset rights.
- [ ] Prepare both thumbnail variants using the user's own face; no stock-person substitution.
- [ ] Review both Shorts independently; each must make sense without the long video.
- [ ] Keep all assets in draft/review status.
- [ ] Publish or schedule only after explicit approval of the exact asset, destination, and timing.
- [ ] Record the verified video URL and analytics only after publication.
