# Working prompts for ecommerce AI video ads (tested October 2026)

These are the prompts behind every example in this repo, copied from the runs that produced them. Replace the `<…>` parts with your product. Every call goes to `https://api.varg.ai/v2` with `Authorization: Bearer $VARG_API_KEY`, or through the varg MCP server (`call_tool`). The full method for each format is in its skill in [vargHQ/skills](https://github.com/vargHQ/skills).

## Contents

1. [Viral product hook (Seedance 2.5)](#1-viral-product-hook)
2. [ASMR unboxing (Seedance 2.5, native sound)](#2-asmr-unboxing)
3. [Product lock block (keep the product identical)](#3-product-lock-block)
4. [Singing mascot: character, jingle, singing clip](#4-singing-mascot)
5. [Try-on: still and fit-check motion](#5-try-on)
6. [Break down a competitor ad (video_analyze)](#6-break-down-a-competitor-ad)
7. [Compliance audit (video_analyze)](#7-compliance-audit)
8. [Product drift check (video_analyze)](#8-product-drift-check)
9. [Transcreation brief for a new market](#9-transcreation-brief)
10. [Hook swap with FFmpeg](#10-hook-swap-with-ffmpeg)

## 1. Viral product hook

`seedance_2_5`, product photo as `@image1`, 9:16, 720p, 6 s: 231 credits ($2.31). Skill: [varg-product-hook](https://github.com/vargHQ/skills/tree/main/varg-product-hook).

```
Vertical UGC product clip shot handheld on an iPhone in a cozy living room, natural window light, slight hand
shake. Extreme close-up: a person's hands hold a fluffy orange cat's front paw on a grey blanket. They bring in
the pet nail clipper from @image1 (exact same product, same white and pastel-blue colors, same LED light at the
blade). The LED switches on and lights up the claw so the pink quick is visible through it; the clipper snips the
very tip of the claw cleanly, the clipping drops into the transparent guard. The cat stays calm. Real footage
look, no music, no text, no subtitles.
```

Archetypes that sell: backyard security camera ("caught this"), torture test (knife across the glove), satisfying close-up, gift reaction, before/after, problem → "Vs…" → solution. Write "points at" or "moves to", never "circles": the model draws what the verb says.

## 2. ASMR unboxing

`seedance_2_5`, box as `@image1` and product as `@image2`, 10 s, `"audio": true`: 385 credits ($3.85). Skill: [varg-unboxing-video](https://github.com/vargHQ/skills/tree/main/varg-unboxing-video).

```
Vertical ASMR unboxing, hands only, no face, top-down camera on a light oak table, soft window light.
@image1 is the exact retail box, @image2 is the exact product inside; never change their shape, colors or printing.
0-3s VISUAL: the closed box from @image1 already in frame, two hands rest on it. ACTION: fingertips tap the lid
three times, slow, careful. SOUND: hollow cardboard taps.
3-6s VISUAL: the lid lifts off slowly. ACTION: one hand holds the base, the other lifts the lid and sets it aside,
brief hold. SOUND: soft paper slide, lid suction pop.
6-10s VISUAL: the product from @image2 rests in a white tray; a hand lifts it out and turns it slowly toward the
camera, then presses the button and it switches on. SOUND: tissue crinkle, plastic click.
No music. Pure organic ASMR soundscape. No speech, no text, no subtitles.
```

No box photo? `nano_banana_2_1` with the product photo (5 credits): "a closed premium retail box for this product, lift-off lid, the product photo printed on the front, on a light oak table".

## 3. Product lock block

Put this at the top of any product shot. Add a side-profile reference (`nano_banana_2_1`: "the exact same product from the side on white", 5 credits). Skill: [varg-product-lock](https://github.com/vargHQ/skills/tree/main/varg-product-lock).

```
Product lock. @image1 is the exact product, front three-quarter view; @image2 is the same product from the side,
showing its true <shape> (<real size>). The product keeps this exact shape and size: it does not become <common
drift>, does not change color, <surface details> or <key feature>. Never re-describe it beyond this.
<scene, one simple action, slow and steady, camera holds still with a slight handheld drift>
Real footage look, no music, no text, no subtitles.
```

Banned words: spin, 360, whip, fast zoom, morph, transform. Keep one action per 4–6 s shot.

## 4. Singing mascot

Skill: [varg-mascot-jingle-ad](https://github.com/vargHQ/skills/tree/main/varg-mascot-jingle-ad).

Character, `nano_banana_2_1` with the product photo (5 credits):

```
Turn the <product> from the reference image into a cute claymation mascot character: the same <colors> body and
<key detail>, with two big friendly cartoon eyes and a wide expressive mouth with a visible jaw and small teeth,
two tiny clay arms. It stands on <setting>, facing the camera, mouth slightly open, neutral pose. Stop-motion clay
texture, miniature studio lighting, vertical 9:16, no text.
```

Jingle, `lyria_3_5` (10 credits; it returns about 60 s, so cut the sung lines afterwards):

```
A catchy, upbeat 15-second advertising jingle, playful ukulele and hand claps with a light pop beat, 110 BPM, one
cheerful lead singer, simple memorable melody. Lyrics: [0:00-0:07] "<line 1>" [0:07-0:15] "<brand line>".
Ends on a short bright strum.
```

Singing, `seedance_2_5`: mascot as `@image1`, the jingle mp3 as `@audio1`, 15 s, audio on (578 credits). Lay the master song back on top afterwards:

```
@image1 is the exact claymation mascot and the first frame. The mascot sings the song from @audio1 straight to the
camera, its clay mouth opening and closing exactly in sync with every sung word, eyes blinking, bouncing to the
beat, waving its tiny arms. Camera locked, stop-motion clay texture, about 12 fps feel. Keep the mascot's shape and
colors exactly the same. No text, no other characters.
```

## 5. Try-on

Skill: [varg-tryon-video](https://github.com/vargHQ/skills/tree/main/varg-tryon-video). The still uses `bria_fibo_edit_1_5_virtual_try_on` with a model photo and a garment photo (4 credits):

```
Dress the woman in the <garment> from the second image, worn <how>. Keep her face, hair, pose, <other clothes>,
<shoes> and the room unchanged.
```

Fit check, `kling_v4`, 5 s (79 credits):

```
Fashion fit-check video, phone on a tripod, camera locked, full body and the hem always in frame.
She turns slowly 90 degrees to show the side, pauses, turns back, then lightly tugs both front edges and lets go so
it falls open naturally. Hands stay away from the front panel. <fabric> moves with weight; <pattern, buttons, logo>
stay exactly the same. Natural window light, realistic iPhone footage, no text.
```

## 6. Break down a competitor ad

`POST /v2/tools/video_analyze/call` with `{"model":"video-analyze","video_url":"<ad>","prompt":"…"}` (5 credits). Skill: [varg-ad-library-remix](https://github.com/vargHQ/skills/tree/main/varg-ad-library-remix).

```
Break this competitor product ad down for a remix: every shot with start-end seconds, camera and what happens; all
on-screen text with timings; audio; the hook in the first 3 seconds; the angle (which pain or desire it sells), the
format, the offer, the proof moment and the CTA; and the awareness level of the viewer it targets.
```

## 7. Compliance audit

Same tool, 5 credits. Skill: [ai-ad-compliance-check](https://github.com/vargHQ/skills/tree/main/ai-ad-compliance-check). Match the output against [rules.json](https://github.com/vargHQ/skills/blob/main/ai-ad-compliance-check/references/rules.json).

```
Audit this ad for compliance review: list every spoken claim and every on-screen claim with timestamps (prices,
profit, results, guarantees, earnings, health, time-to-result, shipping promises); every person or face and whether
it looks like a real person, a customer or an AI performer; any security-camera or caught-on-camera framing
presented as real; before/after shots; landmarks, brands or characters visible; and any disclosure of AI use or
paid partnership.
```

## 8. Product drift check

Same tool, 5 credits per clip. Rerun only the shots that fail.

```
Compare the product in this clip with this description: <lock sheet>. For the first, middle and last second: does
shape, size, color, label and every fixed detail match? Answer PASS or FAIL per attribute with the second where it
breaks.
```

## 9. Transcreation brief

Give this to the model with the source transcript and word timings. Skill: [varg-ad-localize](https://github.com/vargHQ/skills/tree/main/varg-ad-localize).

```
MARKET: es-MX · LANGUAGE: Spanish (Mexico, not Spain) · CURRENCY: MXN, price from the MX listing
OFFER: 1 pair, $349 MXN, free shipping 3-5 days · CTA: "Toca la bolsita naranja" (TikTok Shop tag)
APPROVED CLAIMS: cut-resistant level 5 (certificate) · FORBIDDEN: "irrompible", medical claims
NEVER SAY: literal English idioms, "you guys", prices in USD
Rules: rewrite the hook (first 3 s) for the market; keep every line within ±10% of its source syllables; swap units
and currency; keep brand and product names; drop claims not on the card; keep the anchor phrase that starts each beat.
```

## 10. Hook swap with FFmpeg

From [varg-ad-variants](https://github.com/vargHQ/skills/tree/main/varg-ad-variants). It runs locally for free; each new spoken line on `eleven_v4` costs 1 credit.

```bash
node scripts/hook-swap.mjs --body master_clean.mp4 --cut 7.34 --out variants/ \
  clips/mandoline.mp4+lines/pov-mandoline.mp3 \
  clips/knife.mp4+lines/knife-test.mp3
```

Name the variants `{angle}_{offer}_{product}_{format}_{hook}_v{n}` and change one variable per variant.
