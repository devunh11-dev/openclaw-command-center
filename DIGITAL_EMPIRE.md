# Digital Empire Content Pipeline

## Purpose
A proof-first, low-cost content system coordinated by OpenClaw.

## Flow
1. Research: Exa / Firecrawl / vidIQ when credits are available.
2. Human topic approval.
3. Script + metadata generation.
4. Asset production: voice, video, thumbnail.
5. Human quality/compliance review.
6. Publish to the connected YouTube channel.
7. Distribute to social/blog destinations.
8. Measure with YouTube analytics / Windsor.ai / vidIQ.
9. Feed verified performance findings back into the next research cycle.

## Guardrails
- Never publish without an explicit approval checkpoint.
- Never invent sources, metrics, or tool results.
- Keep API keys and OAuth tokens out of Git.
- Prefer free/low-cost providers; no silent paid fallback.
- Preserve original commentary and channel-specific value.
- Store source URLs with each research brief.
- Treat generated assets as drafts until reviewed.

## Current connected YouTube channel
- vidIQ channel ID: UC2IYU_QpelUmDsdcv3tY58A

## Current execution notes
- vidIQ channel authorization is available.
- vidIQ research calls currently report insufficient credits, so this workflow must degrade gracefully to Exa/Firecrawl research rather than pretending vidIQ research succeeded.
- Notion content search currently returned an integration server error; no Notion write is claimed here.
