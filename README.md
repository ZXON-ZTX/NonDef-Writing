# NonDef Writing

**直接陈述观点，用事实、推理和具体例子支撑。**

NonDef Writing 是面向中英文学术文本的 Codex skill。保留 **620组替换词条**，配合 **16类迁移规则**处理词库尚未覆盖的表达，减少空泛自辩、叠加限定和机械平衡句。

## 功能

- **减少防御性表达**：精简不增加信息的自我辩护、预设反驳和重复限定。
- **词条与规则结合**：适用的表达按原词条映射改写；未覆盖的表达继续按规则检查。
- **保留原意与证据边界**：保留数据、术语、公式、引文、必要条件和真实不确定性，不把推测写成事实。
- **保护显式免责声明**：只有文章中实际存在明确的“免责声明”或“Disclaimer / Disclaimers”标题、段首标签，才原样保留该部分，并提醒用户手动修改。没有显式标记时，不根据句意判定，也不输出提醒。
- **支持中文和英文**：保持原文语言；英文论文使用对应的英文表达方式。
- **默认输出改后正文**：不附修改说明；出现显式免责声明时，按规则附简短手动修改提醒。用户要求查看修改点时，按该项请求输出。

## 安装

将本仓库放入 Codex 的技能目录，文件夹命名为 `nondef-writing`。

Windows PowerShell：

```powershell
git clone https://github.com/ZXON-ZTX/NonDef-Writing.git "$env:USERPROFILE\.codex\skills\nondef-writing"
```

macOS / Linux：

```bash
git clone https://github.com/ZXON-ZTX/NonDef-Writing.git "$HOME/.codex/skills/nondef-writing"
```

也可以在 [Releases](https://github.com/ZXON-ZTX/NonDef-Writing/releases) 下载技能压缩包，解压后将 `nondef-writing` 文件夹放入上述目录。安装后在新建的 Codex 对话中调用。

## 使用

```text
$nondef-writing
请修改下面这段正文：
[粘贴中文或英文文本]
```

如果需要查看具体改动：

```text
$nondef-writing
请修改以下文本，并只列出修改点：
[粘贴文本]
```

简短示例：

| 原文 | 改写 |
| --- | --- |
| 我们对日志进行了分析。 | 我们分析了日志。 |
| We would like to point out that the sample was small. | The sample was small. |

样本大小等影响结论的信息仍需保留；删除的是没有增加信息的提示外壳。

## 执行顺序

**显式免责声明保护与总体约束 → 语义适用的原词条 → 未覆盖表达的迁移规则。**

所有修改基于同一份输入决定，不对新生成文字反复进行链式替换。没有适用条件的句子保持原样。

## 词库与规则

| 内容 | 位置 |
| --- | --- |
| 技能入口和总体约束 | [SKILL.md](SKILL.md) |
| 620组融合词库，E001—E620 | [Markdown](references/merged-replacements-620.md) · [TSV](references/merged-replacements-620.tsv) |
| 16类替换与迁移规则，R01—R16 | [规则正文](references/replacement-rules.md) |
| 全部620组词条对应的规则索引 | [规则索引](references/replacement-rule-index.tsv) |
| 第一批120组 | [词条](references/extra-replacements.md) |
| 第二批500组 | [词条](references/expansion-500.md) |
| 原始截图402行备查资料 | [原始记录](references/original-replacements.md) |
| 第二批词条的编写参考与来源说明 | [资料来源](references/open-source-references.md) |

默认融合词库为120＋500＝620组；原始截图记录另外保留供追溯。各批次和融合词库包含相同记录，不重复计算为新增条目。

本仓库保留现有技能的13个原文件，另提供此安装和使用说明。
