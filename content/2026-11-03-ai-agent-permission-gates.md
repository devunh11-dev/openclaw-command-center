# Fifth Content Package — 2026-11-03

## Working title
Stop Giving AI Agents Full Access: Build a 3-Level Permission Gate

## Package ID
AE-2026-11-03-AGENT-PERMISSION-GATES

## Audience
Solo creators, small businesses, and people building AI agents or multi-agent workflows with OpenClaw, GitHub Actions, and connected apps. The audience wants useful automation without handing an agent unrestricted access to private files, shells, repositories, or public accounts.

## Core promise
Teach a practical permission ladder for AI agents: **Read → Draft → Approve**. The agent can gather information first, prepare changes in a limited draft area second, and only perform sensitive external actions after a person reviews the exact action. Explain how OpenClaw tool policies, workspace sandboxing, execution approvals, and GitHub Actions token permissions fit together.

## Fresh angle and non-duplication
This package is distinct from the recent Automation Empire topics:
- The AI content workflow overview covered the production pipeline.
- The video quality-gate package covered pre-render checks and FFprobe.
- The Google Sheets brief-builder package covered turning an idea row into a structured prompt.
- The Make vs Zapier package compared free-plan usage units and workflow limits.

This package focuses on **permission boundaries for AI agents**. It is not a general cybersecurity scare video and does not promise that any configuration makes an agent unhackable. The practical lesson is to give each agent only the tools, data, and side effects required for its job, then verify the boundary with harmless tests.

## Research notes

### OpenClaw controls
- OpenClaw documents layered tool policy: a base tool profile, tool groups, sandbox tool gates, and allow/deny rules. A profile named full selects tools; it does not by itself grant unrestricted host execution.
- OpenClaw documents per-agent access patterns, including full access, read-only, and no access. A read-only setup combines workspaceAccess set to ro (or none), narrow workspace roots, and tool restrictions that block write, edit, apply_patch, exec, and process where those capabilities are not needed.
- OpenClaw execution approvals require the configured policy, allowlist, and any applicable user approval to agree. The docs also describe full/elevated exceptions, so the video must not imply that every execution path always prompts.
- Important caveat: execution approvals reduce accidental execution risk, but they are not a per-user authentication boundary or a read-only filesystem policy. They must be combined with tool policy, sandboxing, and narrow filesystem scope.
- For multi-agent setups, OpenClaw supports per-agent policies. Session visibility and agent-to-agent messaging are separate boundaries and should be restricted when agents have different trust levels.
- The OpenClaw security audit checks areas such as inbound access, DM/group policies, and allowlists. An audit is a useful check, not a guarantee that every risk has been removed.

### Human approval and workflow permissions
- OpenAI's Agents documentation distinguishes automatic guardrails from human review. Guardrails validate inputs, outputs, or tool behavior; human review pauses a sensitive tool call so a person can approve or reject it.
- GitHub Actions supports explicit GITHUB_TOKEN permissions. If permissions are specified, omitted scopes become none. A read-only content-validation workflow can start with contents: read; a separate job should receive only the additional scope it genuinely needs.
- OWASP's September 2026 GenAI Security Project update announced the 2026 Top 10 for LLM Applications and the Agent Control Standard. This supports the timely framing that agent security is increasingly about controlling what connected agents can access and do, not just what they can say.

### Cost and tool-use note
- No Exa search was run because the connected Exa tool did not expose a verifiable zero-cost balance or per-call cost in its available description.
- Firecrawl balance was checked: 460 of 1,000 plan credits remained. No Firecrawl search or scrape was run because the user prohibited spending credits.
- vidIQ balance was checked: 0 total credits (0 renewable, 0 add-on). All credit-consuming vidIQ research and generation was skipped.
- Public official documentation was used for research instead. No paid API, video generation, image generation, or credit-consuming research call was made.

### Sources
1. OpenClaw execution approvals: https://docs.openclaw.ai/tools/exec-approvals
2. OpenClaw tool policy: https://docs.openclaw.ai/gateway/config-tools/tool-policy
3. OpenClaw tool and agent permissions: https://docs.openclaw.ai/gateway/security/tool-permissions
4. OpenClaw security audit: https://docs.openclaw.ai/gateway/security/running-the-audit
5. OpenAI guardrails and human review: https://developers.openai.com/api/docs/guides/agents/guardrails-approvals
6. GitHub Actions workflow permissions: https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax
7. OWASP 2026 GenAI security update and Agent Control Standard: https://genai.owasp.org/2026/09/01/owasp-genai-security-project-unveils-2026-top-10-for-llm-applications-new-agent-control-standard-and-sponsors-as-community-tops-30000-members/

## Script draft

### Opening hook (0:00–0:30)
**[A-roll: user's approved digital twin, direct to camera. Blue background; gold warning outline around a permissions panel.]**

Here is one of the easiest ways to make an AI agent risky: give it access to everything.

Your files. Your terminal. Your GitHub repository. Your email. Your social accounts.

Now imagine one bad instruction or one misunderstood request. The agent does not just give you a wrong answer. It might make a real change.

Today, let's build a much better setup: three permission levels — **Read, Draft, and Approve**.

### The three-level model (0:30–1:10)
**[Graphic: three connected cards — READ / DRAFT / APPROVE. The final card has a human confirmation icon.]**

Think of an AI agent like a new team member. You would not give someone on their first day the keys to every account in your business.

Start with the smallest permission set that lets the job get done.

Level one: the agent can inspect information, but not change it.

Level two: it can prepare work in a limited draft area, but cannot send or publish it.

Level three: actions that affect the outside world wait for your approval.

This is a design pattern, not one magic switch. You combine tool permissions, workspace boundaries, and approval checks.

### Level one — Read only (1:10–2:00)
**[Screen demo: a test workspace with documents and a read-only agent profile. Show a blocked write attempt using a harmless test file.]**

First, create a research agent.

Its job is to read approved documentation, collect facts, compare sources, and return a report. It does not need to edit your files or run arbitrary commands.

OpenClaw documents a read-only pattern using a read-only workspace, narrow filesystem roots, and tool rules that block write, edit, patch, execution, and process tools when they are not required.

Keep the workspace narrow. Do not casually point a research agent at your entire home folder or private configuration directory.

And remember this detail: a tool profile controls which tools are selected. It is not the same thing as granting unrestricted access to your computer.

The test is simple: ask the research agent to read a sample file. Then ask it to change that file. The second action should be blocked.

### Level two — Draft only (2:00–2:55)
**[Graphic: a folder labeled DRAFTS. A one-way arrow leads into it; a lock blocks the Publish button.]**

Next is your writer or builder agent.

This one needs permission to create something, but only in a staging area. It can write a Markdown brief, prepare a proposed code change, or create a caption draft.

It cannot publish the video, send the email, merge the pull request, delete the original, or change account permissions.

Use a dedicated drafts folder or a separate working branch. Keep the original project intact.

The same idea applies to GitHub Actions. If a workflow only checks files, start with the narrow permission it needs:

~~~yaml
permissions:
  contents: read
~~~

GitHub documents that when you specify permissions, scopes you leave out become none. If a later job genuinely needs to comment on a pull request, give that job only the additional permission it needs. Do not make every step a writer just because one step needs to write.

### Level three — Approve the action (2:55–4:00)
**[A-roll: twin points at an approval card. On-screen fields: ACTION, TARGET, CONTENT, ACCOUNT, SCOPE.]**

Now we reach the important gate.

Posting publicly, sending a message, deleting a file, merging code, changing permissions, or running a command on the real host can have consequences outside the draft folder.

Before one of those actions runs, show the person exactly what is about to happen.

What action? On which account or repository? What content will be sent? Which file will change? Is the approval for this one action or for a continuing permission?

OpenAI's agent guidance describes human review that pauses a sensitive tool call until a person approves or rejects it.

OpenClaw's execution approvals use policy, an allowlist, and any applicable user approval together. But do not misunderstand that control: an execution approval is not a replacement for read-only filesystem boundaries or proper authentication. And some full or elevated modes can bypass ordinary prompts, so keep those modes tightly controlled.

My rule is simple: no vague “approve everything.” Approve one clearly described action, with a narrow scope.

### How to divide a small agent team (4:00–4:45)
**[Motion graphic: three agents in separate lanes.]**

If you run more than one agent, give each one a different job.

Your researcher gets read-only access.

Your writer can create drafts in its own workspace.

Your publisher stays locked until a human approves the exact final package and destination.

Do not assume that separate agent names automatically mean separate security boundaries. OpenClaw documents session visibility and agent-to-agent messaging as additional controls. Restrict those when agents should not share private history or talk to every other agent.

### Test the boundary (4:45–5:25)
**[Screen demo: harmless test repository; show allowed read, allowed draft write, blocked publish action.]**

Before connecting real accounts, test with a fake project.

One: can the research agent read the sample file but not edit it?

Two: can the writer create a draft without touching the original?

Three: does the sensitive action stop and request approval?

Four: can you see what happened afterward?

OpenClaw also provides a security audit command. Run the audit after configuration changes and review the findings. It is a check, not a promise that the system is perfect.

Never put real tokens or passwords on screen. Use test data, keep secrets out of prompts and logs, and verify the actual permissions in your installed version.

### Recap and CTA (5:25–5:55)
**[A-roll: twin on screen; the three gold cards return.]**

That is the whole model.

Read what you need. Draft where it is safe. Ask before anything that changes the outside world.

You still get useful automation, but you reduce the damage a mistaken or misled agent can cause.

Follow Automation Empire for practical AI workflows — and build your agents with boundaries before you give them more power.

## Title and metadata

### Primary title
Stop Giving AI Agents Full Access: Build a 3-Level Permission Gate

### Alternate titles
1. Read, Draft, Approve: The Safer Way to Build AI Agents
2. OpenClaw Security: Lock Down Your AI Agent's Tools
3. Your AI Agent Does Not Need Admin Access

### Description
AI agents can do more than answer questions. With connected tools, they may read files, edit projects, run commands, or trigger actions in outside accounts.

In this Automation Empire tutorial, we build a practical three-level permission model:

1. READ — research and inspect approved information without changing it.
2. DRAFT — prepare files and proposed changes in a limited staging area.
3. APPROVE — pause before sensitive actions such as sending, publishing, deleting, merging, or running commands on a real host.

We use OpenClaw's documented tool-policy, sandbox, and execution-approval concepts, plus GitHub Actions token permissions and human-review guidance. This is a layered design pattern, not a claim that one setting makes an agent perfectly secure.

Use a test workspace first. Keep secrets out of prompts and recordings. Check the documentation for your installed version.

Follow Automation Empire for practical AI automation that keeps a human in control.

### Hashtags
#AIAgents #OpenClaw #AIAutomation #AgentSecurity #GitHubActions #AutomationEmpire

### Search tags
AI agent permissions, OpenClaw security, secure AI agents, read only AI agent, human in the loop AI, AI agent sandbox, least privilege AI, GitHub Actions permissions, agent approval workflow, AI automation tutorial, multi agent security, Automation Empire

### Chapters
00:00 Why full access is risky
00:30 The Read–Draft–Approve model
01:10 Level 1: read only
02:00 Level 2: draft only
02:55 Level 3: approve sensitive actions
04:00 Separate permissions for agent teams
04:45 Test the boundaries
05:25 Recap

## Short 1 — Your AI agent does not need admin

### Working title
Your AI Agent Does Not Need Admin Access

### Hook
Stop giving every AI agent access to everything.

### Script (35–45 seconds)
Your AI agent does not need admin access just to help you work.

Give it three levels.

First: **Read**. It can research and inspect approved files, but it cannot change them.

Second: **Draft**. It can prepare a document or code change in a separate workspace, but it cannot send, publish, or merge.

Third: **Approve**. Anything that changes the outside world pauses until you review the exact action.

That is how you keep automation useful without making every agent an owner of your accounts.

Start small. Test the boundary. Expand permissions only when the job actually needs them.

Follow Automation Empire for practical AI workflows.

### Short description
A simple Read → Draft → Approve permission model for safer AI agents. Tool policy, workspace boundaries, and human approval work together; no single toggle is a complete security system.

### Short hashtags
#AIAgents #OpenClaw #AgentSecurity #AIAutomation #AutomationEmpire

### Visual direction
Vertical 9:16. Open with the user's approved twin beside a large “NO ADMIN BY DEFAULT” hook. Three fast cards appear in order: READ (blue eye), DRAFT (gold document), APPROVE (gold shield/check). End on a human approval card. Keep captions large and inside safe margins.

## Short 2 — One GitHub permission line

### Working title
One GitHub Line That Limits Your AI Workflow

### Hook
Your GitHub automation may have more permission than its job needs.

### Script (35–45 seconds)
Here is a small security improvement for a GitHub Actions workflow that only needs to inspect repository files.

Start with:

~~~yaml
permissions:
  contents: read
~~~

That gives the workflow read access to repository contents. When you explicitly set permissions, the scopes you leave out become none.

If a separate job needs to comment on a pull request, add only the pull-request permission that job needs.

Do not give every step write access just because one step needs it.

Keep publishing, merging, and other sensitive actions behind a human review.

Small permissions. Smaller blast radius.

Follow Automation Empire for practical AI workflows.

### Short description
A quick GitHub Actions least-privilege tip: declare the GITHUB_TOKEN scopes your workflow actually needs and keep sensitive changes approval-gated.

### Short hashtags
#GitHubActions #DevSecOps #AIAgents #LeastPrivilege #AutomationEmpire

### Visual direction
Vertical 9:16. Show a workflow card with a broad permission list shrinking to one blue line: contents: read. Animate unused scopes fading to zero. The user's approved twin points to the line; finish with a gold approval lock. Use a clearly labeled demo repository, not private account details.

## Thumbnail concepts

### Variant A — “DON'T GIVE IT ADMIN”
- Canvas: 16:9, midnight navy background, electric-blue edge light, restrained gold accents.
- Presenter: user's own approved digital-twin look on the right, surprised but credible expression, cutout with a clean gold rim light.
- Main text: “DON'T GIVE IT ADMIN” in large, high-contrast white/gold lettering on the left.
- Graphic: three stacked permission cards labelled READ, DRAFT, APPROVE; the final card has a visible human-check icon.
- Signature element: small Automation Empire gold bar at lower left.
- Composition: face and hook readable at mobile size; no fake warning counts, breach imagery, or claims of guaranteed security.

### Variant B — “READ → DRAFT → APPROVE”
- Canvas: 16:9, deep blue-to-black gradient with a clean gold workflow line.
- Presenter: user's own approved digital-twin look on the left, pointing toward the three-step flow.
- Main text: “READ → DRAFT → APPROVE” with APPROVE in gold.
- Graphic: three large cards with simple eye, document, and approval icons; a small lock separates the draft stage from the final action.
- Signature element: consistent blue/gold Automation Empire frame and typography.
- Composition: simple enough to read on a phone; different layout from Variant A while keeping the same brand system.

### Thumbnail production prompt
Create an original 16:9 Automation Empire YouTube thumbnail using the user's supplied/approved digital-twin face reference only. Preserve the recognizable likeness; do not substitute a stock presenter or infer new personal traits. Use midnight navy, electric blue, and gold; large readable typography; crisp lighting; one clear visual metaphor; no misleading security claims. Produce two separate compositions matching Variants A and B. Do not generate until a no-cost route is confirmed.

## Production plan
- Format: one 5:45–6:00 flagship tutorial plus two independent 9:16 Shorts.
- Presenter: user's approved digital twin and cloned voice, only if the user confirms a genuinely no-cost production route. No unrelated voice or stock presenter.
- Visuals: original motion graphics, a fake/test repository, a clearly labeled sample workspace, and permission cards. Do not show live tokens, private files, account identifiers, or real credentials.
- Long-form pacing: energetic, direct, explanatory. Keep the difference between tool availability, workspace access, host execution, and approval explicit.
- Reuse: Shorts are separately scripted and have different teaching points; do not simply crop the same 45 seconds twice.
- Thumbnail: choose A or B after review. Both are concepts only; no image has been generated.
- Budget: $0. No paid generation, API calls, subscriptions, or credit-consuming research.

## Production checklist
- [ ] Verify OpenClaw documentation and setting names against the installed version before recording.
- [ ] Build the demo in a disposable test workspace and repository.
- [ ] Demonstrate a blocked write in the read-only lane.
- [ ] Demonstrate a draft-only write in the staging lane.
- [ ] Demonstrate a human approval pause before a harmless simulated side effect.
- [ ] Explain that exec approvals are not a substitute for filesystem isolation or authentication.
- [ ] Explain that full/elevated modes and session visibility require separate controls.
- [ ] Use a fake repository and fake content; never expose real tokens, passwords, private messages, or private configuration.
- [ ] Use the user's approved digital twin and cloned voice only after confirming no-cost availability.
- [ ] Generate no images or video until the user approves the route and cost.
- [ ] Human-review script, captions, claims, thumbnail, and final export.
- [ ] Do not upload, publish, schedule, merge, or distribute without explicit approval.

## Package operations and limitations
- Duplicate check: current GitHub integration branch contains the four prior briefs dated 2026-10-01, 2026-10-31, 2026-11-01, and 2026-11-02. Main and the alternate integration branch contain only the earlier 2026-10-01 brief. No 2026-11-03 package with this topic was present.
- Tracker: existing live spreadsheet is “Automation Empire — Video Production Tracker”; the stable Package ID was checked and was not present before insertion. The live Sheet1 schema has ten columns ending in Package ID. The backup tracker was left untouched.
- Drive: existing “Automation Empire — Draft Assets” folder was inventoried; it contains the prior package drafts and a backup tracker. This new draft belongs in that folder.
- HeyGen: all four existing sessions were checked. No session was actively generating. One launch draft is completed at 46.7 seconds; another earlier tutorial failed because the free-tier quota was exhausted; the second-brain session is waiting for input with an existing completed resource; the earlier content-workflow session is completed. No new session or render was started.
- Research: official OpenClaw, OpenAI, GitHub, and OWASP documentation was used. Exa was not called because zero-cost usage could not be verified. Firecrawl search/scrape was not called because it would consume credits; the balance check showed 460 of 1,000 credits remaining. vidIQ was skipped because its balance was zero.
- Publishing: no upload, post, schedule, merge, or public-setting change was made.
- Approval needed: review the script and choose thumbnail A or B; confirm a no-cost twin/voice production route before any generation.
