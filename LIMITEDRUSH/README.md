# Codex Touch Bar for MTMR 2026

An Apple-style Touch Bar layout built specifically for the Codex desktop app on
Apple silicon Macs. MTMR is shown only while Codex is active; other apps keep
their native Apple Touch Bar.

![Codex Touch Bar](codex-touchbar.png)

## Features

- Native-style monochrome shortcut buttons.
- Animated Clawd pet with all 20 official TokenTracker states and all five
  physical reactions (jump, wiggle, flip, multi-blink, and wave),
  plus automatic idle reactions, double-tap, and long-press feedback.
- Live daily token count and estimated cost from TokenTracker, with a local
  Codex session-log fallback.
- Tap the wider center speech bubble to cycle through the full TokenTracker-style
  pool: today, 7-day and 30-day totals, active days, conversations, quota status,
  usage-sensitive reactions, and personality messages. Clawd changes pose,
  props, and outfits too, including the wizard hat and staff, juggling balls,
  typing particles, ultrathink effects, overheating, sleep/wake, and mini modes.
- Remaining-quota progress bar and next reset time, read live from the locally
  authenticated Codex app server every 10 seconds.
- Keyboard-combination actions for Codex shortcuts.

## Files

- `items.json` — the ready-to-use preset.
- `MTMR-CodexTouchBar.patch` — the complete native Swift changes required by
  this preset, based on `josmanvis/mtmr-designer` at tag
  `v2026.1-build.18` (`97670cb`).
- `codex-touchbar.png` — a Touch Bar capture of the installed layout.

## Install

1. Clone `https://github.com/josmanvis/mtmr-designer` and check out
   `v2026.1-build.18`.
2. From the repository root, apply the patch:

   ```bash
   git apply /path/to/MTMR-CodexTouchBar.patch
   ```

3. Build the `MTMR` scheme in `mtmr-src/MTMR.xcodeproj` for Apple silicon.
4. Copy `items.json` to:

   ```text
   ~/Library/Application Support/MTMR/items.json
   ```

5. Grant the built app Accessibility permission in System Settings.

TokenTracker is optional. When its local usage API is available, MTMR uses its
today and rolling-summary data so the Touch Bar matches TokenTracker's own
companion messages; otherwise it reads local Codex session logs for today's
tokens and cost. Quota data never falls back to stale logs: if the live Codex
app server request fails, the quota widget shows an unavailable state. No
credentials, signing certificates, or private account data are included in
this preset.
