# Third Content Package — 2026-11-01

## Working title
Build a One-Click AI Brief Builder in Google Sheets (No API Key)

## Audience
Solo creators, small businesses, and beginner YouTube creators who collect ideas in spreadsheets but repeatedly rewrite the same instructions when asking an AI assistant for scripts, Shorts, titles, and thumbnail directions.

## Core promise
Turn one idea row in Google Sheets into a consistent, structured AI-ready prompt with a custom menu and a small bound Apps Script. The script does not call an AI API: it prepares the prompt in the sheet for the creator to copy into an AI chat they already use. This avoids an API key or API charge for the prompt-building step; AI chat plan limits and Google Apps Script quotas still apply.

## Research notes
- Google's Apps Script Sheets guide documents bound scripts, reading and writing spreadsheet values, and extending Sheets with custom menus, dialogs, and sidebars: https://developers.google.com/apps-script/guides/sheets
- Google's custom-menu guide says only bound scripts can create menus, and the menu is commonly added from an `onOpen()` function: https://developers.google.com/apps-script/guides/menus
- Google's installable-trigger guide documents additional event types and notes that installable triggers run under the account of the person who created them. This demo deliberately avoids creating an installable trigger; a simple `onOpen()` adds the menu, and the creator clicks the menu item to build the prompt: https://developers.google.com/apps-script/guides/triggers/installable
- Apps Script quotas differ between consumer and Workspace accounts and can change. Do not promise unlimited or universally free execution: https://developers.google.com/apps-script/guides/services/quotas
- Important distinction: this is a prompt builder, not an autonomous AI call. The creator copies the generated prompt into their existing AI chat and reviews the response. An automatic model call would require a separately configured provider/API and may incur charges.
- Existing tracker reviewed: `Automation Empire — Video Production Tracker`, tab `Sheet1`; current columns include working title, format, audience promise/hook, production notes, research/evidence, and next action. The new tracker entry uses a stable Package ID for idempotent upsert.
- Existing GitHub content briefs reviewed: `2026-10-01-ai-automation-first-video.md` and `2026-10-31-ai-video-qa-gate.md`. This package is a distinct spreadsheet prompt-builder tutorial, not another content-pipeline overview or MP4 quality-check tutorial.
- Existing Drive draft folder reviewed. The previous quality-gate package is the only item currently listed there; this filename is new.
- HeyGen sessions checked: no session was actively generating. The latest launch render is completed at 46.7 seconds; a separate long-form attempt previously failed with `free_tier_quota_exceeded`. No new generation was started.
- vidIQ balance check returned 0 available credits, so vidIQ research was skipped.
- Firecrawl current balance check returned 578 remaining of 1,000 plan credits. Free tool discovery returned a provider error (HTTP 500) and cost 0 credits. No Firecrawl search or scrape was run because the instruction prohibits spending credits.
- Exa search was used to retrieve official Google Apps Script documentation. The Exa response does not expose a per-call credit receipt, so this package does not claim that Exa usage was credit-free.

### Sources
1. Extend Google Sheets with Apps Script: https://developers.google.com/apps-script/guides/sheets
2. Custom menus in Google Workspace: https://developers.google.com/apps-script/guides/menus
3. Apps Script triggers and restrictions: https://developers.google.com/apps-script/guides/triggers
4. Installable triggers: https://developers.google.com/apps-script/guides/triggers/installable
5. Apps Script quotas and limitations: https://developers.google.com/apps-script/guides/services/quotas
6. Apps Script authorization: https://developers.google.com/apps-script/guides/services/authorization
7. Existing Automation Empire tracker: https://docs.google.com/spreadsheets/d/1GkLcj5eol0pqjUaFWpJBsVTAkTzMmHiamPZFvC6ZLfQ/edit
8. Existing GitHub workflow: https://github.com/devunh11-dev/openclaw-command-center/blob/integration/secure-js-tool-plan-20261009/.github/workflows/content-pipeline.yml

## Script draft

### Opening and hook (0:00–0:30)
**Presenter — user's approved digital twin; cloned voice if a no-cost render route is confirmed**

Ever sit down to make a video and spend more time explaining the idea to your AI than actually making the video?

Let's fix that handoff.

I'm going to turn one row in Google Sheets into a structured AI brief with one click. No API key, no extra automation subscription for the prompt-building step.

And just to be clear: the spreadsheet is not secretly generating AI. It builds the prompt, then you choose the AI chat you want to use and review the result.

### Show the finished workflow (0:30–0:55)
On screen: show a row with a working title, format, audience promise, notes, and research links.

I put the idea in one row. I choose Automation Empire from the menu, click Build AI Brief Prompt, and the sheet writes a complete prompt into a new column.

Now I can copy that prompt into my AI chat and ask for a script, two Shorts, titles, a description, chapters, and thumbnail concepts — all using the same context.

### Set up the sheet (0:55–1:35)
You need a Google Sheet with a header row. This demo uses the columns already in the Automation Empire tracker:

- Asset / working title
- Format
- Audience promise / hook
- Production notes
- Research / evidence
- Next action

The script looks up the columns by their header names, not by fixed column letters. That makes it easier to move columns around later.

For safety, make a copy of your tracker and test the script there first. Do not paste private keys or sensitive account information into your content brief.

### Add the custom menu (1:35–2:05)
Open the spreadsheet, choose Extensions, then Apps Script. That creates a script bound to this spreadsheet.

Paste the code from the description, save it, and reload the spreadsheet. The `onOpen()` function adds an Automation Empire menu when the sheet opens.

This is a built-in Sheets extension point documented by Google. The menu is not a third-party add-on.

### Build the prompt (2:05–3:35)
Select any content row below the header. Open Automation Empire and click Build AI Brief Prompt.

The function reads the selected row, finds the fields by name, and assembles a prompt with the idea, format, audience, notes, and research.

If the AI Brief Prompt column does not exist yet, the script adds it. Then it writes the prompt into that row.

Here is the key: the output prompt tells the AI to create original material, identify uncertain claims, include source links, and avoid invented statistics or testimonials. It also keeps publishing behind a human approval step.

### Use the prompt in your AI chat (3:35–4:20)
Copy the prompt from the new column and paste it into the AI assistant you already use.

You can ask it for one long-form script, two distinct Shorts, title options, description, hashtags, chapters, and two thumbnail concepts.

The spreadsheet has only packaged the context. The AI chat does the language generation. You still need to check sources, confirm product features, and edit the result so it sounds like your channel.

### What is automated — and what is not (4:20–4:55)
This removes repetitive prompt-writing and makes every idea start with the same useful structure.

It does not call an AI API, upload a video, generate a thumbnail, or publish anything. If you later connect a model API, that is a separate step with its own permissions, billing, and rate limits.

Google Apps Script also has quotas that vary by account type and can change. Keep the workflow small, test it on a copy, and check the current limits before scaling it.

### Close and CTA (4:55–5:20)
One row becomes one reusable brief. One menu click prepares the handoff. You stay in control of the AI output and the final publishing decision.

That is a practical way to make your content process more repeatable without paying for an API just to format a prompt.

Follow Automation Empire for practical AI workflows that save repetitive work without handing your quality control to a robot.

### Apps Script demo code
This is a bound-script example for a sheet whose first row contains the header names listed above. It adds an `AI Brief Prompt` column if needed and writes the prompt for the selected row. It does not contact an AI service.

```javascript
function onOpen() {
  SpreadsheetApp.getUi()
    .createMenu('Automation Empire')
    .addItem('Build AI Brief Prompt', 'buildAiBriefPrompt')
    .addToUi();
}

function buildAiBriefPrompt() {
  const ui = SpreadsheetApp.getUi();
  const sheet = SpreadsheetApp.getActiveSheet();
  const activeRange = sheet.getActiveRange();

  if (!activeRange || activeRange.getRow() < 2) {
    ui.alert('Select one content row below the header row first.');
    return;
  }

  const rowNumber = activeRange.getRow();
  const lastColumn = sheet.getLastColumn();
  const headers = sheet
    .getRange(1, 1, 1, lastColumn)
    .getDisplayValues()[0]
    .map(value => value.trim());

  const values = sheet
    .getRange(rowNumber, 1, 1, lastColumn)
    .getDisplayValues()[0];

  const field = name => {
    const index = headers.indexOf(name);
    return index < 0 ? '' : values[index].trim();
  };

  const idea = field('Asset / working title');
  const format = field('Format');
  const audience = field('Audience promise / hook');
  const production = field('Production notes');
  const research = field('Research / evidence');
  const nextAction = field('Next action');

  if (!idea && !audience) {
    ui.alert('Add a working title or audience promise before building a prompt.');
    return;
  }

  const prompt = [
    'You are an original YouTube content strategist for Automation Empire.',
    'Create useful, truthful, original material. Do not invent statistics, testimonials, sources, or tool features.',
    'Return: one long-form script, two distinct Shorts, three title options, a description, hashtags, chapters, research links, and two thumbnail concepts.',
    'Do not copy another creator. Label uncertainty. Keep publishing behind explicit human approval.',
    '',
    'Working idea: ' + (idea || 'Not supplied'),
    'Format: ' + (format || 'Choose a suitable format and explain why'),
    'Audience promise / hook: ' + (audience || 'Not supplied'),
    'Production notes: ' + (production || 'Not supplied'),
    'Research / evidence: ' + (research || 'Not supplied'),
    'Next action: ' + (nextAction || 'Not supplied')
  ].join('\n');

  let promptColumn = headers.indexOf('AI Brief Prompt') + 1;
  if (promptColumn === 0) {
    promptColumn = lastColumn + 1;
    sheet.getRange(1, promptColumn).setValue('AI Brief Prompt');
  }

  sheet.getRange(rowNumber, promptColumn).setValue(prompt);
  ui.alert(
    'Prompt saved in the AI Brief Prompt column. Copy it into your AI chat. This script does not call an AI API.'
  );
}
```

### Setup and test notes
1. Make a copy of the tracker and open the copy.
2. Choose Extensions → Apps Script.
3. Paste the code, save, and reload the spreadsheet.
4. Select a data row (not the header) and choose Automation Empire → Build AI Brief Prompt.
5. Inspect the new AI Brief Prompt cell. Copy it into your AI chat manually.
6. If Google asks for authorization, review the requested scopes before approving. Do not grant broader permissions than the script needs.
7. Test with sample content first. The script uses the active sheet and writes only to that spreadsheet.

## Title and metadata

### Primary title
Build a One-Click AI Brief Builder in Google Sheets (No API Key)

### Alternate titles
- Turn Any Video Idea Into an AI Brief With One Click
- This Google Sheets Menu Builds Your Next Video Prompt
- Stop Rewriting AI Prompts: Automate the Brief in Sheets

### Description
Turn one content idea into a reusable AI-ready brief — right inside Google Sheets.

In this Automation Empire tutorial, we add a small Google Apps Script custom menu. Select a content row, click Build AI Brief Prompt, and the script writes a structured prompt into a new column. Copy it into the AI chat you already use to draft a long-form script, two Shorts, titles, description, hashtags, chapters, and thumbnail concepts.

Important: this is a prompt builder, not an automatic AI API integration. The script does not send your data to an AI model, does not need an API key, and does not incur an AI API charge for the prompt-building step. Your AI chat plan limits and Google Apps Script quotas still apply. If you later connect a model API, review its permissions, pricing, and limits separately.

Make a copy of your sheet before testing. Review the code and any authorization request before approving it.

Official references:
- https://developers.google.com/apps-script/guides/sheets
- https://developers.google.com/apps-script/guides/menus
- https://developers.google.com/apps-script/guides/services/quotas

Follow Automation Empire for practical, original AI automation workflows.

### Hashtags
#GoogleSheets #AppsScript #AIAutomation #YouTubeWorkflow #ContentCreator #PromptEngineering #AutomationEmpire

### Search tags
Google Sheets Apps Script, AI content brief, Google Sheets automation, Apps Script custom menu, no API key AI workflow, YouTube content planning, AI prompt builder, creator workflow, content automation, spreadsheet automation

### Chapters
00:00 Stop rewriting the same AI brief
00:30 One row to one structured prompt
00:55 Set up the sheet
01:35 Add the Automation Empire menu
02:05 Build the prompt
03:35 Paste it into your AI chat
04:20 What is and isn't automated
04:55 Keep human review in control

## Short 1 — One row to one AI brief

### Working title
Turn One Google Sheets Row Into an AI Brief

### Hook
Stop rewriting the same video prompt every time you have a new idea.

### Script (30–40 seconds)
Stop rewriting the same video prompt every time you have a new idea.

Put the title, audience, format, and notes into one Google Sheets row.

Then add a tiny Apps Script menu called Automation Empire. Select the row, click Build AI Brief Prompt, and the sheet assembles the context into one reusable prompt.

Copy it into your AI chat and start with a consistent brief.

The script does not call an AI API — it just removes the repetitive setup. Follow Automation Empire for practical workflows.

### Short description
A Google Sheets custom menu can package one idea row into a structured AI prompt. The script prepares the prompt; you choose the AI chat and review the output.

### Short hashtags
#GoogleSheets #AppsScript #AIAutomation #YouTubeShorts #AutomationEmpire

### Visual direction
Vertical 9:16. Open with the user's approved digital twin and a messy list of video ideas. Cut to one clean spreadsheet row, then show the Automation Empire menu and the AI Brief Prompt cell. Use the user's cloned voice only if a no-cost render route is confirmed. Keep captions large and within safe margins.

## Short 2 — The honest no-API workflow

### Working title
No API Key? Use This Human-in-the-Loop AI Workflow

### Hook
You can automate the boring setup without pretending the spreadsheet is the AI.

### Script (35–45 seconds)
You can automate the boring setup without pretending the spreadsheet is the AI.

Google Sheets and Apps Script can build a structured prompt from your idea, audience, format, and notes.

One click writes that prompt into the sheet. You copy it into the AI chat you already use.

No model API call happens in the script, so there is no API key or API charge for that step.

The AI chat still has its own plan limits, and you still review the result before publishing.

That is human-in-the-loop automation: less repetitive work, but you stay in control.

### Short description
A no-API prompt builder can automate context assembly while leaving AI generation and final review in your existing chat. No claim of unlimited free AI usage.

### Short hashtags
#NoCodeAutomation #GoogleAppsScript #AIWorkflow #CreatorTools #AutomationEmpire

### Visual direction
Vertical 9:16. Start on the user's approved digital twin beside a split-screen: “Prompt builder” on the spreadsheet side and “AI chat” on the other. Animate the prompt moving from the sheet to the chat, then show a human-review check. Use the cloned voice only if a no-cost route is verified; no new generation is included in this package.

## Thumbnail concepts

### Variant A — “ONE CLICK → AI BRIEF”
- Composition: user's own approved face/digital twin on the right, surprised-but-credible expression, pointing to a spreadsheet row that transforms into a clean prompt card.
- Exact hook text: ONE CLICK → AI BRIEF
- Supporting visual: one highlighted row, one gold arrow, one large prompt card; no tiny unreadable spreadsheet text.
- Palette: midnight navy (#07152B), electric blue (#1777FF), gold (#F5C542), white.
- Typography: same bold condensed headline treatment and placement used across Automation Empire thumbnails.
- Why test it: communicates the one-click outcome immediately.

### Variant B — “NO API KEY?”
- Composition: user's own approved face/digital twin on the left; right side shows a simple Sheets icon → prompt card → AI chat flow.
- Exact hook text: NO API KEY?
- Supporting visual: a small crossed-out API-key field, with the clear distinction “prompt builder ≠ AI model” shown as a simple visual label.
- Palette and typography: same navy/blue/gold identity, bold readable text, uncluttered background.
- Why test it: emphasizes the low-cost angle while remaining honest about the separate AI-chat step.

Both are concepts only. Use the user's actual face/twin; do not substitute a stock person. No thumbnail image generation has been run.

## Production plan
- Main video: 16:9, target 5:10–5:30. Use direct-to-camera sections with the user's approved digital twin and cloned voice only if the route is confirmed no-cost; otherwise keep the package as a script and use genuine screen recording with the user's own narration.
- Screen demos: show a duplicate spreadsheet, Extensions → Apps Script, the custom menu, a selected row, the generated prompt cell, and the manual copy/paste into an AI chat. Use real captures, not fabricated UI.
- B-roll: spreadsheet-to-prompt animation, prompt card, human-review check, and a simple “no API call” diagram.
- Short 1: 9:16, 30–40 seconds, show the one-row-to-prompt transformation.
- Short 2: 9:16, 35–45 seconds, explain the boundary between prompt assembly and AI generation.
- Thumbnails: prepare both concepts with the user's own face after approval; no image generation.
- Avoid showing private spreadsheet rows, email addresses, tokens, API keys, or personal account details.

## Production checklist
- [ ] Approve the working title and long-form script.
- [ ] Test the Apps Script on a copy of the tracker before demonstrating it.
- [ ] Confirm the sheet's header names match the code; if headers change, update the field names deliberately.
- [ ] Confirm the custom menu appears after reload and the prompt is written to the correct row.
- [ ] Show that the script only builds a prompt and does not call an AI API.
- [ ] Review any Google authorization prompt and the requested scopes before approving.
- [ ] Verify the current Apps Script quotas for the account type; do not promise unlimited use.
- [ ] Use the approved digital twin and cloned voice only if a no-cost generation route is confirmed.
- [ ] Create both Shorts as independent edits with readable vertical captions.
- [ ] Develop thumbnail variants A and B using the user's actual face; no stock-person substitution.
- [ ] Watch the full export and both Shorts; check audio, captions, pacing, framing, and factual accuracy.
- [ ] Keep all assets in draft/review status.
- [ ] Publish or schedule only after explicit approval of the exact asset, destination, and timing.

## Package operations and limitations
- Stable Package ID: AE-2026-11-01-GSHEETS-AI-BRIEF-BUILDER
- GitHub target: `content/2026-11-01-google-sheets-ai-brief-builder.md` on branch `integration/secure-js-tool-plan-20261009`.
- Google Sheets tracker update: one idempotent upsert keyed by `Package ID`; the existing header row is preserved and the key column is added if missing.
- Google Drive target: `Automation Empire — Draft Assets/2026-11-01 Google Sheets AI Brief Builder — Content Package.md`.
- No video/image generation, publishing, scheduling, subscription, paid API call, or public-setting change is included.
