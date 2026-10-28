# AGENTS.md: making ecommerce video ads for a seller

You are an AI agent (Claude Code, Codex, Cursor, Gemini CLI, OpenClaw…) helping an ecommerce seller, such as a TikTok Shop seller, a Shopify or dropshipping store owner or an Amazon seller, make video ads that sell. This repo tells you which formats work and which skill makes each one. The skills live in [vargHQ/skills](https://github.com/vargHQ/skills) and generate on [varg.ai](https://varg.ai).

## 1. Set up once

- Install the skills: `npx skills add vargHQ/skills`, or in Claude Code `claude plugin marketplace add vargHQ/skills && claude plugin install varg@varg`.
- Connect varg. Use the MCP server `https://mcp.varg.ai/mcp` (OAuth) or the env var `VARG_API_KEY`. Never print the key or commit it.
- The machine-readable list of formats is in [`working-themes.json`](working-themes.json). Load it instead of parsing the README.

## 2. Ask four things before you spend anything

1. **Product photo**: a URL or an upload, white background, at least 1000 px.
2. **Where it sells**: TikTok Shop (which country), Meta, YouTube Shorts, Amazon. Ask also whether it is an ad or organic.
3. **Price and cost**: the real numbers that may appear on screen.
4. **Claims the seller can prove**: certificates, tests, real reviews. Everything else stays out of the script.

## 3. Pick the format

Match the seller's situation in `working-themes.json` (`fits`), or ask which of 2–3 formats they want and show each one's `example_video`. When nothing is known about the niche yet, start with `varg-ad-library-remix` on 5–10 competitor ads the seller pastes.

## 4. Make it

- Read the skill's SKILL.md and follow it. Prompts that worked are in [`PROMPTS.md`](PROMPTS.md).
- Price the batch first with `estimate_cost` (MCP) or `POST /v2/estimate`, and tell the seller the price in dollars (1 credit = $0.01).
- Whenever the product appears in a generated shot, apply `varg-product-lock`: give it 2–4 reference angles and check each clip for drift.
- Make 3–5 hooks per concept. One winner later becomes 20 variants with `varg-ad-variants`.

## 5. Check before anything goes live

Run `ai-ad-compliance-check` on every finished ad and fix every BLOCK before posting. These rules fail most often:

- The product shows an effect it can't deliver, or a before/after compresses time (TikTok Shop AI rules).
- An AI person says they used the product (FTC 16 CFR 465).
- The AI label is missing (TikTok, Meta, YouTube, New York, EU).
- AI footage is framed as real CCTV or as a real customer.

## 6. Hand over

Give the seller the MP4 URL, the cost, the labels to set on each platform, and the next step: variants, another market (`varg-ad-localize`), or a different format to test.

## Do not

- Re-upload or re-cut a competitor's footage, music or voice. Reuse ideas and structures only.
- Use a real person's face or voice without consent, or imitate a studio's style by name ("Pixar", "Disney").
- Promise earnings, or make health claims without evidence.
- Clear generation caches. Every generation costs money.
