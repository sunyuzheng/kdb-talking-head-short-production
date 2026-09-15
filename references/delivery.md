# Delivery and quality control

Use this reference for ingest, transcription, render preparation, final encoding, and handoff.

## Confirm the available local stack

Before a long run, check the actual environment for a media probe and encoder, the available local ASR and aligner, a color-managed macOS conversion path when relevant, fonts, and the selected composition renderer. Record the important versions in the run notes. Reuse a proven project-local implementation when it matches the source rather than retyping a complex media pipeline from memory.

For a caption-first run, FFmpeg plus an editable ASS track can handle rotation, subtitles, opening type, screenshots, and simple event inserts without a motion-design framework. A tested Apple Silicon stack used `mlx-qwen3-asr` with Qwen3-ASR-1.7B, Qwen3-ForcedAligner-0.6B, `--timestamps`, and JSON output; locally cached models can run offline. Apple `avconvert` with `Preset1920x1080` supplied the reviewed SDR intermediate for that source. Check installed CLI help and the resulting color and dimensions before reusing this path; it is a concrete adapter, not a mandatory dependency or universal preset.

If the preferred local ASR is unavailable, find another local adapter or report the dependency; do not silently send the recording to a cloud transcription service. If the preferred Apple color path fails, a tested FFmpeg tone-map may be used with stricter frame comparison. If there is no compatible audio track, stop instead of delivering silent or corrupt media.

## Inspect before transforming

Record at least:

- source path, size, duration, frame rate, encoded and displayed dimensions, and rotation;
- video codec, bit depth, color primaries, transfer, matrix, range, HDR or Dolby Vision side data;
- all audio tracks, default disposition, sample rate, channels, loudness, and true peak;
- chapters, timed metadata, location, device, creation time, and data tracks;
- decode errors, black or frozen intervals, opening and tail room, and visible sensitive content.

Generate a contact sheet across the full recording and inspect likely openings, transitions, screens, and endings. Technical metadata does not replace looking at the footage.

A portrait take can be stored as sideways landscape pixels with no useful rotation tag. Confirm the orientation visually, then rotate the pixels into the intended display orientation before considering a crop. Do not center-crop a sideways frame or merely attach another rotation tag. This is distinct from a genuinely horizontal event insert whose full-width context may need to remain visible on the vertical canvas.

## Transcribe locally and preserve timing evidence

Default to a local Chinese ASR model with word-level alignment. Keep the raw ASR output alongside a corrected transcript; corrections should repair recognition and punctuation without silently rewriting the speaker.

Review:

- proper nouns, product names, English words inside Chinese speech, numbers, and negation;
- the exact audio at every proposed cut boundary;
- monotonic timestamps and source-duration bounds;
- captions after retiming, not only before editing.

ASR is an adapter, not an architectural dependency. If a different local model is more accurate or already available, use it while preserving the same evidence and outputs.

Use an existing SRT to locate source material, then refine actual cut points from the sound. A cue can include a long wait, part of a neighboring word, or an imprecise sentence ending. Compare local alignment with the waveform and listen at the boundary when audio playback is available; neither an old SRT nor a second ASR pass is infallible. A supported correction may move the cut slightly outside the old cue while preserving the whole spoken word. Quantize carefully to output frames, record the actual retained intervals, and recheck the assembled excerpt for stray leading/trailing words and clipped endings. Do not describe model comparison or waveform inspection as human listening.

## Convert color, do not relabel it

iPhone portrait sources may be HEVC Main 10, BT.2020 HLG, and Dolby Vision Profile 8 even when the desired delivery is ordinary SDR. A renderer that merely emits H.264 or changes tags can leave skin washed out, highlights clipped, or the whole image too bright.

- Prefer a color-managed conversion that has been tested on representative frames. On macOS, AVFoundation or another Apple color-managed path may reproduce iPhone material better than a generic tone-map.
- A carefully configured FFmpeg `zscale` plus tone-map path can be a fallback, but it typically works from the HDR base layer rather than fully applying Dolby Vision RPU behavior.
- Compare opening, skin, white clothing, windows, and specular highlights against the source on actual rendered frames.
- Output explicit Rec.709 primaries, transfer, matrix, and range; remove stale HDR side data.

There is no universal tone-map preset. The acceptance test is the encoded picture, not the command string.

## Handle camera audio deliberately

Explicitly map the compatible default AAC track rather than every audio stream; iPhone files can contain an additional spatial audio track that common FFmpeg builds cannot decode.

Measure the edited program before normalization. If true peaks are already near 0 dBFS, compression or limiting must create headroom before raising integrated loudness. A social delivery around -18 to -14 LUFS with controlled true peak is a useful neighborhood, not a mandatory target independent of the material.

Check:

- left/right balance and channel choice;
- clicks or truncated consonants at hard cuts;
- A/V start time, end time, and drift;
- loudness and true peak on the final encode.

## Make captions for viewing, not transcription storage

Segment by short semantic unit and natural breath. Keep enough context to understand the line while avoiding dense two-line paragraphs. Correct mixed Chinese/English spacing and names. Use one visible subtitle system in the frame; platform subtitle tracks may still be uploaded for accessibility and search.

Do not burn raw fixed-character ASR line breaks into the video. Write display cues by phrase, preserving names and English terms as units. Keep raw alignment separate from editorial display corrections so a repaired word or omitted filler does not lose its timing evidence. Zero-duration character tokens can occur in forced alignment; group them into positive-duration phrase cues and validate complete text coverage, ordering, and source bounds.

When retiming through cuts, bind a cue's start and end to the same retained source segment. A boundary lookup that maps the start to one segment and the end to another can turn a normal cue into a subtitle that remains on screen for tens of seconds.

When adding an excerpt, lock its actual encoded duration before shifting subsequent main-take cues. Either map the excerpt's word times through its source intervals or align its assembled audio anew. Clip boundary cues to their own retained interval so text does not bleed into the next scene. Keep one source-to-final map for all inserts and returns.

### Place captions above the platform interface

For this creator's Douyin and Xiaohongshu talking-head shorts, use the lower-middle picture as the caption area. Bottom-aligned desktop subtitles are not a good default: usernames, descriptions, topics, music labels, navigation, and right-side action buttons occupy that space.

For a 1080×1920 master, start by fitting the **whole visible caption box**, including the second line, stroke, and shadow, around 60–72% of frame height (roughly y=1150–1380). Initially leave the bottom quarter free of essential text and keep the right action rail clear. These are conservative editorial starting points for this creator, not official shared platform specifications. Actual app layout, device ratio, description length, product/activity cards, and subject position take precedence. Do not push captions over the eyes or mouth; adjust the composition or use a checked per-scene position when the default conflicts with the speaker or proof asset.

Set layout against the final encoded canvas. In ASS, verify alignment and any per-cue `\pos` / `\move` overrides as well as `MarginV`; changing a style margin will not move a cue with an explicit position. Prefer fewer words per cue or a sensible line break over shrinking the type to squeeze around platform controls. Give screenshots, URLs, and CTA labels their own space so they do not compete with the raised captions.

Before delivery, inspect the longest one- and two-line captions, a normal talking-head frame, and a screenshot/CTA scene inside a current target-platform playback view or a clearly labeled UI approximation. Include the username, a representative multi-line description, topic/activity labels, and right-side actions; a blank phone bezel is not this check. Keep text readable in the normal collapsed-description state, and inspect any other state central to the intended placement. Recheck the current UI when the platform or format changes; the expanded comments or description panel may intentionally cover the picture and cannot be solved by a universal safe rectangle. Keep the UI simulation out of the delivered video.

Inspect captions in the encoded MP4 at:

- cut boundaries;
- full-screen graphics and PiP scenes;
- the widest and longest lines;
- the lower-middle caption area with target-platform UI overlaid;
- the first and last cues.

## Verify time-dependent design in time

A contact sheet is good at hierarchy and coverage but weak at diagnosing short-lived annotations, easing, flicker, a mask that trails its target, or an element that survives one frame too long. When the composition contains timed graphics, moving PiP, dynamic privacy treatment, or layout changes, add temporal evidence proportional to the risk:

- inspect a settled frame for each important visual beat, not only its entrance midpoint;
- inspect a short consecutive-frame burst around fast annotations, movement, or a suspected flicker;
- inspect immediately before, during, and after every materially changed scene or mask boundary;
- derive the face/head exclusion area from representative positions across the affected interval, or from tracking when movement is substantial, rather than trusting one convenient frame;
- for a user-reported timecode, retain the same-timecode before/after/final comparison until the encoded delivery passes.

The goal is not maximum frame extraction. Choose samples that can reveal the failure in question. A stable subtitle-only stretch does not need the same evidence as a moving screen mask or a panel crossing a face.

If a beat sheet or storyboard exists, compare it with the encoded video as well as inspecting the pixels: important proof and explanatory roles should not have silently disappeared, and any added visual should have a defensible role rather than being unplanned decoration.

## Separate the platform cover from the opening

A 3:4 Xiaohongshu cover is a standalone image, while the portrait video can remain 9:16. Recompose the image for its destination and label each output by platform or aspect ratio. Verify the dimensions and the exact file referenced by the preview and upload form; generating a correct 3:4 file does not help if the default cover path still selects 9:16.

Keep a natural take moving immediately by default. A cover frame or hold is a separate editorial choice, not a consequence of needing a thumbnail. If the user requests a one-frame cover, insert exactly one encoded frame using the video's own aspect ratio and verify frame zero and frame one. Otherwise do not force the standalone cover into the video. Inspect the final opening for unintended frozen or black frames.

## Remove private and incompatible material

For a public delivery:

- explicitly map only the intended video and audio streams;
- drop camera data tracks, chapters, global and stream metadata, device and software labels, GPS, and creation timestamps unless deliberately retained;
- inspect filmed screens, notifications, certificates, QR codes, family material, and readable background text;
- preserve public proof while cropping, masking, blurring, or redrawing only what creates a real risk.

Do not upload the original phone MOV as a shortcut.

## Final QA

Before handoff or upload, verify the final file itself:

1. Decode completes without errors.
2. Container, video, and audio start at zero and end together within a harmless frame tolerance.
3. Display is 9:16, typically 1080×1920 at a stable delivery frame rate, H.264 plus AAC 48 kHz, and SDR Rec.709 when intended.
4. No accidental black opening, black tail, freeze, stale rotation, HDR side data, extra audio, or data streams remain.
5. Loudness, peaks, channel balance, and cut joins are acceptable.
6. The standalone cover has the destination ratio, a natural expression, a balanced feed-size layout, and the correct preview/upload file; frame zero follows the chosen opening without an unintended hold.
7. Captions are correct, retimed, readable above the target platform UI, and never stuck or duplicated; long and two-line cues have been checked in context.
8. Graphics explain what they claim to explain, do not hide the face unintentionally, and stay inside platform-safe zones.
9. Sensitive metadata and visible private information are absent.
10. Representative opening, middle, graphic transitions, and ending frames have been visually inspected; time-dependent risks have adjacent-frame or short-interval evidence.

A renderer's success code, a Studio preview, or a single contact sheet is not enough on its own. When one sampled frame suggests a crop, obstruction, or transition failure, inspect adjacent frames before diagnosing the whole scene. Keep a compact QA report with measured facts and the frames that support the visual judgment.

If the intended platform rejects the final duration, aspect, codec, or classification, do not silently cut meaning to satisfy it. Report the live constraint and offer the honest options: revise the edit with the user, publish in another supported format, or postpone that destination.

## Adaptable artifact contract

Names may follow the owning project, but keep the roles recognizable:

```text
project/
  source/                 # immutable original or provenance record
  work/
    inspect/              # technical report and contact sheets
    transcript/           # raw alignment and corrected transcript
    process/              # content map, cuts, captions, timeline map
  hf-project/             # optional editable HyperFrames composition
  output/
    *.ready-to-upload.mp4
    *.cover.jpg
    *.srt
    QA.md
    NEXT_TIME.md          # optional
```

Do not duplicate multi-gigabyte media merely to satisfy this shape. Keep a single owning copy or a clearly documented, verified derivative.
