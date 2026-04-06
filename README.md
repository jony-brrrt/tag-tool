# Game Audio Tagger

Upload an audio file, get every tagging sheet column filled automatically using your controlled vocabulary — ready to paste directly into your Google Sheet.

## What it does

1. Drop a WAV, OGG, MP3, or FLAC file
2. The browser analyses it — duration, estimated BPM, key, channels
3. Claude reads the analysis and fills every column using only your defined vocabulary
4. Hit **Copy row** and paste into your tagging sheet — all columns land in the right place

## How to use

1. Clone this repo
2. Open `index.html` in any browser — no server needed, no install, no build step
3. Enter your [Anthropic API key](https://console.anthropic.com) — stays in memory only, never stored
4. Set your **world character** (e.g. `dark gothic fantasy`) — used in every caption
5. Pick the tab: **Music**, **SFX**, or **UI Sound**
6. Drop a file

## Column output per tab

**Music:** filename, duration, est_key, est_bpm, world_character, asset_type, game_context, instrumentation, mood_primary, mood_secondary, intensity, key_confirmed, bpm_confirmed, structure, loop_ready, technical_flags, CAPTION

**SFX:** filename, duration, world_character, asset_type, game_context, source_material, sound_character, attack_shape, space, mood, intensity, channel, variant_id, technical_flags, CAPTION

**UI Sound:** filename, duration, world_character, asset_type, interaction_type, tonal_character, sound_source, mood, intensity, tonal_match, channel, technical_flags, CAPTION

## Notes

- BPM and key detection are approximate (browser Web Audio API) — Claude will flag uncertain values. Always confirm by ear.
- The API key is never stored anywhere — it lives only in the browser session.
- Each call uses `claude-sonnet-4-20250514` and costs roughly €0.001–0.002 per file.
- Works entirely offline except for the Claude API call.

## Customising the vocabulary

All vocabulary is defined inside the Claude prompts in `index.html`. Search for the `prompts` object and edit the allowed values to match your own controlled vocabulary if it differs.
