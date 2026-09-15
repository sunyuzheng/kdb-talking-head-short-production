---
name: kdb-talking-head-short-production
description: Turn one recorded single-speaker mobile video into a coherent, publish-ready vertical short through local transcription, content-aware editing, readable captions, selective explanatory graphics, technical and privacy cleanup, and optional explicitly approved platform publishing. Use when the user wants one raw talking-head take made ready to post. Use lizheng-video-editing instead for broader interview, highlight, article, and channel-asset workflows; use talking-head-recut only when the spoken edit is already locked and the remaining job is graphic packaging.
---

# KDB Talking-Head Short Production

Turn one real recording into the strongest honest version of itself. Preserve the speaker's thought and personality; use editing and graphics to improve understanding, not to manufacture energy or meaning.

## Target result

A complete run normally leaves:

- one publish-ready vertical MP4;
- an independently composed cover in the target platform's aspect ratio;
- corrected, retimed subtitle files;
- the editable project and the decisions needed to reproduce it;
- visual, semantic, technical, and privacy QA evidence;
- optionally, a short “next time” note and an approved platform publication.

The minimum success condition is not “effects were added.” A cold viewer should understand what the video is about, what remains worth watching for, and where that promise is paid off. The finished video should still sound like the person who recorded it.

## Boundaries

- Treat source media as read-only. Work in a project directory and keep provenance.
- Understand the whole recording before choosing the hook, edit structure, cover, or graphics.
- Do not invent speech, facts, evidence, stakes, or a stronger stance than the speaker expressed.
- Default to local Chinese ASR and local media processing. Do not require an API key. Keep the ASR implementation replaceable.
- Remove private metadata and avoid exposing sensitive screen content. Never publish source camera files directly.
- Do not recommend pickup lines or another take in this one-pass flow. If useful, end with concise advice for how the speaker could improve the next recording.
- Uploading or publishing is a separate external action. Before it, show the exact payload, destination, audience, visibility, and material settings; obtain approval for that payload.

## Form an editorial view first

Inspect the media, transcribe it, and review the whole recording before editing. Build a small content map that answers:

- What will the right viewer expect from this surface and first frame?
- What is the main viewer payoff: a judgment, result, method, change, demonstration, or story?
- What minimum context makes the opening understandable?
- What does the viewer already know, and what specific answer should remain open?
- Where does the body actually deliver that answer?
- Which moments are evidence, even if they look visually imperfect?

The opening can be a result, judgment, question, unusual detail, demonstration, or story tension. It does not have to be a detached “highlight” or an instant contrarian claim. A useful cognitive gap makes the viewer think “I understand X and want to know Y”; if the viewer cannot identify X, it is confusion rather than curiosity.

When designed visuals are useful, plan them in semantic beats rather than treating each subtitle or sentence as a new shot. One beat may span several sentences if they perform the same viewer-facing job. Bind important graphic changes to named words, phrases, pauses, or evidence moments on the locked final timeline so timing remains explainable after retiming.

Read [references/editorial.md](references/editorial.md) whenever the hook, structure, cut, illustration, or next-time advice requires judgment.

## Edit the spoken take

Start from continuity. Remove only material whose absence makes the thought clearer: obvious pre-roll and tail, abandoned starts, standalone filler, accidental repetition, irrelevant detours, or a corrected error when the correct version is present.

Make cuts at real acoustic and semantic boundaries. Prefer whole phrases or thoughts over syllable surgery. Keep useful pauses, emphasis, personality, and imperfect spoken rhythm. Reorder only complete semantic units when the resulting claim remains faithful and the visual discontinuity can be handled honestly.

Editing intensity follows the material and the user's request. A coherent take may need almost no cuts; a wandering take may support a bolder reconstruction. Do not use deletion percentage, cut count, or target duration as a substitute for listening.

For a coherent take where the user mainly wants subtitles, make natural continuity, corrected short captions, and a strong readable cover the baseline. Keep the original opening when it already establishes the subject and payoff. A successful run may have no interior speech cuts and no illustrations; additional evidence or graphics should earn their place in this particular recording.

Lock the spoken timeline before binding final captions or complex animation timing. Visual planning may inform an edit—especially when a real cut or sensitive screen needs coverage—but global timecodes should not be finalized against a moving timeline.

Once the spoken edit is settled, including any review the user requested, create a technically correct clean A-roll plus a locked, retimed caption track, and treat their timeline as immutable during graphic packaging. If the spoken edit later changes, regenerate the A-roll and timeline map rather than making undocumented cuts inside the graphics project.

## Add only visuals that do work

Use the simplest form that materially helps the viewer:

- short opening type to establish the subject or promise;
- a chapter rail when the spoken structure is otherwise hard to hold;
- a full-screen relationship or process diagram for an abstract mechanism;
- a redrawn UI, code view, or operation animation when a filmed screen is unreadable or sensitive;
- temporary PiP or split screen when person and interface both matter;
- a proof asset, photograph, or real screen when it carries evidence;
- one strong conclusion treatment when the idea benefits from emphasis;
- a chart only when real data exists.

There is no required number of illustrations. If the take is already clear, subtitles and a restrained opening may be enough. If using HyperFrames, load the `hyperframes` skill first and then the relevant composition skills; use it as an expression layer after the content decision, not as the source of the decision.

Give each designed beat one primary visual job. When a new visual becomes primary, decide whether the previous one should leave, recede, or remain because the comparison still needs it. The A-roll is the continuity layer; stillness, negative space, and an unadorned stretch are legitimate choices. Do not import a “constant motion” or “effect at every boundary” rule into a video whose clarity and human presence benefit from restraint.

Design for the phone-sized result, including the platform interface. For this creator's Douyin and Xiaohongshu talking-head videos, place captions in the lower-middle picture above the username, description, topic, and navigation overlays, rather than along the bottom edge. Check the encoded video with representative platform UI over it; see the caption placement guidance in [references/delivery.md](references/delivery.md). Keep one readable subtitle layer and protect the eyes and mouth.

Compose the standalone cover for its actual destination: a 3:4 Xiaohongshu cover and a 9:16 video are separate canvases. When available, use `video-title-and-cover` for detailed cover work; otherwise follow the self-contained cover criteria in [references/editorial.md](references/editorial.md). Treat the cover as its own editorial job: state the recognizable subject and the strongest supported reason to watch in very few, very large words. For cover hierarchy and real screenshots or event excerpts, use the relevant sections of [references/editorial.md](references/editorial.md). Their layouts and durations are choices, not required additions to a caption-only run.

## Finish the media correctly

Read [references/delivery.md](references/delivery.md) before rendering or handing off. In particular:

- perform a real HDR/Dolby Vision/HLG to SDR Rec.709 transform when required; changing color tags is not a conversion;
- explicitly choose the compatible camera audio track, control peaks before loudness normalization, and keep A/V starts and durations aligned;
- strip location, device, timestamp, data-track, chapter, and other unintended metadata;
- generate subtitles as short semantic units, correct names and mixed Chinese/English terms, retime them through the final edit, and inspect the rendered result;
- verify the standalone cover's aspect ratio and actual upload path; handle frame zero separately according to the chosen opening;
- verify decode, color, audio, captions, safe areas, face obstruction, first and last frames, black frames, and privacy on the final MP4.

For time-dependent graphics, masks, moving PiP, or a face that changes position, inspect temporal clusters rather than relying on isolated hero frames: the settled state, adjacent frames around the action, and both sides of each affected boundary. When repairing a user-reported timecode, compare that same moment before the change, after the change, and in the final encode.

Do not deliver merely because a renderer exited successfully. Share a concrete preview when graphics, cover, crop, or typography materially change the viewer-visible hierarchy, and incorporate feedback. When the user delegates end-to-end local production, continue through rendering and encoded-file inspection; a preview is not automatically a new approval gate. Honor an explicit request to stop for design review, and keep platform publication approval separate.

## Give useful next-time feedback

When it adds value, end with one to three concrete suggestions derived from this recording. Phrase them as improvements for the next time, not defects the user must repair now. Prefer high-leverage changes to the opening, structure, example, or conclusion over generic delivery coaching. Keep the advice short enough to become part of the video or its handoff.

## Publish only through an approval gate

If the user asks for YouTube Shorts publication, read [references/youtube-shorts.md](references/youtube-shorts.md). Other platforms follow the same boundary: prepare and verify locally first, then present the exact post payload and destination. Approval applies only to what was shown; a material change to title, description, related video, visibility, audience, subtitle track, or destination requires fresh approval.

After an approved upload, verify the actual platform result: processing state, visibility, public or private URL as applicable, subtitle language, related video, checks, and the published media—not merely the presence of an upload receipt.

## Keep the handoff legible

Project structure may adapt to the owner, but a durable run should make these truths easy to find:

- source provenance and technical inspection;
- raw and corrected transcript;
- content map and edit decisions;
- source-to-final timeline mapping;
- visual brief or storyboard when graphics exist;
- clean A-roll or current composition source;
- final MP4, cover JPEG, and subtitle file;
- QA report and optional next-time note;
- publication payload and returned URL when publication occurred.

For the cases and source documents that shaped this skill, read [references/sources.md](references/sources.md). They are provenance and examples, not templates that override the current video.
