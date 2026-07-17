---
name: ad-restyler
description: >-
  Restyle any ad or video into a completely different visual style — Aardman claymation, LEGO-style
  bricks, X-ray, 16-bit pixel art, Ghibli anime, felt puppets, voxel art, knitted yarn, premium 3D
  Pixar-style animation, or a custom style built live — while preserving the original shots, camera
  moves, motion, and timing exactly. Use whenever the user wants to "restyle" a video or ad, "turn my
  ad into claymation / anime / pixel art / LEGO", "make this video look like X style", "style transfer
  my video", or uploads a video with intent to change its visual style. Fixed gate flow: source check
  → style selection → preservation preferences → prompt approval → delivery gate ("Generate via
  MaxFusion AI MCP — yes or no?"). Yes: generate the restyled clips with MaxFusion MCP tools (Google
  Omni Flash, 720p, 10s clips) and return them in chat. No: Google AI Studio path — run via API key if
  possible, otherwise deliver the complete copy-paste package.
---

# Ad Restyler

Restyle any ad or video into a different visual world with one prompt, while keeping every shot, camera move, performance, and beat of comic timing exactly as filmed.

One skill, two execution paths, chosen at the delivery gate:
- **MaxFusion AI MCP path** — the agent generates everything itself and returns finished clips in chat.
- **Google AI Studio path** — the agent runs the generation via API if it can; otherwise the user gets the complete run-ready package in chat.

## Requirements

- An AI assistant capable of following this skill (built for Claude; works with any capable agent)
- **For the MaxFusion path:** MaxFusion AI MCP connected
- **For the AI Studio path:** a Google AI Studio API key with access to the Google Omni Flash video-to-video model
- A source video. Google Omni Flash handles clips of **10 seconds or less**. Longer ads are split into ≤10s segments, each restyled with the identical prompt, then rejoined in edit.

## The Core Formula (never deviate)

Every restyle prompt follows one locked skeleton:

> Restyle this video as **[STYLE NAME]**: **[material, texture, surface, and rendering details]**. Keep everything else exactly the same — same shots, same camera moves, same motion.

Rules:
1. The invariance clause ("Keep everything else exactly the same — same shots, same camera moves, same motion.") is **mandatory and verbatim** in every prompt. It is what makes this a restyle instead of a regeneration.
2. Style details describe **materials and rendering only** — never new actions, new characters, new objects, new settings, or new text.
3. When the source has people whose performance matters, append the performance-preservation line (see Gate 3).

## Workflow — Fixed Gate Flow

### Gate 1 — Source Check
Ask the user:
- Do you have the source video ready to upload, or a link/description of it?
- Video length? (≤10s → one prompt, one generation. Longer → explain split-and-rejoin; every segment gets the identical style prompt.)
- Does the video contain people whose facial performance / comic timing must survive the restyle? (Yes → performance line is appended in the final prompt.)

### Gate 2 — Style Selection
Present the style menu (names only, never the full prompts):

1. Aardman Claymation
2. Plastic Construction Bricks (LEGO-style)
3. X-Ray Radiograph
4. 16-Bit Pixel Art
5. Studio Ghibli Anime
6. Felt Puppet Stop-Motion
7. 3D Voxel Art
8. Knitted Wool Yarn
9. Premium 3D Animation (Pixar-style)
10. Custom style — built live with the Custom Style Builder

### Gate 3 — Preservation Preferences
Confirm defaults (all ON unless the user changes them):
- Preserve dialogue/audio timing ✔
- Preserve character count and blocking ✔
- No added text ✔
- No added characters or objects ✔
- No setting changes ✔

If people + performance matter (from Gate 1), append to the chosen style prompt:
> preserving the original shot framing, camera moves, character blocking, performances and comic timing exactly as they are; expressions match the original performances.

### Gate 4 — Prompt Approval
Show the user the complete final prompt (style preset + any appended lines, one per segment if multi-segment). **Wait for explicit approval before proceeding.** Apply targeted edits if requested, re-show, re-confirm.

### Gate 5 — Delivery Gate
Ask exactly:

> **Do you want me to generate this via MaxFusion AI MCP — yes or no?**

**If YES → MaxFusion AI MCP Generation Path:**
1. Run a live capability check on the MaxFusion MCP — verify current tools and the video model catalog with real calls. Never assume tool capabilities from memory.
2. Upload the user's source video as a reference asset via the MCP upload tool.
3. Generate with Google Omni Flash (`gemini-omni-flash`) at **720p** (locked — the model runs at 720p only), video-to-video, one generation per ≤10s segment, identical prompt across all segments.
4. Poll each job to completion.
5. Deliver every finished clip **in chat as inline generation widgets**. Never paste raw storage/S3 links. No canvas.
6. Multi-segment ads: deliver clips in order with segment labels so the user can rejoin them in edit.

**If NO → Google AI Studio Path:**
1. If the agent has execution capability and the user's Google AI Studio API key is available: run the generation directly against Google Omni Flash video-to-video and return the results in chat.
2. If the agent cannot execute: deliver the complete run-ready package in chat —
   - The final prompt(s) in a single copy-paste block per segment
   - Run instructions: open Google AI Studio (or any product exposing Google Omni Flash video-to-video) → upload the source clip (≤10s) → paste the prompt → generate at the highest available resolution
   - Multi-segment note: run every segment with the **identical** prompt, then rejoin in the editor. Consistency comes from prompt identity — never vary the style wording between segments.

Either way, the user ends the conversation with everything they need in chat.

## Style Preset Library

### 1. Aardman Claymation
Restyle this entire video as hand-sculpted Aardman-style stop-motion claymation, preserving the original shot framing, camera moves, character blocking, performances and comic timing exactly as they are. Both people become plasticine puppets with hand-sculpted clay skin showing visible fingerprint impressions, sculpting-tool marks, slight facial asymmetry and subtle pinch lines around the eyes and mouth; their expressions stay deadpan and bored, matching the original performances. The clay is matte and opaque with soft micro-bumps, subtle tool-seam lines at the joints, and a faint waxy sheen catching the key light. Hair and eyebrows are sculpted as solid clay forms, not strands, with visible tool-comb texture. Clothing is treated as thin rolled clay or fabric-textured polymer, holding soft creases and finger-pressed folds rather than realistic drape. Eyes are small glossy inset beads with a painted highlight, giving the classic stop-motion stare. Micro-jitter and slight frame-to-frame positional drift are present throughout, replicating the imperfect hand-animated movement of true stop-motion — no motion blur, no smoothing. Set dressing and props are similarly rebuilt as miniature handcrafted claymation pieces with visible seams and thumbprints, lit with the warm, slightly grainy practical lighting typical of an Aardman set. Audio, dialogue, and timing remain untouched — only the visual medium changes.

*Adapt "Both people" to the actual subject count of the source video ("The person becomes…", "All three people become…"). Adapt "deadpan and bored" to the actual emotional register of the source performances.*

### 2. Plastic Construction Bricks (LEGO-style)
Restyle this video as a world assembled from interlocking plastic construction bricks: studded blocky surfaces, glossy moulded plastic, stepped brick edges, blocky toy figures. Keep everything else exactly the same — same shots, same camera moves, same motion.

### 3. X-Ray Radiograph
Restyle this video as an X-ray radiograph: translucent grayscale interiors, bright bone-white structures against deep black, ghostly semi-transparent surfaces, medical imaging glow. Keep everything else exactly the same — same shots, same camera moves, same motion.

### 4. 16-Bit Pixel Art
Restyle this video as 16-bit pixel art: chunky visible pixels, limited retro palette, dithered gradients, sprite-style characters, SNES-era game aesthetic. Keep everything else exactly the same — same shots, same camera moves, same motion.

### 5. Studio Ghibli Anime
Restyle this video as hand-drawn Studio Ghibli anime. Keep everything else exactly the same — same location, same shots, same camera moves, same motion. Don't change the setting. Don't add characters or objects. Don't add text.

### 6. Felt Puppet Stop-Motion
Restyle this video as felt puppet stop-motion: everything sculpted from wool felt and fuzzy fabric, visible stitching and seams, soft fibre texture, handmade miniature set. Keep everything else exactly the same — same shots, same camera moves, same motion.

### 7. 3D Voxel Art
Restyle this video as 3D voxel art: everything built from chunky cubic blocks, blocky stepped edges, flat shaded faces, Minecraft-like world. Keep everything else exactly the same — same shots, same camera moves, same motion.

### 8. Knitted Wool Yarn
Restyle this video so everything is knitted and crocheted from chunky wool yarn: visible stitches and purl rows, fuzzy fibre halo, soft squashy forms, loose threads at the edges. Keep everything else exactly the same — same shots, same camera moves, same motion.

### 9. Premium 3D Animation (Pixar-style)
Restyle this video as premium 3D animated film in the style of a top-tier animation studio: smooth subsurface-scattered skin with soft warm undertones, large expressive eyes with detailed iris reflections, gently exaggerated facial proportions, physically-based rendering with soft global illumination, cinematic depth of field, rich saturated color grading, and polished materials — soft fabric weave on clothing, subtle specular highlights on surfaces. Keep everything else exactly the same — same shots, same camera moves, same motion.

### 10. Custom Style Builder
When the requested style is not in the library, build it live:
1. Ask: what material/world? (e.g. "origami paper", "stained glass", "oil painting")
2. Write 3-6 material and rendering descriptors: surface, texture, edge behavior, light behavior, plus one era/reference anchor if useful.
3. Assemble via the Core Formula. Invariance clause verbatim. No new actions, characters, objects, settings, or text.
4. Show the user before finalizing (this feeds into Gate 4 approval as normal).

## Hard Rules
- Never remove or reword the invariance clause.
- Never inject content changes into a style prompt.
- One style per prompt — never blend styles unless the user explicitly asks for a hybrid custom style.
- Multi-clip ads: identical prompt across all clips, always.
- MCP path: live capability check before generating, 720p locked, widgets only, no raw links, no canvas.
- Never generate before Gate 4 approval and the Gate 5 answer.
