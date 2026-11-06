<!-- qa:v1 -->
# Automation Empire Content Package — 2026-11-06

**Package ID:** AE-2026-11-06-GITHUB-ACTIONS-CONTENT-QA
**Status:** Draft ready for review
**Rendering / publishing / scheduling:** Not started / not performed
**Presenter:** Use the user's approved digital twin and cloned voice only after a genuinely $0 production route is verified.
**Brand:** Deep navy, electric blue, gold accents, bold mobile-readable typography.

## Working title

Build a Free GitHub Actions Content QA Bot Before You Publish

## Alternate titles

1. Catch Bad YouTube Drafts Before You Upload
2. Automate Your Video Script Checks With GitHub Actions
3. Give Your Content Pipeline a Quality Gate

## Audience and original angle

For solo creators and small teams who store scripts, descriptions, chapters, and production notes in Markdown or GitHub. The existing Automation Empire repository already has a simple GitHub Actions workflow that checks four required headings. This tutorial extends that idea into an opt-in quality gate for stable package IDs, title length, two distinct Shorts, ordered chapters, HTTPS source links, hashtags, and basic credential-pattern tripwires.

It uses Node.js built-ins and GitHub Actions. It makes no AI API call, uses no paid dependency, and does not publish anything. A strict marker allows older briefs to keep passing baseline checks while they are migrated gradually. The lesson extends the existing workflow rather than adding a second competing workflow.

## Script draft

**Target runtime:** 5:50–6:15  
**Format:** 16:9 flagship tutorial, direct-to-camera digital twin, screen recording, animated checklist graphics.  
**Production note:** Script and source-code package only. No video, voice, music, or thumbnail image has been generated.

### Full narration and scene direction

**[0:00–0:28 | A-roll hook; show a polished draft card, then reveal missing chapters and a missing Short]**

You can have a great video idea, a strong script, and a beautiful thumbnail—and still send a broken package into production. Maybe the title is too long. Maybe the chapters are missing. Maybe you forgot the second Short. Or maybe a draft accidentally contains a credential that should never have been committed.

Today, we're going to make GitHub catch the obvious mistakes before a human approves the video.

**[0:28–1:00 | B-roll: GitHub repository, content folder, green check and red warning icons]**

This is a content quality gate. It is not an AI agent, and it will not decide whether your video is entertaining. It checks rules you define: required sections, a unique package ID, chapter order, source links, and basic safety patterns.

The advantage is consistency. You do not have to remember the same checklist every time you prepare a new video.

**[1:00–1:42 | Screen recording: open the existing content-pipeline workflow]**

Start with the workflow you already have. In our Automation Empire repository, the current GitHub Actions job runs when content Markdown changes. It checks for a title section, a script draft, and a production checklist.

That is a useful first gate, but it cannot tell whether your package has two separate Shorts, whether chapter times move forward, or whether the title is within your own limit. We are going to extend that workflow instead of creating a second workflow beside it.

**[1:42–2:18 | Motion graphic: a content contract appears as checklist items]**

First, define the content contract. Every new package opts into stronger checks with one small marker at the top of its Markdown file. Then it includes a stable package ID, one working title, a script, two Shorts, chapters, source links, hashtags, and a production checklist.

Why opt in? Because older documents may use a different format. You should not turn on strict rules for every old file until you have migrated those files. An opt-in marker lets you improve one package at a time.

**[2:18–3:32 | Screen recording: create scripts/validate-content.mjs; highlight the checks]**

Next, add a tiny Node script. No package installation, no API key, and no external service. It reads one Markdown file and checks the structure.

It confirms the required headings. For a new-format package, it checks the package ID format and title length. It looks for both Short headings. It reads the chapter list and makes sure timestamps increase. It checks that the source section contains secure HTTPS links and that the hashtag section is not empty.

There is also a small tripwire for common credential shapes. That is not a secret scanner, and it can never replace GitHub's own secret-scanning protections.

**[3:32–4:20 | Screen recording: show the GitHub Actions YAML; highlight paths and permissions]**

Now connect the script to GitHub Actions. Keep the trigger narrow: run it when content, the validator, or this workflow changes. Give the job only read access to repository contents. A quality checker does not need permission to push code, publish a release, or change a channel.

The workflow checks out the repository, finds the Markdown packages, and runs the Node validator on each file. If a check fails, GitHub shows an error annotation in the run. That tells you what to fix before the draft moves forward.

**[4:20–5:02 | Demo: intentionally remove a Short heading and move a chapter backwards]**

Let's test it. First, remove the Short Two heading. The validator fails and points to the missing section. Restore it. Next, move a chapter timestamp backwards. It fails again. Put the chapter back in order and run the check one more time.

This is the important part: the workflow is not claiming the script is good. It is confirming that the package meets the structure you agreed to.

**[5:02–5:42 | Security and cost graphic: read-only token, public runner, no API key]**

A few guardrails matter. Do not put API keys in the Markdown file. Do not give this job write permissions. Pin third-party Actions to a verified full commit SHA when you harden the workflow, and review updates before changing that pin.

GitHub documents that standard hosted runners are free for public repositories. Private repositories have plan allowances and possible charges after those allowances are exceeded, so check your billing settings before scaling. This example makes no AI API calls and installs no paid dependency.

**[5:42–6:10 | A-roll recap; blue-and-gold Automation Empire end card]**

That is your content QA gate: define the rules, validate the draft, run the check automatically, and keep the final creative decision with a person.

Your automation should catch preventable mistakes—not take control of your publishing account. Follow Automation Empire for practical AI workflows you can actually test.

## Two distinct Shorts

### Short 1 — Your YouTube Script Should Fail a Test

**Target:** 35–45 seconds, vertical 9:16.

**Hook:** "Your video script should be able to fail a test."

**Script:**

Before you upload, make your content package pass a checklist automatically.

Give every draft a package ID. Require a title, a full script, two separate Shorts, ordered chapters, source links, and a production checklist.

Then let GitHub Actions check those rules every time the Markdown changes.

If the second Short is missing, the check fails. If chapter times go backwards, the check fails.

That does not make the video creative. It makes the handoff more reliable.

**Visual sequence:** Presenter hook; checklist cards appear; missing Short Two turns the status red; restored heading turns it green; end card reads "CHECK THE DRAFT BEFORE THE UPLOAD."

**Short description:** A simple GitHub Actions quality gate can catch missing sections and chapter-order mistakes before a video package reaches production. It checks structure, not creativity or factual accuracy.

### Short 2 — Your QA Bot Does Not Need Admin Access

**Target:** 35–45 seconds, vertical 9:16.

**Hook:** "Why does a content checker need permission to change your repository?"

**Script:**

If your GitHub Actions job only reads Markdown and checks a script, it does not need write access.

Set the workflow token to read-only for repository contents.

That way, the job can inspect your content and report errors, but it cannot push a commit or change your files.

Use the smallest permission that gets the job done. Then review third-party Actions and pin them to verified commit SHAs.

A quality check should be a guardrail, not an administrator.

**Visual sequence:** An oversized ADMIN key appears; it shrinks into a READ ONLY badge; "Read files" is checked while "Push changes" is blocked; show a full-SHA pinning graphic; end card reads "LEAST PRIVILEGE. BETTER AUTOMATION."

**Short description:** A GitHub Actions content validator can usually work with read-only repository permissions. Give automation only the access its task requires.

## Content contract example

A new package opts into stronger checks by placing this marker at the top. Legacy packages without it receive only baseline heading checks until migrated.

~~~markdown
<!-- qa:v1 -->
# Automation Empire Content Package

**Package ID:** AE-2026-11-06-GITHUB-ACTIONS-CONTENT-QA

## Working title
Build a Free GitHub Actions Content QA Bot Before You Publish

## Script draft
Full narration goes here.

## Two distinct Shorts
### Short 1 — Your YouTube Script Should Fail a Test
Script and visuals go here.

### Short 2 — Your QA Bot Does Not Need Admin Access
Script and visuals go here.

## YouTube description
Description goes here.

## Chapters
- 0:00 — The problem
- 0:30 — The content gate
- 1:00 — Define the contract
- 2:18 — Build the validator
- 3:32 — Connect GitHub Actions
- 4:20 — Test failures
- 5:02 — Security and cost
- 5:42 — Recap

## Hashtags
#GitHubActions #ContentAutomation #YouTubeWorkflow #AutomationEmpire

## Research notes and source links
- [GitHub Actions workflow syntax](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
- [GitHub Actions workflow commands](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-commands)
- [Secure use reference](https://docs.github.com/en/actions/reference/security/secure-use)

## Production checklist
- Review script and factual claims.
- Check both Shorts independently.
- Review thumbnails and captions.
- Keep publishing approval separate.
~~~

## Demo validator source

Save this as **scripts/validate-content.mjs** in a test branch. It uses Node.js built-ins and does not call a network service.

~~~javascript
import { readFileSync } from "node:fs";

const file = process.argv[2];

if (!file) {
  console.error("Usage: node scripts/validate-content.mjs <markdown-file>");
  process.exit(2);
}

const text = readFileSync(file, "utf8");
const lines = text.split(/\r?\n/);
const errors = [];

function requireHeading(name) {
  if (!lines.includes("## " + name)) {
    errors.push("Missing required heading: ## " + name);
  }
}

[
  "Working title",
  "Script draft",
  "Production checklist"
].forEach(requireHeading);

const strictMode = text.includes("<!-- qa:v1 -->");

if (strictMode) {
  const idIsValid =
    /^\*\*Package ID:\*\*\s*AE-\d{4}-\d{2}-\d{2}-[A-Z0-9-]+\s*$/m.test(text);

  if (!idIsValid) {
    errors.push("Missing or invalid stable Package ID.");
  }

  const titleMatch =
    text.match(/^## Working title\s*\r?\n+([^\r\n]+)/m);

  if (!titleMatch) {
    errors.push("Working title must be the first line after its heading.");
  } else if (titleMatch[1].trim().length > 70) {
    errors.push("Working title exceeds the 70-character house limit.");
  }

  [
    "Two distinct Shorts",
    "YouTube description",
    "Chapters",
    "Hashtags",
    "Research notes and source links"
  ].forEach(requireHeading);

  if (!/^### Short 1\b/m.test(text)) {
    errors.push("Missing the Short 1 section.");
  }

  if (!/^### Short 2\b/m.test(text)) {
    errors.push("Missing the Short 2 section.");
  }

  const chapterSection =
    (text.split("## Chapters")[1] || "").split(/\r?\n## /)[0];

  const chapters = [
    ...chapterSection.matchAll(
      /^\s*-\s*(\d{1,2}):([0-5]\d)\s+—\s+\S.+$/gm
    )
  ];

  if (chapters.length < 4) {
    errors.push("Add at least four ordered chapter timestamps.");
  }

  let previousSeconds = -1;

  for (const chapter of chapters) {
    const seconds = Number(chapter[1]) * 60 + Number(chapter[2]);

    if (seconds <= previousSeconds) {
      errors.push("Chapter timestamps must increase strictly.");
      break;
    }

    previousSeconds = seconds;
  }

  const sourceSection =
    (text.split("## Research notes and source links")[1] || "").split(/\r?\n## /)[0];

  const sourceLinks = [
    ...sourceSection.matchAll(/\[[^\]]+\]\(https:\/\/[^)\s]+\)/g)
  ];

  if (sourceLinks.length < 3) {
    errors.push("Add at least three HTTPS source links.");
  }

  const hashtagSection =
    (text.split("## Hashtags")[1] || "").split(/\r?\n## /)[0];

  const hashtags = hashtagSection.match(/#[A-Za-z0-9_]+/g) || [];

  if (hashtags.length < 3) {
    errors.push("Add at least three hashtags.");
  }

  const secretPatterns = [
    /ghp_[A-Za-z0-9]{30,}/,
    /github_pat_[A-Za-z0-9_]{40,}/,
    /sk-[A-Za-z0-9]{20,}/,
    /xox[baprs]-[A-Za-z0-9-]{20,}/,
    /-----BEGIN (RSA )?PRIVATE KEY-----/
  ];

  if (secretPatterns.some((pattern) => pattern.test(text))) {
    errors.push("Possible credential pattern found. Inspect locally; do not print secrets.");
  }
}

if (errors.length > 0) {
  for (const error of errors) {
    console.error("::error file=" + file + "::" + error);
  }

  process.exitCode = 1;
} else {
  console.log(
    strictMode
      ? "Strict content package checks passed: " + file
      : "Legacy baseline checks passed: " + file
  );
}
~~~

**Validator limitations:** This is a deterministic structural check, not a complete Markdown parser, URL reachability test, plagiarism checker, fact checker, or secret scanner. Credential patterns are only a basic tripwire and can produce false positives or miss unknown formats. The repository's GitHub secret scanning and push protection are separate safeguards.

## GitHub Actions workflow example

Extend the existing **.github/workflows/content-pipeline.yml** rather than adding a second workflow with duplicate triggers. This is a teaching example for a test branch; it is not installed by this content-package commit.

~~~yaml
name: Automation Empire content QA

on:
  push:
    paths:
      - "content/**/*.md"
      - "scripts/validate-content.mjs"
      - ".github/workflows/content-pipeline.yml"
  pull_request:
    paths:
      - "content/**/*.md"
      - "scripts/validate-content.mjs"
      - ".github/workflows/content-pipeline.yml"
  workflow_dispatch:

permissions:
  contents: read

jobs:
  validate-content:
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: Check out repository
        uses: actions/checkout@v4

      - name: Validate content packages
        shell: bash
        run: |
          set -euo pipefail

          while IFS= read -r -d '' file; do
            node scripts/validate-content.mjs "$file"
          done < <(find content -type f -name '*.md' -print0)
~~~

**Supply-chain note:** The sample uses the familiar checkout major-version tag for readability. Before using it in a hardened production workflow, verify the official action release and pin the dependency to its full commit SHA. Do not copy an unverified SHA from a tutorial. Review future dependency updates deliberately.

## Local test plan

Run these commands from the repository root on a test branch:

~~~bash
node --version
node scripts/validate-content.mjs content/2026-11-06-github-actions-content-qa.md
~~~

Then test the failure path on a temporary copy:
1. Remove the Short 2 heading; the strict validator should fail.
2. Restore it and move one chapter timestamp backwards; the validator should fail.
3. Restore the timestamp and remove one source link; the validator should fail if fewer than three remain.
4. Run the validator again; the package should pass.
5. Open a pull request and confirm that the check appears before merge.

Do not test by adding fake secrets to the real repository. Use harmless dummy patterns only in a disposable local file, and never push those patterns to GitHub.

## YouTube description

A great video package can still fail before production: missing chapters, an absent Short, an overlong title, or a forgotten production checklist. In this Automation Empire tutorial, we'll extend a simple GitHub Actions check into a practical content QA gate using Markdown, Node.js, and a read-only GitHub token.

You'll learn how to define a content package contract, validate a stable package ID, check two Shorts, verify chapter order, require HTTPS source links, and surface failures directly in GitHub Actions.

This example uses Node.js built-ins and makes no AI API calls. It is a structural checker, not a creativity score, fact checker, or complete security scanner. Review every draft yourself, and keep publishing approval separate from automated validation.

GitHub Actions allowances vary by repository visibility and plan. Standard hosted runners are free for public repositories; private-repository usage is subject to included allowances and billing rules. Check your account before increasing run frequency.

Follow Automation Empire for practical AI workflows you can test and verify.

## Chapters

- 0:00 — Why good drafts still fail
- 0:28 — What a content QA gate checks
- 1:00 — Inspect the existing workflow
- 1:42 — Define the content contract
- 2:18 — Build the Node validator
- 3:32 — Connect GitHub Actions
- 4:20 — Test a broken package
- 5:02 — Security and cost guardrails
- 5:42 — Recap and next step

## Hashtags

#GitHubActions #ContentAutomation #YouTubeWorkflow #NodeJS #Markdown #CreatorTools #AutomationEmpire

## Search tags

GitHub Actions tutorial, automate content quality checks, YouTube script checklist, content QA automation, GitHub Actions Markdown validator, Node.js workflow, creator workflow automation, content pipeline, read only GitHub token, Automation Empire

## Thumbnail concepts

### Thumbnail A — CATCH BAD DRAFTS BEFORE UPLOAD

- **Composition:** 16:9. Deep navy background with electric-blue panels and gold edge lighting.
- **Presenter:** The user's actual approved digital-twin likeness on the right, surprised/open-mouth expression, eyes toward a large draft card.
- **Text:** Left side, three-line hook: "CATCH BAD / DRAFTS / BEFORE UPLOAD". Keep every word large and readable on a phone.
- **Visual:** A script card with two red X marks for missing chapters and a missing Short Two; a gold checkmark appears after the fix.
- **Signature:** Small Automation Empire gold emblem in the lower-right safe area.
- **Honesty:** Do not show fake views, fake GitHub status counts, or fabricated success metrics.

### Thumbnail B — YOUR SCRIPT NEEDS A TEST

- **Composition:** 16:9 split layout, distinct from A.
- **Presenter:** The user's approved digital twin on the left, pointing toward two large test cards.
- **Text:** "YOUR SCRIPT / NEEDS A TEST" in bold white and gold.
- **Visual:** One red FAIL card with a missing chapter; one green PASS card with an ordered chapter list. Use illustrative labels, not fake production analytics.
- **Signature:** Navy, electric blue, gold accents, consistent type treatment.
- **A/B test hypothesis:** A sells the pain of bad handoffs; B sells the practical automation mechanism.

Both are design briefs only. Do not generate either image until a $0 image-generation route is confirmed. Use the user's actual face reference, never a stock presenter.

## Production checklist

- [ ] Review the narration and confirm every feature shown matches the actual GitHub workflow.
- [ ] Use a disposable test branch for the validator demonstration.
- [ ] Keep the current content-pipeline workflow intact until the replacement is reviewed.
- [ ] Confirm both Shorts stand alone and do not repeat the same explanation.
- [ ] Verify every source link and current pricing statement before recording.
- [ ] Keep the GitHub token read-only for the validation job.
- [ ] Pin third-party Actions to verified full commit SHAs before production use.
- [ ] Do not place real secrets or personal data in the demo.
- [ ] Use the approved digital twin and cloned voice only after a genuinely $0 render route is verified.
- [ ] Create thumbnails only after a genuinely $0 image route is verified.
- [ ] Review captions, spelling, contrast, and safe margins.
- [ ] Keep final upload, scheduling, and public release behind separate user approval.

## Research notes and source links

1. [GitHub Actions workflow syntax](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax) — event path filters, permissions, job configuration, and workflow structure.
2. [GitHub Actions events that trigger workflows](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows) — push, pull request, and manual dispatch behavior.
3. [GitHub Actions workflow commands](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-commands) — error annotations and runner commands.
4. [Secure use reference](https://docs.github.com/en/actions/reference/security/secure-use) — dependency pinning and secure workflow practices.
5. [Managing GitHub Actions settings for a repository](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository) — action policies and full-SHA pinning settings.
6. [GitHub pricing](https://github.com/pricing) — current plan allowances and public-repository Actions pricing.
7. [actions/checkout repository](https://github.com/actions/checkout) — official checkout action source and release information.

## Status and approval

**Package ID:** AE-2026-11-06-GITHUB-ACTIONS-CONTENT-QA  
**Status:** Draft ready for review  
**GitHub Actions workflow:** Existing workflow inspected; no workflow or validator code installed by this package.  
**Drive:** Draft-only storage requested.  
**Tracker:** Upsert by Package ID.  
**Rendering:** Not started.  
**Thumbnail generation:** Not started.  
**Publishing / scheduling:** Not performed.  
**Approval needed:** Script/title review, thumbnail A or B selection, and confirmation of a genuinely $0 production route before using the user's twin, cloned voice, or image generation.
