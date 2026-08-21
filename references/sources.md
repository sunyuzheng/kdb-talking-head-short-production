# Sources and provenance

This skill is a synthesis of repeated real productions. These sources explain why the guidance exists; they are not mandatory templates for a new video.

## Skill-writing method

- [Best practices for writing skills](https://github.com/grapeot/context-infrastructure/blob/main/rules/skills/bestpractice_skill_writing.md) by grapeot. The skill follows its result-determinacy approach: define the outcome, acceptance criteria, resources, boundaries, output contract, and observed failures without overfitting a rigid SOP.

## Production cases

- Five consecutive KDB one-pass talking-head iterations established the editorial workflow: conservative semantic editing, first-frame covers, explanatory graphics, context-aware openings, next-recording advice, and final delivery QA.
- The public Short [提高自己天花板最快的方法：先试一次你“不敢”的事](https://youtube.com/shorts/o08HjmNSEBE) supplied the latest end-to-end production evidence. Its real rework included overly small mobile type, an opening card that covered the face, wrapped chapter counters, iPhone HDR handling, caption retiming, and encoded-file QC.

## Existing implementations and adjacent skills

- [lizheng-video-production](https://github.com/sunyuzheng/lizheng-video-production) contains the existing KDB transcription, subtitle, filler-cut, title, and content-asset implementation. Use its `lizheng-video-editing` skill for broader interview, highlight, article, and channel-asset production.
- [HyperFrames](https://github.com/heygen-com/hyperframes) is the optional composition layer used for designed explanatory graphics.
- `talking-head-recut` is an optional runtime skill for graphic packaging after the spoken edit is locked. It is not bundled here and should be used only when it is installed in the current environment.

Use this skill for end-to-end production of one recorded vertical talking-head short and the publication approval boundary. Use the adjacent tools only when their narrower job actually applies.

## Media boundary

No source MOV, rendered MP4, photographs, private transcripts, API credentials, browser state, platform cookies, or owner-local absolute paths belong in this public repository.
