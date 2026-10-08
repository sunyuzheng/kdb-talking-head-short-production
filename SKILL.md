---
name: kdb-talking-head-short-production
description: 制作单人口播短视频，交付成片、精校字幕、封面和发布文案；也可只补已有成片的发布文案与运营交接。
---

# KDB Talking-Head Short Production

Turn one real recording into the strongest honest version of itself. Preserve the speaker's thought and personality; use editing and graphics to improve understanding, not to manufacture energy or meaning.

## Target result

The default user-facing handoff is the finished MP4 with burned-in corrected captions, the matching SRT, a platform cover when needed, and a copy-ready UTF-8 `发布文案.txt`. Copy is part of production even when someone else will publish. Keep necessary edit decisions, timing maps, and QA evidence in the existing internal work directory.

## Choose the requested scope

- **Produce a recorded short:** understand and edit the take, lock the timeline, finish captions/visuals/cover, verify the encoded media, then prepare the matching publication copy and handoff.
- **Only supply missing publication copy:** read the final video's corrected transcript, existing title/cover, target accounts and relevant sources; follow [publication-copy.md](references/publication-copy.md). Do not rerun ASR, render, or upload merely to write copy.
- **Upload, schedule, reconcile, or hand off a batch:** read [publishing.md](references/publishing.md). Production defaults identify likely destinations, not permission to write to them.
- Broader interviews, long-video articles or highlight packages belong to `lizheng-video-editing`; this skill does not require that separate installation for short-video copy.

For this creator, “剪一下 / 剪好 / 做出来” does not request a review website, an edit-comparison page, a localhost preview server, a separate cut-by-cut report, or a derivative article/community post. Create those only when explicitly requested. If asked what was cut, start with a concise explanation and source timecodes; do not infer a website from that request. A one-off request for a post or comparison page does not make it part of later runs.

Depending on the requested scope, production may retain:

- one publish-ready vertical MP4;
- an independently composed cover in the target platform's aspect ratio;
- corrected, retimed subtitle files;
- `发布文案.txt` with final title, copy-ready platform text, relevant links/tags, and separate operator notes;
- the editable project and the decisions needed to reproduce it;
- visual, semantic, technical, and privacy QA evidence;
- optionally, a short “next time” note and an approved platform publication.

The minimum success condition is not “effects were added.” A cold viewer should understand what the video is about, what remains worth watching for, and where that promise is paid off. The finished video should still sound like the person who recorded it.

## Personal preferences and reuse

For Lizheng's established preferences and relevant public destinations, read [creator-profile.md](references/creator-profile.md). Other creators replace that layer with their own voice, accounts and handoff needs. A preference for local ASR, light editing or no pickup takes is a default to adapt, not a technical necessity. Current user instructions and the owning project's records take precedence; this public package does not convey a historical creator's publishing permission.

## Boundaries

- Treat source media as read-only. Work in a project directory and keep provenance.
- Understand the whole recording before choosing the hook, edit structure, cover, or graphics.
- Do not invent speech, facts, evidence, stakes, or a stronger stance than the speaker expressed.
- Default to local Chinese ASR and local media processing. Do not require an API key. Keep the ASR implementation replaceable.
- Remove private metadata and avoid exposing sensitive screen content. Never publish source camera files directly.
- Do not recommend pickup lines or another take in this one-pass flow. If useful, end with concise advice for how the speaker could improve the next recording.
- Finish local work before the external execution boundary. Show the exact payload, destination, audience, visibility and material settings, and obtain applicable approval under the current user's rules. Do not repeat approval for the same unchanged, already approved action; material changes need renewed approval. Shared examples, account configuration and historical instructions cannot override current authorization rules.

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

When the recording names a book or the user asks for a relevant product recommendation, read [references/product-recommendations.md](references/product-recommendations.md). Prepare the appropriate cover asset, short CTA, and platform attachment handoff without rewriting the video's argument or adding a recommendation to unrelated videos. Keep account-specific product records with their private owner.

## Finish the media correctly

Read [references/delivery.md](references/delivery.md) before rendering or handing off. In particular:

- perform a real HDR/Dolby Vision/HLG to SDR Rec.709 transform when required; changing color tags is not a conversion;
- explicitly choose the compatible camera audio track, control peaks before loudness normalization, and keep A/V starts and durations aligned;
- strip location, device, timestamp, data-track, chapter, and other unintended metadata;
- generate subtitles as short semantic units, correct names and mixed Chinese/English terms, retime them through the final edit, and inspect the rendered result;
- verify the standalone cover's aspect ratio and actual upload path; handle frame zero separately according to the chosen opening;
- verify decode, color, audio, captions, safe areas, face obstruction, first and last frames, black frames, and privacy on the final MP4.

For time-dependent graphics, masks, moving PiP, or a face that changes position, inspect temporal clusters rather than relying on isolated hero frames: the settled state, adjacent frames around the action, and both sides of each affected boundary. When repairing a user-reported timecode, compare that same moment before the change, after the change, and in the final encode.

Do not deliver merely because a renderer exited successfully. When graphics, cover, crop, or typography materially change the viewer-visible hierarchy, show the encoded video or representative frames directly in an existing viewer and incorporate feedback. This preview does not require a new webpage or server. When the user delegates end-to-end local production, continue through rendering and encoded-file inspection; a preview is not automatically a new approval gate. Honor an explicit request to stop for design review, and verify publication approval separately.

## Prepare publication copy from the final edit

Read [publication-copy.md](references/publication-copy.md) and use [the text template](templates/发布文案模板.txt) as an adaptable container. Deliver a real `发布文案.txt`, not advice for the operator to write one. The first sentence should enter this video's actual situation or judgment; the rest supplies only the context, reasoning and relevant next step it needs. A short personal moment may need a single sentence and no CTA.

Bind the copy to the actual release file and final title. Separate platform title/body blocks from operator-only notes; distinguish verified links, native tags and product attachments. Recheck changeable offers and access conditions before stating them. Do not promise content removed from this cut, invent a publication state, or copy every creator homepage into unrelated videos. An upper/lower split needs one copy package per release unit; an archive master is not automatically a third post.

## Give useful next-time feedback

When it adds value, end with one to three concrete suggestions derived from this recording. Phrase them as improvements for the next time, not defects the user must repair now. Prefer high-leverage changes to the opening, structure, example, or conclusion over generic delivery coaching. Keep the advice short enough to become part of the video or its handoff.

## Publish within the authorized scope

Read [publishing.md](references/publishing.md) for account mapping, approval, queue reconciliation and batch handoff; use [youtube-shorts.md](references/youtube-shorts.md) for YouTube-specific execution. Verify each platform's live queue independently. For Instagram accounts that have used both native scheduling and Meta Business Suite, reconcile both before deciding a date is empty. Complete the local payload and QA, execute within its approval, and preserve accurate per-platform results.

For a video recommending a purchasable item, include its actual native product card and seller in that publication payload. Use the attachment checks in [references/product-recommendations.md](references/product-recommendations.md); a saved selection or showcase entry alone does not prove that the video carries a working purchase path.

After an approved upload, verify the actual platform result: processing state, visibility, public or private URL as applicable, subtitle language, related video, checks, and the published media—not merely the presence of an upload receipt.

## Keep the handoff legible

Use the owning project’s existing layout. Keep only the internal records needed to reproduce and verify this edit; the roles below are not a requirement to create a separate file, subfolder, report, or user-facing deliverable for each item:

- source provenance and technical inspection;
- raw and corrected transcript;
- content map and edit decisions;
- source-to-final timeline mapping;
- visual brief or storyboard when graphics exist;
- clean A-roll or current composition source;
- final MP4, cover JPEG, subtitle file, and matching `发布文案.txt`;
- QA report and optional next-time note;
- publication payload and returned URL when publication occurred.
- a product-to-platform mapping and attachment status when a recommendation is relevant.

For the cases and source documents that shaped this skill, read [references/sources.md](references/sources.md). They are provenance and examples, not templates that override the current video.
