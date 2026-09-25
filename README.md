# midicn · music-soundfonts

**音色库（SoundFont）目录与分发的公开材料仓** —— 服务站点 <https://sf.midicn.com>。

本仓装的是 **目录政策、许可分级与可复现台账**；音色文件本身以 **Release 资产**发布
（`sf-soundfonts-v1`），不进本仓。

---

## 一 · 这个站解决什么问题

MIDI 曲目用什么音色播放，很影响听感。音乐库（<https://lib.midicn.com>）为了控制体积，
**只内置一个通用音色**；想换音色，就到声库站取。两条路径：

```
音乐库 →（想换音色）→ 声库站 sf.midicn.com → 下载 .sf2 → 回音乐库播放器「选择本地音色文件…」
```

浏览器播放器只能载入 `.sf2`。你选择的本地音色文件**只存在你自己浏览器的缓存里，不会上传到任何服务器**。

## 二 · 目录范围（我们从哪里收集）

| 来源 | 抓法 | 说明 |
|---|---|---|
| [musical-artifacts.com](https://musical-artifacts.com/) | JSON 接口（`tags=soundfont`） | 唯一提供**批量结构化许可字段**的来源 |
| [FreePats](https://freepats.zenvoid.org/) | 逐乐器页解析 | DFSG 合规、**逐条写明记录人与许可**；民族/世界乐器的主力 |
| [sfzinstruments](https://sfzinstruments.github.io/) | `data/sfz/instruments.yml` | 钢琴与鼓组名品（Salamander 等） |
| [MuseScore 官方分发](https://ftp.osuosl.org/pub/musescore/soundfont/) | 目录索引 + `HEAD` 实测体积 | **FluidR3_GM / MuseScore_General（MIT）** |

**页面不实时调用任何第三方接口** —— 台账落在本地，对方改版不会让目录失效。

## 三 · 许可分级（F1–F4）

两套分级**不要混**：音乐库给**曲目**分 C1/C2/C3（这首曲子能不能商用），本目录给**音色文件**
分 F1–F4（这个文件能不能再分发）。**同一个 F1 音色可以用来演奏 C3 曲目。**

| 档 | 条件 | 本站处置 |
|---|---|---|
| **F1** | CC0 / 公有领域 / WTFPL / Unlicense | ✅ 站内托管 + 直接下载 |
| **F2** | CC BY / MIT / BSD / ISC —— 须署名、可商用、可改作 | ✅ 可托管，**逐条给出署名与许可原文** |
| **F3** | CC BY-SA / GPL —— **有传染性** | ⚠️ **只给来源指引，不托管** |
| **F4** | 禁止商用 / 禁止改作 / Sampling 系列 / 来源存疑 / 版权受限 / 未标注 | ❌ **本站不收录** |

**入档规则是两条都满足**：① 允许**商用**再分发；② 允许**改作**。
音色的主要用途就是衍生使用（拿采样做音乐、改编），只满足一条的收了会误导读使用者。

三个具体判断的例子：

- **CC BY-ND** —— 允许原样再分发，但**禁改作** → F4，不收录。
- **CC BY-NC** —— 允许改作，但**禁商用** → F4，不收录。
- **CC Sampling Plus 1.0** —— 允许采样/改编，但**整包原样分发仅限非商业** → F4，只给来源。

## 四 · 少数「来源存疑」条目：不列出、不推荐

目录里有相当一批条目被**来源站自己**标记为「来源存疑」（多为从商业游戏 ROM 提取的音色）。
这类我们**既不列出、也不推荐** —— 再分发几乎必然侵权，**这种赌不做**。
完整逐条清单（含这些）在公开台账里，供审计。

## 五 · 可复现台账

全量逐条（含**每一条为什么收录 / 为什么不收录**）：

- 人读版：[`SOUNDFONT-CATALOG.md`](https://github.com/midicn/midi-library/blob/main/docs/SOUNDFONT-CATALOG.md)
- 机读版：[`soundfonts.json`](https://github.com/midicn/midi-library/blob/main/docs/soundfonts.json)

生成链（都在数据仓 `midicn/midi-library`）：

```
tools/sf_crawl.py       抓四个来源 → docs/internal/*.json
tools/sf_ledger.py      合并 + 分档 + 分类 → docs/SOUNDFONT-CATALOG.md + docs/soundfonts.json
```

**档位判定与分类只有一处实现**（`sf_ledger.py`）：抓取器只陈述事实（许可原文、标签、体积、下载地址），
不做判断。这样「可不可以分发」永远只有一个答案。

## 六 · Release 资产（站内托管）

`sf-soundfonts-v1` 里是**解包后的 `.sf2`**，全部为 **F1（可自由分发）**，每个文件顶部即注明
来源归档地址与 sha256（见资产同名的清单字段或站点的托管清单）。

体积红线：**只托管单个 ≤50 MB 的 `.sf2`**。更大的只给来源地址，自己取。

## 七 · 本仓内容的许可

- 本仓**文字材料**（README、政策、说明）：CC BY 4.0（可商用、可改写，须署名）
- 本仓**分发的音色文件**：**各自的原许可**，逐条标注；本站不改变原许可，也不主张权利

发现任何条目许可标注有误，或你认为某个文件不该在这里，请开 issue —— 我们会核并撤下。
