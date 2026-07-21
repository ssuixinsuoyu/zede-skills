# zede-skills

这是一个可用 `skills` CLI 一键安装的个人 Agent Skills 合集。每个 Skill 保持独立目录，资源文件随 Skill 一起发布；`my-skills` 只负责识别意图并路由，不重复实现子 Skill 的功能。

## 一键安装全部 Skill

```bash
npx -y skills add ssuixinsuoyu/zede-skills -g --all
```

该命令会安装 5 个功能 Skill 和 1 个总入口 Skill。

## 只安装一个 Skill

```bash
npx -y skills add ssuixinsuoyu/zede-skills -g --skill content-topic-ideator
```

把最后的名称替换为下表中的任意 Skill 名称即可。若只安装功能 Skill，不会自动安装总入口或其他子 Skill。

## 更新

更新本仓库已安装的全部 Skill，重新执行一键安装命令即可用仓库最新版本刷新现有副本：

```bash
npx -y skills add ssuixinsuoyu/zede-skills -g --all
```

## Skill 清单

| Skill | 用途 |
| --- | --- |
| `my-skills` | 总入口。判断请求属于选题、视频文案、学习还是视觉讲解，并路由到对应子 Skill。 |
| `content-topic-ideator` | 为自媒体账号批量生成差异化、可拍摄且附可核查来源的候选选题，也可先分析公开账号再给方向。 |
| `zede-video-copywriter` | 从选题出发，先确认使用者真正想表达的核心观点，再从零写成一篇可直接口播的完整视频文案。 |
| `zede-plan-learning-roadmap` | 逐题澄清目标并诊断基础，在确认后生成有依据、可执行、可验收且能持续重排的学习路线。 |
| `interactive-learning` | 一次一问地带学，根据回答动态调整讲解，并用复述和迁移应用判断是否真正掌握。 |
| `interactive-explainer` | 把完整中文口播稿制作成 1920x1080、可前后点击、适合录屏的单文件 HTML 视觉讲解。 |

## Codex 使用示例

让总入口自动选择：

```text
$my-skills 我想用三个月学会 Python，并且最后能独立做一个自动化项目。
```

直接调用某个 Skill：

```text
$content-topic-ideator 根据我的 AI 自媒体账号，给我 20 个附直接来源的选题。

$zede-video-copywriter 把这个选题从零写成一篇可直接念的 90 秒抖音口播稿。

$zede-plan-learning-roadmap 帮我制定一条从零开始学习视频剪辑的路线。

$interactive-learning 一次一题教我理解 Python 的函数。

$interactive-explainer 把这份中文口播稿做成可以前后点击的录屏 HTML。

```

## 运行条件

- 研究型选题、学习资源核验和视觉参考研究需要联网能力。
- `interactive-explainer` 的完整流程需要可用的图像生成能力；最终视觉验收需要浏览器。
- Skill 默认不会替用户发布内容、创建远程仓库或推送代码。

## 许可证

本仓库采用根目录 [LICENSE](LICENSE) 中的自定义非商业许可证。个人、教育、研究及其他非商业用途可以使用、复制、修改和分享；商业使用需要事先获得授权。
