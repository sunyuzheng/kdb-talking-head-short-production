# Sources and provenance

This skill is a synthesis of repeated real productions. These sources explain why the guidance exists; they are not mandatory templates for a new video.

## Skill-writing method

- [Best practices for writing skills](https://github.com/grapeot/context-infrastructure/blob/main/rules/skills/bestpractice_skill_writing.md) by grapeot. The skill follows its result-determinacy approach: define the outcome, acceptance criteria, resources, boundaries, output contract, and observed failures without overfitting a rigid SOP.

## Production cases

- Five consecutive KDB one-pass talking-head iterations established the editorial workflow: conservative semantic editing, first-frame covers, explanatory graphics, context-aware openings, next-recording advice, and final delivery QA.
- The public Short [提高自己天花板最快的方法：先试一次你“不敢”的事](https://youtube.com/shorts/o08HjmNSEBE) supplied the latest end-to-end production evidence. Its real rework included overly small mobile type, an opening card that covered the face, wrapped chapter counters, iPhone HDR handling, caption retiming, and encoded-file QC.
- A caption-first mobile production was explicitly approved by the user in September 2026. It retained the coherent main take, used a large two-line cover over moving footage, and added a real post screenshot plus an approximately 30-second chronological event excerpt. Rework established the practical difference between nominal font size and rendered glyph size, missing portrait rotation metadata, silent setup time inside SRT cues, and neighboring words leaking across approximate cut points. These are transferable decisions and checks; the headline, layout, insert duration, source footage, and private project files are not bundled as a universal template.

- September 2026 post-publication feedback identified low cover text, an overfilled portrait composition despite a 3:4 output, an unflattering frame choice, and captions placed near the platform's bottom information overlays. The user requested future skill improvements only, not revisions to the already published post. This informs independent cover composition, expression selection, lower-middle captions, and UI-aware QA; it is negative production feedback, not measured audience-performance evidence.

## Existing implementations and adjacent skills

- [lizheng-video-production](https://github.com/sunyuzheng/lizheng-video-production) contains the existing KDB transcription, subtitle, filler-cut, title, and content-asset implementation. Use its `lizheng-video-editing` skill for broader interview, highlight, article, and channel-asset production.
- [HyperFrames](https://github.com/heygen-com/hyperframes) is the optional composition layer used for designed explanatory graphics.
- `talking-head-recut` is an optional runtime skill for graphic packaging after the spoken edit is locked. It is not bundled here and should be used only when it is installed in the current environment.

## External methodological comparison

- [Vincent Wei's `video-talkcraft`](https://github.com/Vincentwei1021/video-talkcraft), reviewed at commit `5d6637f1749bf046236c6b8b81eb2aa83f3499d3` on 2026-08-29, is a script-plus-finished-voiceover workflow for motion-designed explainer videos rather than an edit of a recorded mobile take. Its useful transferable ideas are semantic-beat planning, one primary visual job per beat, explicit visual handoffs, speech-anchored timing, measured face-safe regions, and temporal QA using settled and consecutive frames.
- This skill deliberately does not inherit `video-talkcraft`'s constant-motion requirement, mandatory treatment at every shot boundary, fixed visual language, prescribed sound-effect coverage, or default host-as-corner-chip composition. Those choices solve a different product and can conflict with a video-first, restrained talking-head edit.
- The upstream toolkit is distributed under PolyForm Noncommercial 1.0.0. No code, templates, motion cards, assets, or sound samples from that repository are copied into this skill; only the independently expressed editorial and QA principles above are cited and adapted.

Use this skill for end-to-end production of one recorded vertical talking-head short and the publication approval boundary. Use the adjacent tools only when their narrower job actually applies.

## Platform layout references

Reviewed in September 2026 as visual examples, not current official layout specifications:

- A [Douyin playback screenshot featuring Liu Run](https://imagepphcloud.thepaper.cn/pph/image/287/347/975.jpg), reproduced in a [2024 article](https://www.thepaper.cn/newsDetail_forward_26055470), shows bottom account/description overlays and a right-side action rail competing with low captions. It supports checking both regions, not a universal pixel boundary.
- A [2025 Xiaohongshu portrait-cover grid](https://image.woshipm.com/2025/05/28/75dfd954-3b6d-11f0-8928-00163e09d72f.png), reproduced in [this analysis](https://www.woshipm.com/operate/6222392.html), shows compact portrait cards and separate note titles beneath them. Some examples do use low cover text; raising this creator's cover copy is a personal preference, not a platform-wide rule.

Inspect the live target app when producing a new format or when its interface changes. Older examples explain the visual problem; they cannot certify today's safe area.

## Publication-copy and operator handoff update (2026-10-08)

An editor receiving recent shorts found `发布文案.txt` in the delivery folders but could not reproduce it from the previously shared skill. Earlier examples ranged from a single title and short body to complete YouTube, Instagram and Xiaohongshu blocks. The transferable fix is an explicit production stage, a copy-only mode, a plain-text template, and separate operator notes. Actual episode files, private publication manifests and account IDs remain outside this repository.

Operator questions about missing copy, main versus clip accounts, and separately publishable parts versus a complete master inform the handoff contract. An October queue reconciliation also found Instagram-native and Meta Business Suite schedules displayed separately; this is why an apparent gap must be checked across the account's scheduling entry points, not treated as proof of an empty slot. These are workflow observations, not engagement claims or permanent platform specifications.

The pre-existing local editorial update from user-supplied three-column cover grids is retained: a natural portrait, a short recognizable topic and a concrete related judgment, inspected at feed size. It is a design direction, not a fixed layout or evidence of improved reach.

## Media boundary

No source MOV, rendered MP4, photographs, private transcripts, API credentials, browser state, platform cookies, or owner-local absolute paths belong in this public repository.
