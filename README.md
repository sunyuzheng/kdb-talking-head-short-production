# 单人口播短视频：剪辑、字幕、封面与发布文案

把自然录下的一段话，做成能直接交给运营发布的成片。默认一起交付 **MP4、精校 SRT、封面和 `发布文案.txt`**。

这个仓库是给 Agent 使用的 Skill，不是一个已部署的自动剪辑服务。它提供编辑判断、交付规则和可复用模板；媒体处理、转写和平台操作需要运行环境提供工具。

## 给剪辑和运营同学

之前拿到的版本主要写了剪辑，发布文案散落在实际项目和云端交接说明里。这次把它补成了主流程中的独立步骤：**剪完也写完；只缺文案也能单独补。**

- [发布文案怎么写](references/publication-copy.md)：从最终成片提炼内容，写各平台正文、相关链接、话题和运营说明。
- [发布文案模板.txt](templates/发布文案模板.txt)：可直接下载，删掉不适用的块，再填最终文本。
- [分发与批次交接](references/publishing.md)：发哪个账号、哪一个 MP4、哪些是母版、哪些已经排期。
- [完整 Skill](SKILL.md)：从原片到成片的入口。

**视频已经剪好，只缺文案**，把对应的精校字幕、现有标题／封面、目标平台与相关链接一起交给 AI：

```text
使用 $kdb-talking-head-short-production，只补这条成片的发布文案。
读取最终字幕和已有标题／封面，目标是 YouTube 和 Instagram。
按本期内容放合适的链接；输出发布文案.txt，正文能直接复制。
账号、使用哪个成片和已发布状态单独写进运营说明；没核验的不要猜。
这次不重新剪辑，也不上传。
```

也可以让已有的 Agent 直接阅读 [publication-copy.md](references/publication-copy.md)，不必为了补文案安装剪辑软件。分享给同事的是整个仓库或这份完整参考文件，不是单独一条缺少上下文的提示词。

## 完整制作怎样衔接

| 阶段 | 要解决的问题 | 主要参考 |
| --- | --- | --- |
| 看懂原片 | 这条在说什么，哪里有重说，哪些停顿有意义 | [编辑判断](references/editorial.md) |
| 锁定剪辑 | 选完整的一遍，保留自然语气，记录原片到成片的时间映射 | [技术交付](references/delivery.md) |
| 字幕、素材、封面 | 字幕精校并烧录；真实素材放在对应口播处；封面有清楚的观看理由 | [技术交付](references/delivery.md)、[编辑判断](references/editorial.md) |
| 写发布文案 | 让观众看懂本期内容，并找到适用的课程、访谈、社区或商品 | [发布文案](references/publication-copy.md) |
| 验收与交接 | 检查最终文件、文案一致性、账号和各平台实际状态 | [分发与交接](references/publishing.md) |

先锁定口播，再绑定字幕和图形的时间。文案以最终剪辑为准：删掉的内容不能继续当成短片卖点，上下集也不能共用一段与各自内容不符的介绍。

默认不做每期审阅网站、剪辑对照网页、伴读文章或复杂动效。需要说明剪掉什么时，时间码和简短理由就够；另有明确要求再扩展。

## 发布文案不是通用广告结尾

文案要保留视频里真正有用的判断、理由或情境。生活随想可能一句话就够；技术讨论需要解释关键区别；讲课程时给相关课程入口；讲一次采访时给对应完整版。没有相关下一步，就不硬加 CTA。

`发布文案.txt` 通常包含：

- 最终标题和各目标平台可直接复制的完整正文；
- 与本期相关且核对过的链接、话题；适用时注明原生 tag、商品卡或关联视频；
- 单独的运营说明：对应成片、目标账号、分集／母版选择、真实发布状态与待处理项。

不让运营自己补写正文，也不把“已生成文案”当成“已发布”。主号、会客厅、切片号分别映射，Google Drive 负责归档。

## 为什么它带有个人偏好

立正希望自然说完就能做出来，不想每次为了后期补录，也不需要每句都加动画。流程因此偏向完整表达、克制剪辑、准确字幕和清楚的封面。

这些选择不一定适合所有人。需要练口播的人可以加回录前指导和补录；演示视频可能需要更多屏幕画面；其他创作者应该换成自己的口吻、账号、链接与审批方式。[个人偏好文件](references/creator-profile.md) 将这一层单独列出，公开 Skill 不包含账号登录态或发布许可。

实现也可以替换。默认本地中文 ASR；MLX、FFmpeg、Apple 色彩转换等只是实际用过的工具。HyperFrames 是可选的图形工具，不是每期必经步骤。缺少某个工具时，先判断是否有可靠替代；不能为了套框架增加不必要的工作。

## 安装与使用

将完整仓库放进 Agent 使用的 skills 目录。以已有 Codex 本地配置为例：

```bash
git clone https://github.com/sunyuzheng/kdb-talking-head-short-production.git \
  ~/.codex/skills/kdb-talking-head-short-production
```

已有安装先查看本地改动，再快进更新；不要覆盖自己改过的偏好：

```bash
git -C ~/.codex/skills/kdb-talking-head-short-production status --short
git -C ~/.codex/skills/kdb-talking-head-short-production pull --ff-only
```

统一管理 Skills 的环境，也可克隆到自己的仓库目录，再让运行时指向这一份来源。只需要人工使用文案方法时，直接下载参考文件即可。

完整制作的调用示例：

```text
使用 $kdb-talking-head-short-production 处理这条单人口播。
保留自然表达，剪掉废弃重说和明显空白，保留有意义的停顿。
精校并烧录字幕，选自然人物帧做清楚的大字封面。
一起交付成片、SRT、封面和发布文案.txt；先完成本地交付，不上传。
```

## 交付目录保持简单

复用所在项目的布局，不强制改名或复制大文件。新项目可以这样组织：

```text
0-YYYYMMDD-主题/
  成片.mp4
  字幕.srt
  封面.jpg
  发布文案.txt
  原片/       # 私有来源，按当前归档规则保留
  工程/       # 对齐、剪辑决定、时间映射、渲染与必要 QA
```

一期拆两条，就按发布单元对应成片与文案；完整母版另标“仅归档”或本期明确用途。批量交付用一个简短清单列清条数、账号、文件和状态，不需要另造网页。

## 公开发布与云端流程

上传前准备准确的文件、正文、目的地、受众和设置，按照当前用户及工作区规则取得覆盖该 payload 的批准；已经批准且没变化的同一动作不重复询问。分享仓库、配置账号、历史案例都不能代替授权。自动化默认 dry-run，在执行边界核验批准。

排期要读真实队列。YouTube 和 IG 各自核对；IG 若用过原生排期和 Meta Business Suite，两处都要查，不能从一张日历的空白推定没有排期。上传后保存远端 ID 并读回，区分已上传、检查中、已排期、已发布。

准备做 iCloud 收件与云端 bot 时，再读 [CLOUD_FLOW.md](CLOUD_FLOW.md)。它是单文件迁移交接包，包含接收、去重、渲染、恢复与分发接口设计，**不代表这些服务已经部署**。

## 文件地图

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](SKILL.md) | Agent 主入口与模式选择 |
| [references/editorial.md](references/editorial.md) | 开头、自然剪辑、封标与素材判断 |
| [references/delivery.md](references/delivery.md) | 转写、颜色、声音、字幕与成片 QA |
| [references/publication-copy.md](references/publication-copy.md) | 独立可用的发布文案方法 |
| [templates/发布文案模板.txt](templates/发布文案模板.txt) | 可复制的交付容器 |
| [references/publishing.md](references/publishing.md) | 分发、对账与运营交接 |
| [references/creator-profile.md](references/creator-profile.md) | 可替换的个人偏好与公开入口 |
| [references/youtube-shorts.md](references/youtube-shorts.md) | YouTube 上传与核验 |
| [references/product-recommendations.md](references/product-recommendations.md) | 书／商品与实际挂载 |
| [references/sources.md](references/sources.md) | 来源、真实返工和相邻能力 |
| [CLOUD_FLOW.md](CLOUD_FLOW.md) | 云端迁移快照 |

不包含原始视频、私密转写、私人路径、账号凭证、Cookie 或平台登录态。多人访谈与长视频内容资产可使用 [lizheng-video-production](https://github.com/sunyuzheng/lizheng-video-production)；独立标题封面能力有更细的编辑与成图指导，本仓库仍保留可独立使用的基本判断。

文档与代码采用 [MIT License](LICENSE)。方法来源和许可边界见 [sources.md](references/sources.md)。
