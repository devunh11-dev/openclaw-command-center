# Fourth Content Package — 2026-11-02

## Working title
Make vs Zapier Free: 1,000 Credits vs 100 Tasks (2026)

## Audience
Solo creators, small businesses, and beginner AI-automation builders who want a useful workflow without accidentally triggering a paid plan, running out of usage, or sending large video files through the wrong service.

## Core promise
Explain the real difference between Make credits and Zapier tasks, then demonstrate a small human-reviewed idea-to-draft workflow that stays inside published free-plan limits. The video does not claim that AI generation, every integration, or unlimited automation is free.

## Fresh angle and non-duplication
This package is distinct from the previous Automation Empire topics:
- The AI content workflow overview explained the production pipeline.
- The quality-gate package covered pre-render checks and FFprobe.
- The Google Sheets brief-builder package automated prompt assembly.
- This package explains how free automation plans meter usage, how bundles multiply Make operations, how Zapier counts successful actions, and which tool fits a specific workflow.

The central teaching point is that 1,000 Make credits and 100 Zapier tasks are not directly comparable units. The counting rules and workflow limits matter more than the headline numbers.

## Research notes

### Make — official plan and usage rules
- Make's official pricing page lists the Free plan at up to 1,000 credits per month, a maximum of 2 active scenarios, a 15-minute minimum interval between scheduled runs, a 5-minute maximum scenario execution time, and a 5 MB maximum file size. Routers and filters are listed among the Free-plan workflow features.
- Make states that credits are the billing unit and that most actions consume 1 credit, while some advanced features using Make's AI Provider may consume more.
- Make's official Operations guide defines an operation as a module run. A trigger module runs once to check for or retrieve data; downstream modules can run once for each bundle. Its worked example shows 1 trigger operation plus 3 downstream modules processing 10 bundles each, for 31 operations in that run.
- Practical implication: a 1,000-credit monthly allowance does not mean 1,000 complete multi-step workflow runs. Bundle counts and the number/type of modules change consumption.
- Practical implication for video creators: the Free-plan 5 MB file-size limit makes Make a poor place to move full MP4 files. Keep large media in Drive or the video platform and pass links and metadata through the automation instead.

### Zapier — official Free-plan and task rules
- Zapier's official Free-plan article lists 100 tasks per month, two-step Zaps (one trigger plus one action), one user, and a 15-minute polling interval for polling triggers.
- Zapier's task-usage article says successful action steps count as tasks. Trigger steps, filters, paths, and editor testing do not count as tasks. Some products have their own rates; a successful Zapier MCP tool call currently uses 2 tasks.
- Zapier's trigger guide confirms that Free polling triggers check every 15 minutes. Instant triggers use webhooks where supported, so not every trigger has the same delay.
- Recording note: Zapier's task-usage article says Next Gen Zaps and the SDK begin task billing on December 1, 2026. Re-check this notice if recording or publishing after that date.

### Read-only account audit for this package
- The connected Make organization reports the Free plan, a 1,000 monthly operation allowance, 0 consumed in the current cycle, and automatic extra-credit purchasing disabled. The official public pricing page now labels the billing unit as credits; explain that terminology carefully rather than treating operations and credits as universally interchangeable.
- The connected Make workspace currently has no active scenarios. The existing scenarios returned by the read-only inventory are inactive. No scenario was created, activated, edited, or run for this package.
- The connected Zapier toolkit was not active, so the user's own Zapier plan and usage could not be verified. The comparison uses only Zapier's current public official documentation; do not imply the user's Zapier account is on Free.
- HeyGen session audit found no session currently rendering. The existing launch video is completed at 46.7 seconds; the earlier business-tutorial render failed because the free-tier video quota was exhausted. No new render was started.
- vidIQ balance was 0, so no vidIQ research or generation was used.
- Firecrawl's read-only balance check returned 484 of 1,000 credits remaining. No Firecrawl search or scrape was run because the user prohibited credit spend.
- Exa does not expose a zero-cost balance check in the connected tool description. No Exa search or fetch was run because its per-call credit cost could not be confirmed as zero.
- Public official vendor documentation was reviewed for this package. No paid research credits, AI API calls, video/image generations, subscriptions, publishing, scheduling, or public-setting changes were made.

### Sources
1. Make pricing and Free-plan limits: https://www.make.com/en/pricing
2. Make operations, bundles, and operation counts: https://help.make.com/operations
3. Zapier Free-plan features: https://help.zapier.com/hc/en-us/articles/32337438839565-What-s-included-in-Zapier-s-Free-plan
4. Zapier task usage, including MCP rates: https://help.zapier.com/hc/en-us/articles/8496196837261-How-is-task-usage-measured-in-Zapier
5. Zapier polling and instant triggers: https://help.zapier.com/hc/en-us/articles/8496244568589-How-Zap-triggers-work

## Script draft

### Opening hook (0:00–0:30)
**Presenter:** user's approved Automation Empire digital twin; cloned voice only if a no-cost generation route is confirmed.

You see these two numbers: one thousand and one hundred.

Make says up to one thousand credits on its Free plan. Zapier says one hundred tasks. So does Make automatically win by ten times?

No. Because credits and tasks are not the same thing.

Today, I'm going to show you what each platform actually counts, build the same simple content-draft idea two different ways, and show you how to avoid a surprise bill.

### The free-plan snapshot (0:30–1:20)
Let's start with the limits.

Make's Free plan lists up to one thousand credits per month, up to two active scenarios, and a fifteen-minute minimum interval for scheduled runs. It also lists a five-megabyte maximum file size.

Zapier's Free plan lists one hundred tasks per month and limits a Zap to two steps: one trigger and one action. Polling triggers check every fifteen minutes.

Both can be useful. Neither is unlimited, and neither should be described as a free, hands-off AI video factory.

### How Make counts (1:20–2:25)
Make measures work through modules and bundles.

A module run is an operation. The trigger checks for new data. If it finds several rows, the modules after the trigger may run once for each row.

Imagine ten new content ideas arrive in one check.

The trigger checks once. Then three downstream modules each process ten rows: create a draft file, update the tracker, and send a private review notification.

That is one trigger operation plus thirty downstream operations: thirty-one operations for that run.

That's why one thousand credits does not mean one thousand full workflow runs. The number of bundles and the modules you use change the total. Most common actions use one credit, but some AI-provider features can use more.

And here's a creator-specific warning: the Make Free plan lists a five-megabyte maximum file size. Do not try to push your full video exports through it. Keep the MP4 in Drive or your video editor and send the link and metadata instead.

### How Zapier counts (2:25–3:20)
Zapier uses tasks.

On the Free plan, you can create a two-step Zap: one trigger and one action. A successful action step uses a task. The trigger itself does not. Filters, paths, and editor tests also do not count as tasks.

So a simple example is: when a new idea row appears in Google Sheets, create one draft file in Google Drive.

If that one action succeeds one hundred times, it uses one hundred tasks, assuming no other task-consuming actions use the same allowance.

One more detail for people using Zapier MCP: the current task-usage guide lists two tasks for each successful MCP tool call. Those calls share the task allowance. Check the current rate before building around MCP.

### Build the same content-draft workflow (3:20–4:35)
Here is the Make version.

Start with a Google Sheets trigger that watches for new idea rows. Add a condition so only rows marked Ready for Draft continue. Create a Markdown or text draft in Google Drive. Update the source row with the Drive link and a Draft Created status. Optionally, send a private review notification.

The AI step is deliberately human-in-the-loop. The automation prepares the brief and stores the draft. You copy the prompt into the AI chat you already use, review the response, and decide what happens next. This example does not call a paid AI API.

For the Zapier Free version, simplify it to one trigger and one action: a new idea row creates one draft file. If you need several separate action steps, that is where the Free-plan two-step limit becomes important.

### Which one should you choose? (4:35–5:25)
Choose Make when you need a small multi-module flow, branching, or a few coordinated updates — and when you can stay within the two-active-scenario and monthly-credit limits.

Choose Zapier Free when one trigger and one action solve the problem and you value a simple setup.

Do not compare one thousand credits to one hundred tasks as if they were identical. Estimate the actual modules, bundles, successful actions, and MCP calls in your own workflow.

Before you switch anything on, check the current plan, set a usage limit, and make sure extra-credit or pay-per-task purchasing is not enabled if your goal is zero dollars.

### Close and CTA (5:25–5:50)
The best free automation is not the one with the biggest number on its pricing page. It is the smallest workflow that reliably does the job without surprising you later.

Start with one trigger, one useful outcome, and a human approval step.

Follow Automation Empire for practical AI workflows that save repetitive work without handing your quality control to a robot.

## Title and metadata

### Primary title
Make vs Zapier Free: 1,000 Credits vs 100 Tasks (2026)

### Alternate titles
- Make Free vs Zapier Free: What Can You Actually Automate for $0?
- Before You Build an AI Workflow, Learn These Free-Plan Limits
- 1,000 Credits Does Not Mean 1,000 Runs — Make Explained

### Description
Make and Zapier both offer Free plans, but their usage limits are counted differently.

In this Automation Empire tutorial, we compare the current public Free-plan limits and build a simple human-reviewed content-draft workflow:

- Make: up to 1,000 credits per month, up to 2 active scenarios, and a 15-minute minimum scheduled interval.
- Zapier: 100 tasks per month, two-step Zaps, and a 15-minute polling interval for polling triggers.
- Make operations can multiply when downstream modules process multiple bundles.
- Zapier successful action steps count as tasks; triggers, filters, paths, and editor tests do not.
- Zapier MCP successful tool calls currently use 2 tasks each.

The numbers are not directly interchangeable. Check the official plan pages before recording or building because limits and billing rules can change.

The demo prepares a draft file and updates a tracker. It does not call a paid AI API, generate a video, or publish content. AI generation remains in the AI chat you choose, with that service's own plan limits.

Official references:
- Make pricing: https://www.make.com/en/pricing
- Make operations: https://help.make.com/operations
- Zapier Free plan: https://help.zapier.com/hc/en-us/articles/32337438839565-What-s-included-in-Zapier-s-Free-plan
- Zapier task usage: https://help.zapier.com/hc/en-us/articles/8496196837261-How-is-task-usage-measured-in-Zapier
- Zapier triggers: https://help.zapier.com/hc/en-us/articles/8496244568589-How-Zap-triggers-work

Follow Automation Empire for practical, original AI automation workflows. No income or growth results are promised.

### Hashtags
#MakeAutomation #Zapier #AIAutomation #FreeTools #NoCodeAutomation #GoogleSheets #ContentCreator #AutomationEmpire

### Search tags
Make free plan 2026, Zapier free plan 2026, Make vs Zapier, Make credits explained, Zapier tasks explained, Make operations bundles, free AI automation, Google Sheets to Google Drive automation, no code content workflow, automation pricing limits, Zapier MCP tasks

### Chapters
00:00 1,000 credits vs 100 tasks
00:30 The real Free-plan limits
01:20 How Make counts credits and bundles
02:25 How Zapier counts tasks
03:20 Build a content-draft workflow
04:35 Which free plan should you choose?
05:25 The safest way to start

## Short 1 — Make credits are not workflow runs

### Working title
1,000 Make Credits Does NOT Mean 1,000 Runs

### Hook
One thousand Make credits does not mean one thousand complete automations.

### Script (35–45 seconds)
One thousand Make credits does not mean one thousand complete automations.

Make counts module runs. The trigger checks for new data, then the modules after it can run once for every row or bundle.

If one check finds ten rows and three modules process each row, that is one trigger operation plus thirty more: thirty-one operations in that run.

So before you build, count the modules and the bundles — not just the headline number.

Keep big MP4 files in Drive and pass links through your automation.

Follow Automation Empire for practical AI workflows.

### Short description
Make usage depends on module runs and bundles. A trigger check can return many rows, multiplying the work in downstream modules. Check the actual credit counter before scaling.

### Short hashtags
#MakeAutomation #MakeCredits #AIAutomation #NoCode #AutomationEmpire

### Visual direction
Vertical 9:16. Open with the user's approved digital twin beside a huge gold “1,000” that flips into “NOT 1,000 RUNS.” Animate one trigger feeding ten row cards, then three downstream module lanes. Finish on a bold “1 + 10 + 10 + 10 = 31” graphic. Use the user's cloned voice only if a no-cost render route is confirmed. Keep the arithmetic large and readable.

## Short 2 — Make vs Zapier Free

### Working title
Make vs Zapier Free in 30 Seconds

### Hook
Make gives you credits. Zapier gives you tasks. Here's why the numbers are not equal.

### Script (35–45 seconds)
Make's Free plan lists up to one thousand credits per month and two active scenarios.

Zapier's Free plan lists one hundred tasks per month and two-step Zaps: one trigger and one action.

Both have fifteen-minute polling or scheduling limits for the relevant trigger types.

But they count differently. Make usage changes with module runs and bundles. Zapier tasks count successful actions, and successful Zapier MCP tool calls currently use two tasks.

Pick the tool that fits the workflow — not the biggest number.

Follow Automation Empire for practical AI workflows.

### Short description
A quick, source-based comparison of Make and Zapier Free plans. Their usage units and workflow limits differ, so 1,000 credits and 100 tasks are not a one-to-one comparison.

### Short hashtags
#MakeVsZapier #ZapierFree #MakeFree #AutomationTips #AutomationEmpire

### Visual direction
Vertical 9:16. Start with the user's approved digital twin centered between a blue Make panel and an orange Zapier panel. Show “1,000 credits” versus “100 tasks,” then stamp “NOT THE SAME UNIT.” Finish with a simple choice card: “Make = small multi-step flow” / “Zapier = one trigger + one action.” Use the cloned voice only if a no-cost render route is confirmed.

## Thumbnail concepts

### Variant A — “1,000 vs 100?”
- Composition: user's own approved face/digital twin centered or slightly right, with a surprised-but-credible expression.
- Exact hook text: 1,000 vs 100?
- Visual: Make logo and blue credit counter on the left; Zapier logo and orange task counter on the right; a gold “NOT THE SAME” strip underneath.
- Palette: midnight navy (#07152B), electric blue (#1777FF), gold (#F5C542), white, with restrained Zapier orange for its side only.
- Typography: bold condensed headline, large numerals, minimal small print.
- Why test it: creates curiosity while the “NOT THE SAME” label avoids implying a direct unit-for-unit comparison.

### Variant B — “CREDITS ≠ RUNS”
- Composition: user's own approved face/digital twin on the left, pointing to a simple flow diagram on the right.
- Exact hook text: CREDITS ≠ RUNS
- Visual: one trigger node, ten row cards, three downstream module lanes, and a gold “31” result.
- Palette and typography: same navy/blue/gold Automation Empire identity as Variant A.
- Why test it: sells the strongest practical insight rather than a generic product comparison.

Both are concepts only. Use the user's actual face/digital twin; do not substitute a stock person. No thumbnail image generation has been run.

## Production plan
- Main video: 16:9, target 5:45–6:00. Use the user's approved digital twin for direct-to-camera sections and cloned voice only if a no-cost generation route is confirmed.
- Screen recording: use a redacted Make workspace or a clean demo workspace. Do not show the user's email, organization ID, private scenario names, or unrelated account data.
- Make demo: show a sample spreadsheet row, a Watch New Rows trigger, a condition for Ready for Draft, a Drive draft-file action, a tracker update, and an optional private review notification. Do not activate a real scenario during this package run.
- Zapier demo: show the one-trigger/one-action version and the official task counter explanation. The user's Zapier account was not connected during this audit, so do not imply a personal Zapier plan or account setting.
- Use a simple bundle animation to explain the 31-operation example. Attribute the example to Make's official Operations documentation.
- Keep full MP4 files out of Make Free's 5 MB file-size limit. Pass Drive URLs and metadata instead.
- Short 1: 9:16, 35–45 seconds, one-trigger/ten-rows/three-module visual.
- Short 2: 9:16, 35–45 seconds, side-by-side Free-plan comparison.
- B-roll: module nodes, bundle cards, task/credit meters, Drive file link, human-review check.
- No paid generated B-roll or thumbnail generation is included. Prefer real screen captures and simple motion graphics.
- If the user's digital twin or cloned-voice render requires paid credits or an unknown quota, stop and use a script-only review pack until a no-cost route is verified.

## Production checklist
- [ ] Approve the working title and script before recording.
- [ ] Re-check Make and Zapier official plan pages on the day of recording; free-plan limits can change.
- [ ] Clearly distinguish Make credits from operations and explain bundle multiplication.
- [ ] Show the 31-operation example accurately: one trigger check plus three downstream modules processing ten bundles each.
- [ ] Clearly distinguish Zapier tasks from Make credits.
- [ ] Show that Zapier triggers, filters, paths, and editor tests do not count as tasks under the cited Classic Zap rules; successful action steps do.
- [ ] Mention that successful Zapier MCP tool calls currently use two tasks each, and verify the rate before publishing.
- [ ] If recording after December 1, 2026, re-check the Next Gen Zaps and SDK billing notice.
- [ ] Do not describe either Free plan as unlimited or every AI feature as free.
- [ ] Keep AI model generation manual or on a separately verified free allowance; do not insert a paid API call.
- [ ] Keep large MP4 files in Drive or the editor; pass links and metadata through Make.
- [ ] Use the user's own approved digital twin and cloned voice only after a no-cost generation route is confirmed.
- [ ] Create both thumbnail variants using the user's actual face; no stock-person substitution.
- [ ] Watch the long-form export and both Shorts; verify facts, captions, audio, pacing, and mobile readability.
- [ ] Keep all assets in draft/review status.
- [ ] Publish or schedule only after explicit approval of the exact asset, destination, and timing.

## Package operations and limitations
- Stable Package ID: AE-2026-11-02-MAKE-ZAPIER-FREE-TIER
- GitHub target: content/2026-11-02-make-vs-zapier-free-plan.md on branch integration/secure-js-tool-plan-20261009.
- Google Sheets target: Automation Empire — Video Production Tracker, tab Sheet1, upsert keyed by Package ID.
- Google Drive target: Automation Empire — Draft Assets/2026-11-02 Make vs Zapier Free — Content Package.md.
- No Make scenario was created or activated. No Zapier workflow was created. No HeyGen or image generation was started. No publishing, scheduling, paid API call, subscription, product listing, or public-setting change was made.
