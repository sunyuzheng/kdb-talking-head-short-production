# 单人口播：剪辑、字幕、画面、封面与发布文案

拿到一段录好的单人口播原片（长短都可以），剪成适合全平台发布的成片：只剪明显说错和重复，精校并烧录字幕，加帮助观众理解和记住观点的画面。默认一起交付 **MP4、精校 SRT、9:16 和 3:4 封面、各平台的 `发布文案.txt`**。上传和排期不在这份 Skill 里，由发布的人负责。

Skill 只写“什么算做好”和真正不能越过的边界，怎么做由执行的 Agent 按当期素材判断；过去发过的成片只是例子，不是标准。

这个仓库是给 Agent 使用的 Skill，不是一个已部署的自动剪辑服务。媒体处理、转写和平台操作需要运行环境提供工具。规则以 [SKILL.md](SKILL.md) 和 `references/` 为准，这份 README 只说明怎么用。

## 给剪辑和运营同学

**视频已经剪好，只缺文案**：把对应的精校字幕、现有标题／封面、目标平台与相关链接一起交给 AI。

```text
使用 $kdb-talking-head-short-production，只补这条成片的发布文案。
读取最终字幕和已有标题／封面，按全平台准备（YouTube、Instagram、小红书、抖音、视频号）。
按本期内容放合适的链接；输出发布文案.txt，每个平台的正文都能直接复制。
没核实的链接和权益写在文件开头的说明里，不要猜。
这次不重新剪辑。
```

也可以让已有的 Agent 直接阅读 [publication-copy.md](references/publication-copy.md)，再用 [发布文案模板.txt](templates/发布文案模板.txt) 填写，不必为了补文案安装剪辑软件。

**完整制作**：

```text
使用 $kdb-talking-head-short-production 处理这条单人口播。
一起交付成片、SRT、封面和发布文案.txt。
```

剪多少、字幕放哪里、加什么画面，都由 Agent 按 Skill 里的标准自己判断，不需要在提示里逐条交代。

## 为什么它带有个人偏好

立正希望自然说完就能做出来，不想每次为了后期补录；画面要帮观点更容易懂、记得住，但不堆装饰。这些选择不一定适合所有人：需要练口播的人可以加回录前指导和补录，演示视频可能需要更多屏幕画面，其他创作者应该换成自己的口吻、账号、链接与审批方式。[个人偏好文件](references/creator-profile.md) 把这一层单独列出，公开 Skill 不包含账号登录态或发布许可。

实现也可以替换。默认本地中文 ASR；MLX、FFmpeg、Apple 色彩转换等只是实际用过的工具，HyperFrames 是可选的图形工具。缺少某个工具时，先判断有没有可靠的替代，不为了套框架增加工作。

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

## 文件地图

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](SKILL.md) | Agent 主入口：交付什么、什么算做好、边界、按需读什么 |
| [references/editorial.md](references/editorial.md) | 开头、剪辑、画面、封面怎么判断，以及真实返工中的失败 |
| [references/delivery.md](references/delivery.md) | 转写、剪辑点、颜色、声音、字幕时间与成片验收里容易出错的地方 |
| [references/publication-copy.md](references/publication-copy.md) | 各平台发布文案怎么写，也可以单独使用 |
| [templates/发布文案模板.txt](templates/发布文案模板.txt) | 可复制的交付容器 |
| [references/product-recommendations.md](references/product-recommendations.md) | 口播提到书或商品时，素材和购买引导怎么准备 |
| [references/creator-profile.md](references/creator-profile.md) | 可替换的个人偏好与公开入口 |
| [references/sources.md](references/sources.md) | 来源与真实返工 |

不包含原始视频、私密转写、私人路径、账号凭证、Cookie 或平台登录态。多人访谈与长视频内容资产（文章、高光等）可使用 [lizheng-video-production](https://github.com/sunyuzheng/lizheng-video-production)；独立标题封面能力有更细的编辑与成图指导。

文档与代码采用 [MIT License](LICENSE)。方法来源和许可边界见 [sources.md](references/sources.md)。
