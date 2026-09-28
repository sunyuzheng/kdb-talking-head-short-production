# YouTube Shorts publication

Read this only when the user asks to upload, schedule, or publish to YouTube. Platform interfaces and limits change, so inspect the current YouTube Studio state rather than relying on fixed button positions.

## Authorization and publication manifest

Before upload, use read-only inspection of the authenticated Studio session to confirm the active channel and channel ID, current upload or Shorts eligibility signals, and whether the intended Related Video is available to that channel. This inspection must not select a file, create an upload, or change channel state.

For this creator, the 2026-09-28 standing authorization covers routine short-video uploads and scheduling to the established YouTube channel, Instagram account and Google Drive archive. Do not ask for per-video confirmation when the task remains within that scope. Prepare and verify a local publication manifest before any upload. For a user without standing authorization, present that manifest and obtain approval. It includes:

- channel name and channel ID;
- exact local video path and the final file identity or checksum;
- title and description exactly as they will appear;
- visibility or schedule and its timezone;
- audience setting, including made-for-kids status;
- paid-promotion and altered/synthetic-content disclosures when applicable;
- ad-suitability answers when the channel presents them;
- subtitle language and exact subtitle file;
- related video exact title and video ID, or “none”;
- thumbnail or first-frame strategy.

Keep the manifest accurate after platform validation or editorial changes. A specific approval is scoped to its payload; standing authorization covers ordinary editorial and scheduling choices within its established workflow. Ask only when the action materially exceeds the applicable authorization.

If the intended file is not currently eligible for the requested Shorts treatment, do not shorten or restructure it without approval. Present the platform evidence and the available alternatives. If the Related Video control or exact target is unavailable, put `none` in the payload or ask the user to choose another exact video; never substitute a similar title.

## Upload and verify

Use the user's authenticated normal browser session through the supported browser-control skill. Do not extract cookies or secrets. If login, CAPTCHA, two-factor authentication, or an account chooser requires the user, pause at that point.

After confirming that user authorization covers the upload:

1. Open YouTube Studio on the confirmed channel and select the exact final MP4.
2. Wait for the upload and media analysis far enough to validate duration, aspect, and processing state.
3. Enter the approved title, description, audience, disclosures, and thumbnail or first-frame choice.
4. Add the approved related video by exact title or video ID. Do not select an approximate search match.
5. Upload the corrected SRT as the intended language, even when captions are burned into the picture. Confirm the track is shown as supplied by the channel owner.
6. Complete copyright and ad-suitability checks. Do not guess around a warning; report a material issue before continuing.
7. Recheck every approved field, then set the approved visibility or schedule and publish.
8. Open the returned video or Shorts URL and verify visibility, processing, title, description, related video, and subtitle track.

For a private upload, verification still matters: confirm that the video is private and that the returned URL belongs to the intended channel. For a public upload, success means the public watch or Shorts page works—not merely that Studio accepted the file.

Burned captions guarantee feed readability; the uploaded subtitle track adds accessibility and searchable text but may create duplicate words for a viewer who turns captions on. Keep the burned treatment concise and treat the platform track as an accessibility layer, not a second designed caption layer.

The platform may choose or crop its own cover differently across surfaces. Record the intended frame-zero and uploaded-thumbnail strategy, then verify the actual channel and watch surfaces instead of promising identical display everywhere.

## Handoff record

Record:

- upload timestamp and timezone;
- channel ID and video ID;
- final URL;
- title, visibility or schedule, audience, related video ID, and subtitle language;
- check results and any unresolved processing state.

YouTube publication alone does not authorize another platform. This creator has separately authorized routine YouTube, Instagram and Google Drive delivery; Xiaohongshu remains opt-in for each batch. Record the applicable authorization and exact payload for each destination without asking again when it is already covered.
