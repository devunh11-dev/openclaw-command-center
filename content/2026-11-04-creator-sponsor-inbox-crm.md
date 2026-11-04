# Sixth Automation Empire Content Package — 2026-11-04

## Working title

**Turn Your Gmail Into a Creator CRM (No Paid AI API)**

Alternate titles:
1. Stop Losing Sponsor Emails: Build This Gmail + Sheets System
2. A Simple Sponsorship Inbox Workflow for Solo Creators
3. Gmail to Google Sheets: A Human-Reviewed Creator CRM

## Package metadata

- Package ID: AE-2026-11-04-CREATOR-SPONSOR-INBOX-CRM
- Date: 2026-11-04 (UTC)
- Format: one 16:9 flagship video + two independent 9:16 Shorts
- Target runtime: 5:50–6:10
- Audience: solo creators, freelancers, and small digital businesses
- Core promise: organize sponsor enquiries into a searchable follow-up tracker without a paid AI API call
- Production status: draft only; no video or image generation
- Presenter direction: the user's previously approved digital twin and cloned voice, only if a genuinely no-cost render route is confirmed
- Brand direction: Automation Empire; midnight navy, electric blue, gold accents; energetic, clear, credible

## Original angle and accuracy guardrails

This is an inbox-organization workflow, not a promise of sponsorships or income. Gmail labels separate likely sponsor enquiries; a bound Apps Script reads a small, labeled batch and writes limited message metadata into a Google Sheet. An AI assistant can help classify a redacted row, but the script does not call an AI model. No API key, paid model endpoint, automatic reply, or auto-send step is part of this version.

Important permission disclosure: the GmailApp search method used below requires the broad https://mail.google.com/ authorization scope. Although this sample only reads message metadata and writes to the bound spreadsheet, that scope is broader than read-only. Test with a dedicated demo mailbox first. Do not authorize the sample on a sensitive personal inbox unless you are comfortable with the permission request. A Gmail API implementation using a narrower read-only scope would be a separate, more advanced build.

The script deliberately does not read message bodies or attachments, create drafts, send email, delete, archive, mark read, change labels, or forward messages. It logs the sender's domain rather than the full email address. Use synthetic messages for the on-screen demonstration.

Google quotas and service limits can change. The sample searches a maximum of 50 matching threads per run and is intended for a small creator inbox, not bulk email processing.

---

# 1. Flagship YouTube video

## Main title

**Turn Your Gmail Into a Creator CRM (No Paid AI API)**

## Hook alternatives

- “If sponsor emails are getting buried in your inbox, build this simple tracker before you buy another CRM.”
- “Your inbox is where enquiries arrive. It does not have to be where your follow-ups disappear.”
- “You can organize creator enquiries with Gmail, Sheets, and a small script—without paying for an AI API.”

## Script draft

## Full script — target 5:50–6:10

### 0:00–0:25 — Cold open

[Visual: inbox fills with overlapping message cards. One card marked “Partnership enquiry” disappears under newsletters. Cut to a clean Google Sheet with a row appearing.]

**Presenter:**

If you create content, you might eventually get emails about sponsorships, collaborations, products, or paid campaigns. The problem is that those messages arrive in the same inbox as everything else.

And if you rely on memory, a promising enquiry can disappear under a pile of notifications.

Today, I’ll show you a simple creator inbox system using Gmail, Google Sheets, and Google Apps Script. It organizes the messages you label, prevents duplicate rows, and gives you a clean place to review the next step.

No paid AI API is required for this demonstration.

### 0:25–0:55 — What we are actually building

[Visual: three large cards: GMAIL LABEL → SHEETS TRACKER → HUMAN REVIEW.]

**Presenter:**

Here is the workflow.

First, Gmail puts relevant messages under one label. Second, a small script copies limited metadata into a spreadsheet. Third, you review the enquiry and can use your existing AI chat to help summarize a redacted version.

Notice what is not happening: the script is not reading every email, downloading attachments, negotiating a deal, or sending replies. We are building an organized review queue—not an autonomous sales agent.

### 0:55–1:35 — Step one: create a Gmail label

[Screen recording: Gmail settings and labels. Use a clean demo inbox with fake messages.]

**Presenter:**

Start with a dedicated label. In Gmail, create one called “AE Sponsor Inbox.”

For this tutorial, I’m using a test inbox and synthetic messages. I’ll label a few examples with subjects like “Partnership enquiry,” “Creator collaboration,” and “Campaign proposal.”

You can create a filter for words or senders you recognize, then choose the action to apply this label. Start narrow. A filter is a sorting rule, not proof that a message is legitimate or worth accepting.

Do not set this filter to forward, delete, or automatically reply. We only want to label and review.

### 1:35–2:05 — Step two: create the tracker

[Visual: a Google Sheet tab called Sponsor Inbox. Headers animate into place.]

**Presenter:**

Open a copy of a Google Sheet and add a tab named “Sponsor Inbox.”

We’ll track eight fields: the first message ID, last activity, sender domain, subject, Gmail thread link, status, AI notes, and next step.

The first message ID is our deduplication key. If another reply arrives in the same conversation, we update the activity details on the existing row instead of creating another lead.

That means your manual status and notes stay in place.

### 2:05–3:45 — Step three: add the Apps Script

[Screen recording: Extensions → Apps Script. Paste the script from the package and save it.]

**Presenter:**

In the spreadsheet, open Extensions, then Apps Script. Paste the code from this package and save it.

The script checks for the Sponsor Inbox tab, creates the headers if the tab is new, and confirms the headers match before it writes anything.

Then it searches only for messages carrying our label from the last 30 days, with a maximum of 50 threads in this starter version.

For each matching conversation, it reads the first message ID, the latest activity date, the latest sender's domain, the original subject, and the Gmail thread link.

It does not read the message body. It does not open attachments. It does not send anything.

When it finds a message ID that is already in the sheet, it refreshes the metadata columns and leaves your review notes alone. When it finds a new ID, it adds one row marked “Needs review.”

That is the important part: rerunning the script should not keep creating duplicate entries for the same conversation.

### 3:45–4:25 — Step four: test the workflow

[Visual: send a synthetic test message from a second demo account; apply the label; run the script; show one row; run it again.]

**Presenter:**

Before you connect a real inbox, test it.

Send one fake partnership message to your demo inbox. Apply the label. Run the function once and check that one row appears.

Run it again. The row should not duplicate.

Now reply to the same test conversation and run it again. The last activity should update on the existing row, while your status and notes remain unchanged.

If you get zero rows, check the label spelling, the Gmail search query, and whether the message is within the 30-day window.

### 4:25–5:15 — Step five: use AI carefully

[Visual: a sanitized row moves into an AI chat prompt. Personal details blur out.]

**Presenter:**

Now we have a clean review queue.

You can copy a sanitized version of a row into your existing AI assistant and ask it to help classify the enquiry.

Ask for four things: what the sender is requesting, what information is missing, what risks need checking, and a polite reply draft.

Remove personal email addresses, private campaign details, phone numbers, payment information, and anything confidential before using an external AI chat.

And never let a model decide that a message is authentic just because the sender domain looks familiar. Check the sender, links, contract, usage rights, deliverables, deadlines, payment terms, and any request for money or account access yourself.

The AI can help organize your thinking. You make the decision.

### 5:15–5:50 — Permission and quota check

[Visual: permission screen with the Gmail scope highlighted; then a small quota meter.]

**Presenter:**

There is one important permission detail. This example uses GmailApp, and Google's documentation says its search method requires the broad Gmail mail scope. That is more access than the script needs for the limited metadata task shown here.

That is why I recommend a dedicated demo mailbox first. Review the authorization screen before accepting it. If you do not want that broad permission, stop here and use a separate Gmail API read-only implementation instead.

Apps Script also has account-specific quotas and trigger limits. Start with a small batch, run it manually, and check the current quota page before increasing the workload.

### 5:50–6:10 — Recap and CTA

[Visual: three blue-and-gold cards: LABEL → TRACK → REVIEW.]

**Presenter:**

So that is the system: label the enquiries, log the metadata, and review the next action.

It is not a replacement for a real CRM when your operation grows, and it does not guarantee sponsorships. But it gives a solo creator a simple, low-cost starting point.

Follow Automation Empire for practical AI workflows that you can understand, test, and control.

---

## Apps Script demonstration code

Use a duplicate spreadsheet and a dedicated test Gmail account. Create the Gmail label AE_Sponsor_Inbox manually before running this function.

~~~javascript
function syncSponsorInbox() {
  const LABEL = 'AE_Sponsor_Inbox';
  const TAB = 'Sponsor Inbox';
  const HEADERS = [
    'First Message ID',
    'Last Activity',
    'Sender Domain',
    'Subject',
    'Thread URL',
    'Status',
    'AI Notes',
    'Next Step'
  ];

  const ss = SpreadsheetApp.getActiveSpreadsheet();
  let sheet = ss.getSheetByName(TAB);

  if (!sheet) {
    sheet = ss.insertSheet(TAB);
  }

  if (sheet.getLastRow() === 0) {
    sheet.appendRow(HEADERS);
  }

  const currentHeaders = sheet
    .getRange(1, 1, 1, HEADERS.length)
    .getValues()[0];

  if (currentHeaders.join('|') !== HEADERS.join('|')) {
    throw new Error(
      'The Sponsor Inbox headers do not match the expected layout.'
    );
  }

  if (!GmailApp.getUserLabelByName(LABEL)) {
    throw new Error(
      'Create the Gmail label AE_Sponsor_Inbox before syncing.'
    );
  }

  const lastRow = sheet.getLastRow();
  const existingRows = lastRow > 1
    ? sheet.getRange(2, 1, lastRow - 1, HEADERS.length).getValues()
    : [];

  const rowByFirstMessageId = new Map();

  existingRows.forEach((row, index) => {
    const id = String(row[0] || '');
    if (id) {
      rowByFirstMessageId.set(id, index + 2);
    }
  });

  const query = 'label:' + LABEL + ' newer_than:30d';
  const threads = GmailApp.search(query, 0, 50);
  const newRows = [];

  threads.forEach(thread => {
    const messages = thread.getMessages();
    if (!messages.length) return;

    const firstMessageId = messages[0].getId();
    const latestMessage = messages[messages.length - 1];
    const from = latestMessage.getFrom() || '';
    const match = from.match(/@([A-Za-z0-9.-]+\.[A-Za-z]{2,})/);
    const senderDomain = match
      ? match[1].toLowerCase()
      : 'unknown';

    const metadata = [
      thread.getLastMessageDate(),
      senderDomain,
      thread.getFirstMessageSubject(),
      thread.getPermalink()
    ];

    const existingRow = rowByFirstMessageId.get(firstMessageId);

    if (existingRow) {
      // Refresh only metadata; preserve manual status and notes.
      sheet.getRange(existingRow, 2, 1, 4).setValues([metadata]);
    } else {
      newRows.push([
        firstMessageId,
        metadata[0],
        metadata[1],
        metadata[2],
        metadata[3],
        'Needs review',
        '',
        ''
      ]);
      rowByFirstMessageId.set(
        firstMessageId,
        lastRow + newRows.length
      );
    }
  });

  if (newRows.length) {
    const startRow = sheet.getLastRow() + 1;
    sheet
      .getRange(startRow, 1, newRows.length, HEADERS.length)
      .setValues(newRows);
  }

  SpreadsheetApp.flush();
  Logger.log(
    'Sponsor inbox sync complete. New rows: ' + newRows.length
  );
}
~~~

### Optional daily trigger — do not install until the manual test passes

~~~javascript
function installDailySponsorInboxSync() {
  const handler = 'syncSponsorInbox';
  const alreadyInstalled = ScriptApp
    .getProjectTriggers()
    .some(trigger => trigger.getHandlerFunction() === handler);

  if (!alreadyInstalled) {
    ScriptApp.newTrigger(handler)
      .timeBased()
      .everyDays(1)
      .atHour(8)
      .create();
  }
}
~~~

The daily trigger is optional. Apps Script time-driven triggers can run within a randomized time window; an 8 a.m. setting should not be treated as an exact-minute guarantee. Do not install this trigger until the manual test and authorization review are complete.

## AI triage prompt

Paste only sanitized metadata into your existing AI chat:

~~~text
You are helping a solo creator review a possible sponsorship enquiry.

Use only the sanitized information supplied below. Do not invent facts,
claim that a sender is authentic, or assume a campaign is legitimate.

Return:
1. Category: Potential fit / Needs more information / Not a fit / Suspicious.
2. What the sender appears to be asking for.
3. Missing details: deliverables, platform, timeline, usage rights,
   exclusivity, compensation, payment terms, and approval requirements.
4. Red flags to investigate, including unusual links, attachments,
   upfront payment requests, password requests, or pressure.
5. A polite reply draft for a human to review.
6. A recommended next step.

Never send the reply. A human must verify the sender, inspect the
original message safely, approve the terms, and send any response.

Sanitized row:
[PASTE REDACTED SUBJECT, SENDER DOMAIN, AND CONTEXT HERE]
~~~

## Tracker columns and suggested statuses

| Column | Purpose |
|---|---|
| First Message ID | Stable deduplication key |
| Last Activity | Latest conversation activity |
| Sender Domain | Domain only, not full address |
| Subject | Original subject line |
| Thread URL | Link back to the original conversation |
| Status | Needs review / Qualified / Waiting / Declined / Closed |
| AI Notes | Human-reviewed summary |
| Next Step | Owner and follow-up action |

Do not store full message bodies, attachments, private contracts, or payment details in this starter tracker.

---

# 2. Short 1 — 35–40 seconds

## Title

**Stop Losing Sponsor Emails**

## Script

[0:00–0:03]  
“Your inbox is not a CRM—and that is why follow-ups disappear.”

[0:03–0:11]  
“Create one Gmail label called AE Sponsor Inbox. Label the messages that look like partnership or collaboration enquiries.”

[0:11–0:22]  
“Connect a copy of a Google Sheet to a small Apps Script. It logs the message ID, subject, sender domain, date, and thread link.”

[0:22–0:31]  
“Run it again and the same conversation updates instead of creating another row.”

[0:31–0:40]  
“Now you have a review queue. No paid AI API required for the logging step. Follow Automation Empire for practical workflows.”

## Visual plan

- 0–3s: messy inbox; bold hook
- 3–11s: Gmail label appears on a synthetic sponsor email
- 11–22s: row populates in Google Sheets
- 22–31s: second run updates the same row; no duplicate
- 31–40s: blue-and-gold three-step end card

## Short description

A simple Gmail label + Google Sheets + Apps Script workflow can keep creator enquiries organized. Demo uses synthetic emails and logs limited metadata only. Test authorization and quotas before connecting a real inbox.

## Short hashtags

#AutomationEmpire #GmailTips #GoogleSheets #AppsScript #CreatorBusiness

---

# 3. Short 2 — 40–45 seconds

## Title

**Your AI Does Not Need Your Whole Inbox**

## Script

[0:00–0:04]  
“Before you give an AI agent your whole inbox, ask what it actually needs.”

[0:04–0:14]  
“For a simple sponsorship review, start with a labeled message and log only the subject, sender domain, date, and thread link.”

[0:14–0:25]  
“Redact private details. Then ask your existing AI chat to list missing campaign terms, possible red flags, and questions you should ask.”

[0:25–0:36]  
“Keep the original email private. Verify the sender and contract yourself. Never let an AI send a reply or approve a deal automatically.”

[0:36–0:45]  
“Use less data, review every decision, and keep control. Follow Automation Empire.”

## Visual plan

- 0–4s: inbox icon behind a privacy shield
- 4–14s: four metadata fields flow into a sheet; message body stays locked
- 14–25s: redacted row enters a chat prompt
- 25–36s: warning cards: VERIFY / REVIEW / NEVER AUTO-SEND
- 36–45s: Automation Empire blue-and-gold end card

## Short description

A safer AI-assisted inbox workflow starts with less data. This demo uses metadata only, redaction, and human review—not automatic email replies or deal approval.

## Short hashtags

#AutomationEmpire #AIAgents #DataPrivacy #GmailAutomation #HumanInTheLoop

---

# 4. YouTube packaging

## Description

Sponsor and collaboration enquiries can get buried in a busy inbox. In this tutorial, we build a simple creator inbox tracker with Gmail labels, Google Sheets, and Google Apps Script.

You will learn how to:
- Label likely sponsorship enquiries in a dedicated Gmail queue.
- Create a Google Sheets tracker.
- Use Apps Script to log limited message metadata.
- Deduplicate by the first message ID and refresh activity details.
- Use an existing AI chat to help review sanitized information.
- Keep human approval before replies, contracts, or campaign decisions.

Important: this starter script uses GmailApp and requires the broad Gmail authorization scope. It does not read message bodies or attachments, create drafts, send email, or modify messages. Test in a dedicated demo mailbox and review the permission request before authorizing it on a real account. Google Apps Script quotas and service limits can change.

This is an organizational workflow, not a guarantee of sponsorships, income, or campaign acceptance. Tool availability and plan limits vary.

Follow Automation Empire for practical, original AI and automation tutorials.

## Hashtags

#AutomationEmpire #GmailAutomation #GoogleSheets #GoogleAppsScript #CreatorBusiness #AIAutomation #HumanInTheLoop

## Search tags

gmail creator crm, sponsorship email tracker, gmail to google sheets, google apps script gmail, creator sponsorship workflow, gmail labels automation, solo creator tools, ai inbox triage, human in the loop ai, free automation workflow, automation empire

## Pinned comment

Would you rather see the next tutorial build a sponsor follow-up dashboard or a simple campaign deliverables tracker? The demo in this video uses synthetic emails. Review Gmail permissions before connecting a real inbox.

## Chapters

00:00 Why sponsor emails get lost  
00:25 The Gmail-to-Sheets workflow  
00:55 Create the Gmail label  
01:35 Build the tracker  
02:05 Add the Apps Script  
03:45 Test deduplication  
04:25 Use AI with redacted data  
05:15 Gmail permissions and quotas  
05:50 Recap

---

# 5. Thumbnail concepts

Both concepts use the user's own approved digital-twin likeness, not a stock presenter. Use the same face treatment, bold readable type, midnight navy background, electric-blue highlights, and gold accent. Target canvas: 1280 × 720, 16:9, with generous safe margins.

## Concept A — “SPONSOR EMAILS → SHEETS”

- Composition: user's surprised expression on the right third, looking toward a large Gmail envelope transforming into a clean spreadsheet row.
- Main text: “EMAILS → SHEETS”
- Secondary visual: one highlighted message card, one gold arrow, three visible tracker columns.
- Palette: midnight navy, electric blue, warm gold, white text.
- Why test it: communicates the transformation immediately.

## Concept B — “STOP LOSING LEADS”

- Composition: user's face on the left third, pointing toward three large workflow cards on the right.
- Main text: “STOP LOSING LEADS”
- Three cards: LABEL → TRACK → REVIEW.
- Gold accent: a single highlighted follow-up row and small checkmark.
- Why test it: focuses on the creator's pain point rather than the tool names.

## Thumbnail honesty check

Do not show a pile of confirmed sponsor deals, revenue figures, or fake inbox volume. The video demonstrates organization, not a guaranteed business outcome. Use a synthetic inbox screenshot and synthetic company names.

---

# 6. Production and editing plan

## Flagship video

- Aspect ratio: 16:9
- Target runtime: 5:50–6:10
- Presenter: approved personal digital twin and cloned voice, subject to a confirmed no-cost render route
- A-roll: direct-to-camera explanation at hook, transition into build, permission disclosure, and recap
- B-roll: synthetic Gmail inbox, Gmail label setup, blank Google Sheet, Apps Script editor, metadata row, duplicate-run comparison
- Motion graphics: Label → Track → Review; blue-and-gold progress lines; subtle UI callouts
- Captions: large, high contrast, short phrase groups; keep within safe margins
- Audio: clean narration; low-volume instrumental bed only if included at no additional cost
- Screen demo: fake names, fake email domains, no real personal inbox, no credentials, no private contracts

## Shorts

- Vertical 9:16, 1080 × 1920 target
- Keep the first hook inside the central safe area.
- Use distinct scenes; do not simply crop the flagship into two identical clips.
- Short 1 is the workflow transformation.
- Short 2 is the data-minimization and human-review lesson.

## Production checklist

## Quality-control checklist

- [ ] Script approved before generation.
- [ ] Digital twin and cloned voice are the user's approved assets.
- [ ] No-cost generation route verified before rendering.
- [ ] Synthetic inbox and spreadsheet data used.
- [ ] Gmail scope disclosure appears on screen and in description.
- [ ] Code is tested in a duplicate spreadsheet and dedicated demo inbox.
- [ ] Repeated run creates no duplicate first-message IDs.
- [ ] Reply updates metadata without overwriting human notes.
- [ ] No message body or attachment content is copied into the tracker.
- [ ] No email is sent, forwarded, deleted, or automatically drafted.
- [ ] Captions, spelling, audio, and screen recording reviewed.
- [ ] Final video reviewed before any upload.
- [ ] Publishing and scheduling require separate explicit approval.

---

# 7. Research sources

1. GmailApp reference — search, threads, labels, and required authorization scope:  
   https://developers.google.com/apps-script/reference/gmail/gmail-app

2. GmailThread reference — first subject, thread ID, last activity, messages, and permalink:  
   https://developers.google.com/apps-script/reference/gmail/gmail-thread

3. GmailMessage reference — message ID, date, sender, and subject metadata:  
   https://developers.google.com/apps-script/reference/gmail/gmail-message

4. Gmail API filter guide — criteria and actions, including adding labels:  
   https://developers.google.com/workspace/gmail/api/guides/filter_settings

5. Apps Script quotas — account-specific service limits and changing quotas:  
   https://developers.google.com/apps-script/guides/services/quotas

6. Installable triggers — time-driven triggers, authorization, and trigger management:  
   https://developers.google.com/apps-script/guides/triggers/installable

7. SpreadsheetApp reference — spreadsheet and sheet operations:  
   https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet-app

---

# 8. Review and next action

Status: draft package only.

The script and workflow are ready for a test in a duplicate spreadsheet and dedicated demo inbox. The GmailApp version requests broad Gmail authorization even though the sample reads only limited metadata; do not authorize it on a sensitive inbox without reviewing that scope. If narrower read-only permissions are required, build a separate Gmail API version.

The user's digital twin and cloned voice are already the intended presenter assets. No new generation should start unless the route is confirmed to cost $0 and not consume paid or unknown credits.

No email connection was modified, no Gmail filter or Apps Script trigger was installed, no video or image was generated, and nothing was published or scheduled.

Approval needed: review the script and permission disclosure, choose thumbnail A or B, and confirm the no-cost production route before any rendering.
