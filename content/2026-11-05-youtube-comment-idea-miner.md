# Seventh Automation Empire Content Package — 2026-11-05

## Working title

**Turn YouTube Comments Into Your Next 10 Video Ideas (No Paid AI API)**

### Alternate titles
1. Stop Guessing What to Post — Mine Your Comments
2. Your Next Video Is Hiding in Your Comments
3. Build a Free Creator Feedback Loop With YouTube + Sheets

### Audience and promise
For solo creators and small YouTube channels that struggle to decide what to make next. This tutorial shows a privacy-conscious, human-reviewed way to turn recurring viewer questions into a structured idea list using YouTube Studio, Google Sheets, a small bound Apps Script, and an AI chat used manually. The demo does not call an AI API, scrape other channels, reply to comments, or publish anything.

### Original angle
The value is not “AI reads every viewer.” It is a repeatable feedback loop: find genuine questions, remove identifying details, deduplicate, turn the remaining themes into a prompt, then choose ideas that can be demonstrated honestly. The script is a helper, not an audience-profiling system.

## Script draft

**Target runtime:** 5:35–5:55  
**Format:** 16:9 flagship tutorial, direct-to-camera digital twin, cloned voice, screen-recorded demo and clean motion graphics.  
**Presenter:** Use the user's approved digital twin and cloned voice only after a no-cost rendering route is confirmed.  
**Visual identity:** High-contrast navy/blue and gold; consistent typography; energetic, credible delivery.

### Chapters
- 0:00 — Your next video may already be in your comments
- 0:25 — Stop treating comments as a reply-only inbox
- 0:58 — Find useful questions in YouTube Studio
- 1:38 — Build a simple comment inbox in Sheets
- 2:05 — Add the one-click cleanup menu
- 3:18 — Turn cleaned themes into an AI prompt
- 4:15 — Choose ideas you can actually prove
- 5:20 — Recap and next step

### Full narration and scene direction

**[0:00–0:25 | A-roll: presenter, surprised expression. On-screen hook: “YOUR NEXT VIDEO IS ALREADY HERE.”]**

What if your next ten video ideas are already sitting under the videos you published? Most creators open their comments to reply, maybe heart a few messages, and then leave. But inside those comments are questions, sticking points, and requests. Today, I’ll show you a simple way to turn that feedback into a usable idea list—without buying another AI subscription or connecting a paid AI API.

**[0:25–0:58 | B-roll: comment bubbles become idea cards. On-screen text: “QUESTIONS → THEMES → IDEAS.”]**

Here’s the rule: don’t treat one loud comment as proof that everybody wants a topic. Look for patterns. If several people ask how to start, why something failed, or which step comes next, that is a useful signal to investigate. It is not a guarantee that a video will go viral. It is a better starting point than guessing in a blank document.

**[0:58–1:38 | Screen demo: YouTube Studio, Community, Published tab; show the Questions filter. Blur names and profile pictures.]**

First, open YouTube Studio and go to Community. Choose the Published comments tab. Use the filter bar to narrow the list to questions, or search for a phrase connected to the problem your channel teaches. Start with one of your own videos. Pick a small batch—say twenty to thirty useful comments. Skip spam, private information, and anything you would not want to show on screen. Do not collect usernames, profile links, or personal details. We only need the question or problem being described.

**[1:38–2:05 | B-roll: a clean spreadsheet with one column labelled “Comment text — reviewed first.”]**

Next, open a Google Sheet. Create a tab called Comment Inbox. Put one reviewed comment per row in column A, starting in row two. The first row is just the header. You can use synthetic examples while learning: “How do I make captions faster?” or “Why does my automation stop after one step?” Never use a real person's name in the demo.

**[2:05–3:18 | Screen demo: Apps Script editor; code callouts highlight menu, cleanup, deduplication.]**

Now add a small Apps Script that creates an Automation Empire menu. The menu has three actions: set up the two tabs, build a cleaned prompt, and clear the temporary inbox when you’re finished. The script removes obvious email addresses, phone-number patterns, links, and @handles, then removes exact duplicates. It does not send anything to an AI service. It simply prepares text for you to inspect.

Paste the code from the production notes into the Apps Script editor attached to your test spreadsheet. Save it, reload the Sheet, and choose Automation Empire, then Set up comment miner. The first time you run a function, Google may show an authorization screen for the spreadsheet you are editing. Read the scope and approve only if it matches what you expect.

**[3:18–4:15 | Screen demo: AI Prompt tab; cursor highlights the copy-ready prompt. On-screen text: “YOU REVIEW. AI HELPS.”]**

When your reviewed comments are in the inbox, choose Build sanitized prompt. The script creates an AI Prompt tab with a structured instruction. It asks the AI to identify repeated questions, group similar problems, and suggest ten original video ideas. It asks for the audience problem, an honest promise, a practical demonstration, and whether the idea fits long-form or a Short. It also tells the AI not to invent search volume, audience statistics, or performance claims.

Before copying anything, read the prompt yourself. The cleanup code is only a first pass; it cannot guarantee that every identifying detail has been removed. If a comment contains a person's name, workplace, address, health detail, or another private detail, delete it or rewrite it as a neutral paraphrase. Then copy only the reviewed, anonymized themes into the AI chat you choose. The free chat's own limits still apply, but this workflow does not make a paid API call.

**[4:15–5:20 | A-roll + motion graphic: three filters appear — useful, demonstrable, original.]**

Now comes the most important part: choosing. Do not blindly accept the AI's list. Keep an idea only if it passes three checks. First, usefulness: does it solve a specific problem? Second, proof: can you show the steps on screen and verify the claims? Third, originality: can you explain it in your own words with your own example, instead of copying another creator?

For example, if several comments ask why an automation stops after the first item, a useful tutorial might show how to inspect a run history, identify the failed step, and test with one sample record. That is a real demonstration. A title like “This AI Trick Guarantees 10,000 Views” is not. We do not promise outcomes we cannot prove.

Put your chosen ideas into your normal content tracker with a short note explaining which recurring question inspired each one. Clear the temporary Comment Inbox after you have reviewed and transferred the useful themes. Keep the final idea list, not a permanent archive of people's raw comments.

**[5:20–5:55 | A-roll outro; gold logo reveal.]**

That’s the loop: find questions, remove identifying details, deduplicate, ask AI for structured options, and make the final call yourself. You do not need another paid subscription to start listening to your audience more systematically. If you want practical, proof-first AI workflows, follow Automation Empire. Your next useful video might already be waiting in the questions people are asking.

## Two distinct Shorts

### Short 1 — “Your Next Video Is Already in Your Comments”
**Target:** 35–45 seconds, vertical 9:16.

**Hook (0–3s):** “Stop staring at a blank content calendar. Your viewers may already be telling you what to make.”

**Script:**  
Open YouTube Studio and go to your published comments. Filter for questions. Look for the same problem appearing more than once—not one random comment, a pattern. Copy a small batch of questions from your own channel, remove names and personal details, and group similar requests. Ask your AI assistant to turn those anonymized themes into ten original tutorial ideas. Then check every idea: can you actually demonstrate it? No guaranteed-growth claims, no copying, and no need for a paid AI API. Follow Automation Empire for practical workflows.

**Visual sequence:**  
1. Blank calendar, then comment bubbles appear.
2. YouTube Studio question filter, with all names blurred.
3. Three repeated questions collapse into one theme card.
4. Ten idea cards appear; presenter selects one.
5. Blue-and-gold end card.

**Short description:** Your comments can reveal useful tutorial questions. Learn a simple, privacy-conscious way to turn recurring questions into original video ideas. Review and anonymize comments before using an AI assistant.

### Short 2 — “Stop Copying Every Comment Into ChatGPT”
**Target:** 35–45 seconds, vertical 9:16.

**Hook (0–3s):** “You don't need to paste a whole comment section into AI.”

**Script:**  
Make one Google Sheet with a Comment Inbox tab. Paste only a few reviewed questions from your own channel. A tiny Apps Script menu can remove obvious emails, links, phone patterns and @handles, then deduplicate repeated text and build a clean prompt. Inspect it yourself—automatic cleanup is not perfect. Copy only neutral, anonymized themes into your AI chat. Keep the raw comments temporary, and clear the inbox when you finish. The AI suggests options; you decide what is accurate and worth filming.

**Visual sequence:**  
1. Messy comment list slides off-screen.
2. Clean one-column Google Sheet appears.
3. “REMOVE → DEDUPE → PROMPT” animation.
4. Prompt card appears with “Human review required.”
5. Presenter points to “You choose the idea.”

**Short description:** A lightweight Google Sheets + Apps Script helper prepares a reviewed prompt without an AI API call. It does not auto-reply, profile viewers, or publish content.

## Titles, description and SEO

### Primary title
**Turn YouTube Comments Into Your Next 10 Video Ideas (No Paid AI API)**

### Alternate title tests
- Stop Guessing What to Post — Mine Your Comments
- Your Next Video Is Hiding in Your Comments
- Build a Free Creator Feedback Loop With YouTube + Sheets

### YouTube description
Your next useful tutorial may already be hiding in the questions viewers leave under your videos. In this Automation Empire walkthrough, you'll use YouTube Studio, Google Sheets, a small Apps Script custom menu, and an AI chat you use manually to turn reviewed, anonymized questions into a practical video idea list.

You'll learn how to:
- Find questions in your own YouTube Studio comments
- Prepare a small, reviewed comment inbox
- Remove obvious identifying patterns and exact duplicates
- Build a structured AI prompt without calling a paid AI API
- Review ideas for usefulness, proof, and originality

Important: the cleanup script is not a guarantee of anonymization. Inspect and paraphrase comments before sharing them with any AI service. Do not collect usernames or profile details. This is a draft workflow, not an automatic comment-reply or publishing bot. Tool limits and Google quotas can change.

Follow Automation Empire for practical, proof-first AI automation tutorials.

### Hashtags
#YouTubeAutomation #AIAutomation #ContentStrategy #GoogleSheets #AppsScript #CreatorTools #AutomationEmpire

### Search tags
youtube comment ideas, youtube studio questions filter, content ideas from comments, google sheets apps script, creator workflow, ai content planning, youtube creator tips, no paid ai api, audience feedback workflow, automation empire

## Production and visual direction

### Thumbnail A — “YOUR NEXT VIDEO IS IN HERE”
- 16:9 composition, deep navy background with electric-blue UI accents and gold highlights.
- Use the user's actual approved digital-twin likeness on the right, surprised/open-mouth expression, eyes toward a large comment bubble.
- Left side: large readable text “YOUR NEXT VIDEO IS IN HERE”.
- Three small anonymized question bubbles flow into a bright gold idea bulb.
- No fake view counts, no competitor faces, no stock presenter.

### Thumbnail B — “STOP GUESSING WHAT TO POST”
- 16:9 split composition with the user's digital twin on the left, pointing toward three stacked question cards.
- Right side: the cards transform into a tidy grid of ten idea tiles.
- Large hook text “STOP GUESSING WHAT TO POST”; blue/gold palette, strong contrast, uncluttered.
- Change the pose and layout from A so the concepts are genuinely testable alternatives.

### Shot list
1. Presenter hook with clean navy/gold background.
2. YouTube Studio comments interface using a demo account or synthetic sample; blur all names and profile images.
3. Spreadsheet with synthetic comments only.
4. Apps Script editor with highlighted functions.
5. AI Prompt tab showing neutral sample questions.
6. Three-check decision graphic: USEFUL / DEMONSTRABLE / ORIGINAL.
7. Branded outro.

### Audio and edit
- Use the user's cloned voice only if the no-cost route is confirmed.
- Energetic, clear pacing; keep captions readable and do not cover UI controls.
- Subtle original technology bed only if it is already available at no cost.
- Do not generate a new video, voiceover, music track, or thumbnail until its cost is verified as $0.

## Demo Apps Script — source only, not installed

Create a test spreadsheet with two tabs named Comment Inbox and AI Prompt. Paste reviewed, non-identifying comment text into Comment Inbox column A, rows 2–51, one item per row. Attach this script through Extensions → Apps Script. It uses only the current spreadsheet; it makes no network calls and sends nothing to an AI service.

~~~javascript
function onOpen() {
  SpreadsheetApp.getUi()
    .createMenu('Automation Empire')
    .addItem('Set up comment miner', 'setupCommentMiner')
    .addItem('Build sanitized prompt', 'buildCommentPrompt')
    .addSeparator()
    .addItem('Clear temporary inbox', 'clearCommentInbox')
    .addToUi();
}

function setupCommentMiner() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();

  let inbox = ss.getSheetByName('Comment Inbox');
  if (!inbox) inbox = ss.insertSheet('Comment Inbox');
  if (inbox.getLastRow() === 0) {
    inbox.getRange('A1').setValue('Reviewed comment text only — one item per row');
  }

  let output = ss.getSheetByName('AI Prompt');
  if (!output) output = ss.insertSheet('AI Prompt');
  if (output.getLastRow() === 0) {
    output.getRange('A1').setValue('The reviewed prompt will appear here.');
  }

  SpreadsheetApp.getUi().alert(
    'Setup ready. Paste reviewed, non-identifying comments into Comment Inbox column A, rows 2–51.'
  );
}

function buildCommentPrompt() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const inbox = ss.getSheetByName('Comment Inbox');

  if (!inbox) {
    throw new Error('Run Set up comment miner first.');
  }

  const lastRow = Math.min(inbox.getLastRow(), 51);
  if (lastRow < 2) {
    SpreadsheetApp.getUi().alert('No comment rows found. Paste reviewed examples first.');
    return;
  }

  const raw = inbox.getRange(2, 1, lastRow - 1, 1)
    .getDisplayValues()
    .flat();

  const cleaned = Array.from(new Set(
    raw.map(sanitizeComment).filter(Boolean)
  )).slice(0, 50);

  if (cleaned.length === 0) {
    SpreadsheetApp.getUi().alert('No usable text remained after cleanup.');
    return;
  }

  const prompt = [
    'You are a practical YouTube audience-research assistant.',
    'Use only the anonymized excerpts below.',
    'Do not infer commenter identities, demographics, sensitive traits, or private circumstances.',
    'Group repeated questions and describe the problem each group reveals.',
    'Suggest 10 original tutorial ideas for a practical AI automation channel.',
    'For each idea provide: working title, audience problem, honest promise, demo steps, long-form or Short fit, and which supplied theme inspired it.',
    'Do not invent search volume, audience statistics, views, or performance guarantees.',
    '',
    'ANONYMIZED EXCERPTS:',
    cleaned.map((comment, index) => (index + 1) + '. ' + comment).join('\n')
  ].join('\n');

  let output = ss.getSheetByName('AI Prompt');
  if (!output) output = ss.insertSheet('AI Prompt');

  output.clearContents();
  output.getRange('A1').setValue(prompt);
  output.setColumnWidth(1, 700);
  output.getRange('A1').setWrap(true);

  SpreadsheetApp.getUi().alert(
    'Prompt built. Inspect it for identifying details before copying anything to an AI chat.'
  );
}

function sanitizeComment(value) {
  return String(value || '')
    .replace(/[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}/gi, '[email removed]')
    .replace(/https?:\/\/\S+/gi, '[link removed]')
    .replace(/\b(?:\+?\d[\d\s().-]{7,}\d)\b/g, '[phone removed]')
    .replace(/@\w+/g, '[username removed]')
    .replace(/\s+/g, ' ')
    .trim();
}

function clearCommentInbox() {
  const ui = SpreadsheetApp.getUi();
  const answer = ui.alert(
    'Clear temporary comments?',
    'This clears only Comment Inbox!A2:A51. Continue?',
    ui.ButtonSet.YES_NO
  );

  if (answer !== ui.Button.YES) return;

  const inbox = SpreadsheetApp.getActiveSpreadsheet()
    .getSheetByName('Comment Inbox');

  if (inbox) inbox.getRange('A2:A51').clearContent();
  ui.alert('Temporary comment rows cleared.');
}
~~~

### Setup and safety notes
1. Test on a duplicate spreadsheet, not the live production tracker.
2. In YouTube Studio, use the Published comments view and its question/search filters. Do not export or collect usernames, profile URLs, email addresses, or personal details.
3. Review and paraphrase comments before pasting them. The regex cleanup is only a basic safeguard and cannot guarantee anonymity.
4. The script does not call YouTube's API, Firecrawl, Exa, vidIQ, or an AI API. It does not send email, reply to comments, change moderation, or publish.
5. The custom menu requires a spreadsheet-bound script and appears when the spreadsheet is opened in the editor. Google may ask you to authorize the script to edit the current spreadsheet.
6. After extracting themes, use the menu's Clear temporary inbox action. Keep only the creator's final, original ideas.
7. Do not add a time trigger. Manual review is intentional.

## Research notes and source links

1. YouTube Help — [Review and reply to comments](https://support.google.com/youtube/answer/9482367?hl=en): YouTube Studio's Community area includes Published and Held tabs and filters for search, questions, response status, and content type.
2. Google Apps Script — [Custom menus in Google Workspace](https://developers.google.com/apps-script/guides/menus): bound scripts can add custom menu items that run named functions.
3. Google Apps Script — [Simple triggers](https://developers.google.com/apps-script/guides/triggers): onOpen(e) runs when an editor opens a spreadsheet and is commonly used to add a custom menu.
4. Google Apps Script — [Quotas for Google services](https://developers.google.com/apps-script/guides/services/quotas): Apps Script quotas and execution limits vary by account type and can change.
5. YouTube — [Developer policies](https://developers.google.com/youtube/terms/developer-policies): privacy, user control, data minimization, and restrictions on identifying or tracking users.
6. YouTube Data API — [CommentThreads: list](https://developers.google.com/youtube/data/reference/rest/v3/commentThreads/list): optional future API extension; supports up to 100 threads per page and costs 1 quota unit per call. This API route is not used in the no-credit demo.
7. YouTube Data API — [Quota calculator](https://developers.google.com/youtube/data/determine_quota_cost): default quota allocations and per-method costs; project quotas can vary.

## Production checklist

- [ ] Review the long-form script and both Shorts.
- [ ] Confirm all demonstrations use synthetic or properly anonymized examples.
- [ ] Test the Apps Script on a duplicate spreadsheet.
- [ ] Verify the menu appears and the cleanup behaves as described.
- [ ] Inspect the prompt output manually before sharing it with an AI assistant.
- [ ] Select thumbnail A or B; use the user's approved twin only after a $0 rendering route is verified.
- [ ] Use the user's cloned voice only after a $0 route is verified.
- [ ] Review captions, spelling, audio, and all UI labels.
- [ ] Keep all assets in draft/review; do not upload, schedule, or publish without the separate approval required for release.

## Status and approval

**Package ID:** AE-2026-11-05-YT-COMMENT-IDEA-MINER  
**Status:** Draft ready for review  
**Rendering:** Not started  
**Publishing/scheduling:** Not performed  
**Live spreadsheet installation:** Not performed  
**Account comment collection:** Not performed  
**Cost:** No Exa, Firecrawl, vidIQ, HeyGen, or image-generation credits used.

**Approval needed:** script/title review, thumbnail A or B, and confirmation of a genuinely $0 production route before any digital-twin video render.
