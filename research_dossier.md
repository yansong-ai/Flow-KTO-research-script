# Research Dossier: ICLR 2027 and RSS 2027 Conference Scenes

## 0. Scope, Currency, and Evidence Boundary

- Target venues: **International Conference on Learning Representations (ICLR) 2027** and **Robotics: Science and Systems (RSS) 2027**.
- Scene: conference.
- Verification date: **2026-07-14** (Asia/Shanghai).
- Target years: **ICLR 2027 and RSS 2027, confirmed by the user**. Venue selection remains open; the target years are fixed.
- ICLR 2027 status on the verification date: the official Future Meetings page only states **“ICLR 2027: West Coast North America”**. The conventional official 2027 Call for Papers URL returns HTTP 404. No official ICLR 2027 CFP, Author Guide, Reviewer Guide, page limit, deadline, template, anonymity policy, supplementary-material policy, code policy, or LLM policy was located in the reviewed official sources.
- RSS 2027 status on the verification date: the supplied official entry `https://roboticsconference.org/` serves **RSS 2026**. The probed `/2027/` and `/2027/information/cfp/` paths return HTTP 404. No official RSS 2027 CFP, author instructions, reviewer guide, page limit, deadline, template, anonymity policy, video/supplement policy, or rebuttal policy was located in the reviewed official sources.
- Consequence: every numerical or procedural rule below is explicitly labeled **ICLR 2026** or **RSS 2026**. These are planning baselines, not asserted 2027 rules. Both target cycles must be rechecked when their official pages and templates are published.
- Local-example boundary: five PDFs under `/home/robotera/文档/ICLR_template` and the two selected RSS exemplars `/home/robotera/文档/RSS/Generalizing from References using a Multi-Task.pdf` and `/home/robotera/文档/RSS/DexImit.pdf` were read with `pdfinfo`/`pdftotext`. They are used to learn argument and evidence organization. All three files in `ICLR_template/Normal/` were independently matched to official ICLR 2026 poster pages. The two historical files in `PaperWithAwards/` were independently verified as ICLR 2026 Test of Time winners, not ICLR 2016 Best Papers. Directory names alone are not evidence of acceptance or an award.
- Paper-evidence boundary: external papers teach venue fit and presentation patterns only. Their datasets, metrics, results, or claims must never be transferred to the paper being written.
- Flow-KTO evidence boundary: the user supplied a BOT154/BOT159 real-robot comparison and a qualitative observation of clear whole-robot action improvement. This is user-authoritative deployment evidence, but metric definitions, baseline-row mapping, raw event counts, run comparability, repeated windows, variance, and statistical significance remain unverified. It may support venue-fit analysis, not a publication-ready efficacy claim.

### Evidence classes

| Class | Meaning | Permitted use |
|---|---|---|
| Official rule | Direct statement in an ICLR or RSS CFP, author/reviewer instructions, dates page, or official template | Submission compliance for the named venue and year only |
| Official program record | ICLR/RSS program page or OpenReview venue/forum linked by the conference | Confirm venue inclusion and presentation record |
| Local final-paper observation | A local PDF whose header says “Published as a conference paper at ICLR …” | Structural and rhetorical learning, not a universal rule |
| Local draft/preprint observation | A local PDF marked “Under review” or “Pre-print” | Weak comparative evidence only; not accepted-paper evidence |
| Analyst inference | A repeated pattern inferred from examples | Writing recommendation, never a desk-reject rule |

### Official source log

All URLs below were accessed on **2026-07-14**.

| ID | Official URL | Evidence obtained | Boundary |
|---|---|---|---|
| O1 | https://iclr.cc/Conferences/2026/CallForPapers | Scope, subject areas, double-blind process, OpenReview use, oral/poster program | ICLR 2026 only |
| O2 | https://iclr.cc/Conferences/2026/AuthorGuide | Deadlines, anonymity, page limits, supplement/code policy, ethics/reproducibility statements, reciprocal reviewing, dual submission, LLM use, discussion revisions, camera-ready notes | ICLR 2026 only; the page contains minor wording/date inconsistencies, so specific rules are cross-checked with O4/O6 where possible |
| O3 | https://iclr.cc/Conferences/2026/ReviewerGuide | Review purpose, evaluation questions, clarity/correctness/rigor/reproducibility/novelty considerations, reviewer FAQ | ICLR 2026 only; the private OpenReview review-form schema was not publicly accessible, so no numerical scoring rubric is invented here |
| O4 | https://iclr.cc/Conferences/2026/Dates | Abstract and paper submission dates, discussion and decision milestones | ICLR 2026 only |
| O5 | https://iclr.cc/Conferences/FutureMeetings | ICLR 2027 location region only | Does not publish ICLR 2027 submission rules |
| O6 | https://github.com/ICLR/Master-Template/raw/master/iclr2026.zip | Official 2026 LaTeX package and formatting instructions | ICLR 2026 only; do not reuse as the final ICLR 2027 template |
| O7 | https://iclr.cc/virtual/2026/papers.html | Official ICLR 2026 paper list; matches all three local `Normal/` titles | Confirms program inclusion, not award status |
| O8 | https://iclr.cc/virtual/2026/poster/10008998 | Official poster page for TROLL; links to OpenReview forum `X9D5MVpPJ9` | Confirms ICLR 2026 poster record |
| O9 | https://iclr.cc/virtual/2026/poster/10009149 | Official poster page for DiffusionNFT; links to OpenReview forum `VJZ477R89F` | Confirms ICLR 2026 poster record |
| O10 | https://openreview.net/group?id=ICLR.cc/2026/Conference | Official ICLR 2026 OpenReview venue | Confirms submission/review host; public API access to individual notes was challenge-gated during this check |
| O11 | https://proceedings.iclr.cc/paper_files/paper/2026 | Standalone official ICLR 2026 proceedings endpoint | The page displayed `0 papers` on the access date; this is a publication-lag/data-state observation, not evidence that ICLR 2026 had no accepted papers. The root `https://proceedings.iclr.cc/` did list a 2026 entry |
| O12 | https://iclr.cc/public/CodeOfEthics | ICLR Code of Ethics referenced by the Author and Reviewer Guides | General ICLR ethics source; year-specific submission handling still follows the applicable guide |
| O13 | https://iclr.cc/Conferences/2027/CallForPapers | Returned HTTP 404 on the access date | Supports only the narrow statement that this conventional endpoint was not published/accessibly populated; it does not establish future rules |
| O14 | https://roboticsconference.org/ | Official RSS entry; identified the active site as RSS 2026, July 13-17, 2026, Sydney | Does not publish RSS 2027 submission rules |
| O15 | https://roboticsconference.org/information/cfp/ | RSS 2026 CFP and author/submission instructions: dates, format, page limit, double blind, supplement/video, rebuttal, multiple submissions, AI text, and OpenReview workflow | RSS 2026 only; the page explicitly notes that page-limit policy may continue to change |
| O16 | https://docs.google.com/document/d/1iinlZAhQ4_DrYyLZAQRG4FE5vYTnoJR_EvgjcpQmcig/edit?usp=sharing | “RSS 2026 Review Guidelines,” linked directly by O15; constructive/specific review expectations, substantiation of novelty and experimental limitations, LLM-review responsibility, hallucinated-reference handling | RSS 2026 reviewer guidance; it does not provide a public numerical scoring rubric |
| O17 | https://roboticsconference.org/program/papers/ | Official RSS 2026 Accepted Papers list; matches the selected Generalizing from References and DexImit titles | Confirms RSS 2026 acceptance, not award status or a universal paper recipe |
| O18 | https://roboticsconference.org/2027/ and https://roboticsconference.org/2027/information/cfp/ | Both returned HTTP 404 on the access date | Supports only that these probed 2027 endpoints were not populated/accessibly published |
| O19 | https://roboticsconference.org/docs/paper-template-latex.tar.gz | LaTeX template linked by the active RSS 2026 CFP; archive contains `IEEEtran.cls`, `paper_template.tex`, `paper_template.pdf`, and `references.bib` | Current RSS 2026 package only; not an RSS 2027 template |
| O20 | https://iclr.cc/virtual/2026/poster/10008638 | Official poster page for *Compositional Diffusion with Guided Search for Long-Horizon Planning*; links to OpenReview forum `b8avf4F2hn` | Confirms ICLR 2026 poster status; the supplied local PDF remains a preprint version |
| O21 | https://blog.iclr.cc/2026/04/22/announcing-the-test-of-time-awards-from-iclr-2016/ | Official ICLR announcement naming DCGAN and DDPG as the 2026 Test of Time Award recipients | Confirms retrospective award status; it does not make either paper an ICLR 2016 Best Paper |
| O22 | https://iclr.cc/virtual/2023/poster/11309 | Official ICLR page for *Flow Matching for Generative Modeling*, marked top 25% and linked to OpenReview `PqvMRDCJT9t` | Supplemental target-scene exemplar, not user-paper evidence |

## Venue Requirements

### Latest verified cycle: ICLR 2026

| Dimension | Verified requirement or policy | Practical implication |
|---|---|---|
| Scope | ICLR invites work from all areas of machine learning. The 2026 CFP explicitly includes reinforcement learning, generative models, optimization, datasets/benchmarks, and applications to robotics, autonomy, and planning [O1]. | Frame the contribution as new, relevant ML knowledge and identify the ICLR community that benefits from it. Application evidence should validate that knowledge rather than substitute for a contribution. |
| Submission system | Abstracts and papers were submitted through the ICLR 2026 OpenReview venue [O2, O10]. | Every author needs a current OpenReview profile before the applicable deadline. |
| Abstract deadline | A genuine, informative abstract was due **2025-09-19, 11:59 pm AOE**. Placeholder or duplicate abstracts were removed; abstracts were used for reviewer bidding [O2, O4]. | The abstract must already state the real problem, method, and intended evidence. Do not plan to register a placeholder. |
| Full-paper deadline | The full paper was due **2025-09-24, 11:59 pm AOE**; supplementary material was due at the same time [O2, O4]. | Treat the main paper and supplement as one deadline-bound package. |
| Author changes | No new author could be added after the abstract deadline. Author order could be changed up to the full-paper deadline. After full-paper submission, the author set could not change; the FAQ separately allowed order changes during rebuttal and camera ready [O2]. | Finalize the genuine author set before abstract registration and verify every profile/email association. Treat later order changes as exceptional and communicate them according to the applicable guide. |
| Double blind | Main text and supplementary material had to be anonymous. Revealing author identity in either could cause desk rejection. Related arXiv papers by the authors did not by themselves break anonymity, but had to be cited in the third person [O1, O2]. | Audit names, affiliations, acknowledgments, self-referential phrasing, project/repository ownership, PDF metadata, images, and supplemental files. |
| Initial page limit | Initial-submission **main text: 9 pages or fewer**. The limit was strictly enforced; overlength main text could be desk rejected [O2, O6]. | Put the complete contribution and decisive evidence inside nine pages when using the 2026 baseline. |
| Discussion/camera-ready limit | The guide and template state **10 pages** for discussion/rebuttal and camera ready [O2, O6]. | The extra page is for response-driven clarification/new results, not a reason to omit a necessary initial-submission result. |
| References | The reference list did not count toward the page limit; unlimited bibliography pages were allowed [O2]. | Cite complete relevant work rather than compressing away necessary positioning. |
| Appendix | Unlimited appendix pages were allowed after the bibliography, but reviewers were not required to read them [O2]. The FAQ allowed appendices in the main PDF after references or as a separate supplementary file. | Proofs, full hyperparameters, and extended results can move to the appendix, but no central claim may depend solely on it. |
| Supplementary text | ICLR encouraged one file containing paper plus clearly marked supplementary text after the references [O2]. | Use a navigable appendix with explicit links from claims in the main text. |
| Code | Source code could be uploaded as supplementary material. ICLR encouraged code because it helps reviewers assess replicability, but reviewers were not required to inspect it [O2]. | Code release was encouraged, **not mandatory**. Code cannot replace method specification or main-paper evidence. |
| Anonymous code/demo | The FAQ allowed an anonymized zip, an anonymous repository, or a restricted OpenReview comment during discussion. Demonstration links had to be anonymous, and hosts must not track visitors in a way that could reveal reviewers [O2]. | Remove identity-bearing history, organization names, telemetry, analytics, account links, and hidden metadata before submission. |
| Ethics statement | All authors had to read, follow, and acknowledge the Code of Ethics. An Ethics Statement was recommended when the work raised relevant concerns; it was placed before references, excluded from the main-text page limit, and capped at one page [O2, O12]. | Address concrete risks when present; do not add a generic statement that avoids the actual issue. |
| Reproducibility statement | A paragraph-long Reproducibility Statement before references was strongly encouraged. It should point to the paper, appendix, and supplement material needed for reproduction. The guide excluded it from the main-text page limit [O2]. | Map every major claim to algorithms, assumptions, data processing, hyperparameters, proof, or code needed to reproduce it. |
| LLM use | General-purpose LLM assistance was allowed. If LLMs played a significant role in research ideation or writing to the extent they could be regarded as a contributor, authors had to disclose the precise role in a separate section; nondisclosure could lead to desk rejection. Authors remained fully responsible, and LLMs were not eligible for authorship [O2]. | Maintain an accurate usage log for this workflow. At submission time, apply the target-cycle threshold and disclose precisely; never claim “no LLM use” if that is false. |
| Dual submission | Identical or substantially similar work already published, accepted, or submitted in parallel to another conference/journal was prohibited. Non-peer-reviewed sites such as arXiv and workshops without proceedings were allowed; arXiv posting during review was allowed for 2026 [O2]. | Check all related submissions and versions. Cite the authors' own relevant preprints in third person under double blind. |
| Reciprocal reviewing | For 2026, authors on three or more submissions had to review at least six papers, subject to stated organizer exemptions. Each submission also needed at least one qualified author registered to review at least three papers, unless none of the authors met the guide's qualification definition [O2]. | Treat reviewer registration as a submission-critical administrative task, while rechecking the exact next-cycle rule. |
| Review/discussion | Reviews were anonymous and publicly visible on OpenReview. Authors could respond and revise during the public discussion period; reviewers/ACs could ignore revisions substantially different from the original [O2]. | Submit a complete paper. Rebuttal is for focused clarification and bounded evidence, not a replacement method or missing experimental program. |
| Withdrawal | After the full-paper deadline, a withdrawn submission remained publicly hosted and was de-anonymized immediately under the 2026 policy [O2]. | Do not treat OpenReview submission as a disposable private upload. |

### Official template constraints verified from `iclr2026.zip`

- Use the official, current-year LaTeX style. The 2026 template says submissions **must** use LaTeX with `iclr2026_conference.sty` and `iclr2026_conference.bst`; modifying style parameters may be grounds for rejection [O6].
- Keep `\iclrfinalcopy` commented out for double-blind submission. The style then prints anonymous authors and an “Under review” header; uncomment it only for camera ready [O6].
- The template specifies US Letter paper, a 5.5 by 9 inch text block, 10-point type with 11-point leading, Times New Roman preferred, and numbered pages [O6].
- The abstract is a single paragraph. The template controls its indentation, heading, and typography [O6].
- The style automatically adds line numbers for review; the paper must not refer to those line numbers because they disappear from the final version [O6].
- The template uses `natbib` author-year citations (`\citet`/`\citep`) and an alphabetically ordered reference section. Reference formatting must be consistent [O6].
- Figures and tables must be legible. Figure captions follow figures; table titles precede tables. Color is allowed, but the text and captions should remain intelligible when printed in black and white [O6].
- These details describe **the 2026 package only**. Download and inspect the actual package for the target year rather than renaming or modifying the 2026 style.

### Proceedings and accepted-paper access

- ICLR 2026 used OpenReview to host papers and reviews [O1, O10].
- The official ICLR 2026 virtual paper list is populated and provides individual program pages [O7]. It independently confirms that TROLL, DiffusionNFT, and *Compositional Diffusion with Guided Search for Long-Horizon Planning* were ICLR 2026 posters [O8, O9, O20].
- The separate `proceedings.iclr.cc` landing page exposes a 2026 link, but that year page reported `0 papers` on 2026-07-14 [O11]. Therefore, use the official virtual program and OpenReview for current accepted-paper verification, and recheck the standalone proceedings site before citing it as a complete 2026 archive.

### Next-cycle items that remain to be confirmed

Because no ICLR 2027 submission rules were verified, the following must be rechecked from the target-year official pages: abstract/full-paper dates and time zone; author/profile rules; initial, discussion, and camera-ready page limits; what is excluded from the limit; anonymity and self-citation; preprint and dual-submission policy; supplement formats/deadline/size; code/demo links; ethics and reproducibility statements; LLM disclosure; reciprocal reviewing; discussion/revision mechanics; withdrawal/publication behavior; official style archive and checksum; proceedings destination.

## RSS 2027 Venue Requirements

### 2027 官方可核验状态

- 截至 **2026-07-14**，RSS 官方入口 [O14] 仍是 RSS 2026 网站；页面没有 RSS 2027 CFP、日期、模板或 submission policy。
- 本次探测的 `https://roboticsconference.org/2027/` 与 `/2027/information/cfp/` 均返回 HTTP 404 [O18]。这只证明这些路径当前未发布/不可访问，不能据此推断未来规则。
- 因此，**RSS 2027 的页数、匿名、视频、补充材料、rebuttal、OpenReview 可见性、preprint、双投和 AI 文本政策均为 `UNVERIFIED`**。下列数值和流程只属于 RSS 2026。
- RSS 官网没有提供一个可核验的 RSS 2027 Author Guide 或 Reviewer Guide。当前最新的作者信息集中在 RSS 2026 CFP [O15]；当前 reviewer 信息是该 CFP 直接链接的 “RSS 2026 Review Guidelines” [O16]。

### 最新完整官方基线：RSS 2026

| 维度 | RSS 2026 可核验内容 | 对 Flow-KTO 的实际约束 | 2027 状态 |
|---|---|---|---|
| 征稿范围 | RSS 2026 欢迎报告 **novel scientific and systems contributions** 的 Science/Systems papers，并采用 double-blind review [O15] | 论文不能只有通用 learning objective；需要说明 unary feedback/flow policy 解决了哪个机器人科学或系统瓶颈 | `UNVERIFIED` |
| 关键日期 | Title/abstract：2026-01-23；paper：2026-01-30；supplement：2026-02-06；reviews/rebuttal invitations：2026-03-20；rebuttal：2026-03-27；decision：2026-04-27；camera ready：2026-05-11；均为 11:59pm AoE [O15] | 这些日期不得用于 RSS 2027 计划；只显示 2026 的先后关系与 supplement 比主文晚一周 | `UNVERIFIED` |
| 正文页数 | 主文最多 **8 页，参考文献除外**；官方强调上限不是目标，并偏好不冗长的稿件 [O15] | 按 8 页规划一个自包含核心是保守工程选择，不是 RSS 2027 定案 | `UNVERIFIED` |
| 自包含性 | 主 PDF 必须简洁、清楚地说明贡献、prior work、关键技术，并包含让专家核验中心 claims 所需的材料；reviewer 可自行决定是否看 supplement [O15] | score 定义、margin update、最关键对照、BOT evidence 边界和主要消融不能只放附件 | `UNVERIFIED` |
| 模板/PDF | 2026 CFP 链接 LaTeX/Word 模板；不得修改字号、页面尺寸、行距，不得加 “Draft”/“To appear” 或页码；主文件只接收 PDF；字体须嵌入并满足页面说明 [O15, O19] | 2027 模板发布前不制作“最终 RSS 2027 版”；发布后重新下载并校验，而不是重命名 2026 文件 | `UNVERIFIED` |
| Double blind | 姓名、单位不得出现在标题或正文；不得出现致谢；自引在措辞上不得区别于他引；PDF/上传元数据须匿名 [O15] | 真实机器人现场、版本名、机构/站点、图片 logo、dashboard、文件元数据都需要逐项匿名审计 | `UNVERIFIED` |
| 外部链接 | 2026 blinded submission 不得包含 YouTube、GitHub、机构页等外部链接；官方甚至建议避免匿名链接。外部资源可在 camera ready 中加入 [O15] | RSS 初稿分支应默认移除 URL、QR code 和项目页；不能照搬 ICLR 匿名代码链接实践 | `UNVERIFIED` |
| 实验图匿名 | 官方要求避免图片中的 logo 或对特定实验室的明显指认，但仍鼓励正常使用照片和图示 [O15] | BOT154/BOT159 图像若使用，需裁除可识别场地、品牌、账号、人员和设备标签；站点实名不应出现在 blinded 稿 | `UNVERIFIED` |
| 视频/补充材料 | 可上传 video、expanded proof 等；2026 supplement 截止在 paper 后一周；最大 100MB、zip；reviewer 不强制查看；初稿与修订稿须移除外链 [O15] | 视频可让动作改善可视化，但不能成为唯一证据；静态任务定义、协议和数字仍必须在主文 | `UNVERIFIED` |
| Rebuttal | 只有一部分论文获邀提交 **一页 rebuttal** [O15] | 不得把 raw counts、baseline fairness、关键硬件试验或核心推导计划为 rebuttal 补交项 | `UNVERIFIED` |
| OpenReview 可见性 | RSS 2026 使用 OpenReview，但 review 是 private；论文接收后才公开，review 不公开 [O15] | 首稿必须一次性可判断，不能依赖 ICLR 式公开讨论形成论证 | `UNVERIFIED` |
| Demo | 2026 没有单独 demo paper 类别；接收判断不考虑会议现场 demo 的可能性 [O15] | 实机系统本身不是接收理由，仍需科学问题、方法与可核验结果 | `UNVERIFIED` |
| 双投 | 已发表、已接收或与其他会议并行投稿的 identical/substantially similar 稿件不合规；CFP 明确把 ICLR 列为禁止并行投稿示例 [O15] | 同一实质 Flow-KTO 稿件不能同时投 ICLR 与 RSS；不能等待一个结果后再撤另一个 | `UNVERIFIED` |
| Preprint | 2026 允许 technical report/arXiv，但公开或宣传 preprint 可能使 reviewer 实际获知作者身份 [O15] | 2027 政策发布前不推断 preprint 时机；需在合规与实际匿名风险之间单独决策 | `UNVERIFIED` |
| AI 文本 | RSS 2026 没有 formal AI-generated-text policy，但作者对 plagiarism、ethics、citation、results 和 reproducibility 完全负责 [O15] | PaperSpine/LLM 生成内容必须逐句核验；2027 若新增披露要求，以新规为准 | `UNVERIFIED` |
| OpenReview 账户 | 2026 要求 first author 有 OpenReview account；非机构邮箱新 profile 的 moderation 可能耗时两周；作者需更新 conflict domains [O15] | 这是可能导致流程失败的前置事项，但不得直接沿用为 RSS 2027 要求 | `UNVERIFIED` |

### RSS 2027 发布后必须重查

至少重新核验：CFP 分类与 scope；title/abstract/full-paper 截止时间；页数与 references/ethics/appendix 计页方式；官方 LaTeX/Word 包；匿名、自引、外链、图片和 PDF metadata；视频/zip 格式、大小与截止日；reviewer 是否必须查看 supplement；rebuttal 邀请范围和页数；OpenReview 公开/私有；preprint、parallel submission、withdrawal；AI/LLM；paper ID、字体和 camera-ready 规范。任何 2027 新规都覆盖本节的 2026 基线。

## Review Criteria

### Official ICLR 2026 reviewer questions

The Reviewer Guide summarizes the goal of review as deciding whether a submission brings sufficient value to the community and contributes new knowledge [O3]. It asks reviewers to resolve four core questions:

1. What specific question or problem does the paper tackle?
2. Is the approach well motivated and properly placed in the literature?
3. Does the paper support its claims, including theoretical or empirical correctness and scientific rigor?
4. What is the significance of the work? Does it contribute new, relevant, impactful knowledge and sufficient value to the community?

The same guide asks reviewers to consider whether the submission is clear, technically correct, experimentally rigorous, reproducible, and presents novel findings [O3]. It explicitly says that lack of state-of-the-art results is not by itself a reason for rejection; a paper can contribute valuable empirical, theoretical, or practitioner knowledge without a SOTA number [O3].

No public numerical rating scale is reproduced here. The general review invitation was not guest-accessible during verification, and the Reviewer Guide is the auditable source for the criteria above.

### What those criteria require from a manuscript

| Criterion | Reviewer-facing question | Evidence that should be visible in the main paper |
|---|---|---|
| Problem specificity | Is there a real, precisely bounded problem rather than a generic performance gap? | Formal setting, available information, failure mode, affected use cases, and claim boundary |
| Motivation and positioning | Why does the problem remain unresolved, and why is this approach appropriate? | Direct comparison with the closest mechanisms; no strawman baseline; explicit difference from contemporaneous work |
| Novel knowledge | What is learned that was not already known? | One controlling contribution, its components or properties, and the general lesson beyond a benchmark implementation |
| Correctness | Are equations, algorithms, proofs, and implementation mutually consistent? | Defined notation and assumptions; proof or empirical checks matched to the stated claim; no hidden unavailable quantity |
| Experimental rigor | Do experiments isolate and test the claims? | Fair budgets, appropriate baselines, ablations tied to mechanisms, uncertainty/repeated trials, robustness and failure cases |
| Reproducibility | Could a knowledgeable reader reconstruct the result? | Data/split provenance, preprocessing, model/training details, evaluation protocol, compute, seeds, hyperparameters, and supplement map |
| Significance/value | Why should the ICLR community care? | Evidence of relevance, impact, breadth, efficiency, insight, or a useful negative result; SOTA alone is neither necessary nor sufficient |
| Clarity | Can the contribution and evidence be assessed without reconstructing the paper? | Abstract and introduction agree with results; figures answer questions; every major claim points to evidence |
| Ethics/integrity | Are risks, data practices, conflicts, and research integrity handled? | Targeted Ethics Statement when relevant; honest limitations; no fabricated citations, data, or claims |

### Review-process nuances relevant to paper design

- Reviewers may ask for additional experiments, but the guide says these should be limited in scope and validate existing results rather than significantly change the submission [O3]. The initial experimental design must therefore close the central claim.
- Reviewers are not required to read supplementary material [O2, O3]. Main-paper correctness cannot depend on an appendix-only definition, baseline, or decisive result.
- Work published within two months before the full-paper deadline was treated as contemporaneous in the 2026 Reviewer Guide FAQ; authors were not required to compare against such peer-reviewed work. Papers solely on arXiv were not treated as peer-reviewed, though citation was encouraged when known [O3]. This is a 2026 reviewer instruction and must be rechecked for the target cycle.
- Reviewers are instructed to remain open to relevant, impactful knowledge that does not set a new SOTA [O3]. The manuscript should make the knowledge contribution explicit rather than apologizing for a non-SOTA result.

## RSS Review Criteria

### 官方可核验的评审关注点

RSS 2026 CFP 与其直接链接的 reviewer guide 没有公布一个可直接复述的数值评分 rubric；本 dossier 因而不虚构“RSS 官方若干分项分数”。可以直接核验的判断基础是：

1. CFP 要求 Science/Systems paper 报告 **novel scientific and systems contributions** [O15]。
2. 主 PDF 必须自包含，使专家能够核验 central claims；supplement 由 reviewer 自主决定是否查看 [O15]。
3. Reviewer Guidelines 要求对“缺乏新颖性”的判断给出具体相关论文，而不能只下结论；对实验不足、效率、清晰度或适用性问题要指出具体缺失条件 [O16]。
4. 当 reviewer 认为 advance 不够重要/有意义时，guide 要求解释原因，以及未来需要看到什么才能改变判断 [O16]。
5. Reviewer 必须对其 review 内容负责；发现 hallucinated references 时，应根据它们对中心论证的实际破坏程度作判断 [O16]。

其中第 3-5 项是 reviewer 行为规范，不应被误写为新的形式审稿分数；但它们意味着稿件的 novelty、evidence gap 与 limitations 必须写得足够具体，能够接受逐项核查。

### Flow-KTO 在 RSS 场景下必须回答的问题

| RSS reviewer-facing 维度 | Flow-KTO 的关键问题 | 主文所需证据 |
|---|---|---|
| 机器人科学/系统问题 | “每个 observation 只有一条带 unary quality label 的真实机器人离线轨迹”造成了什么具体瓶颈？ | 数据单位、可用/不可用信息、采集/标注成本、现有做法的失效机制、claim boundary |
| 科学新颖性 | policy-centered CFM improvement score 是否形成新原理，还是把 KTO/质量加权迁移到 flow policy？ | 与最近机制的数学对照；score 所代表的量、假设和可检验性质；不以名称或 A+B 代替差异 |
| 系统新颖性 | margin calibration/adaptation 是否解除真实机器人任务间尺度与部署调参问题？ | 固定 margin、无校准、无 adaptation 等隔离消融；跨任务/标签尺度的实际行为，不只训练 loss |
| Claim support | Offline surrogate 的改善是否转化为 closed-loop whole-robot behavior？ | 同机器人/同工作负载/同控制栈的对照；明确定义的 success/efficiency/safety 指标；raw counts 或可复算 denominator |
| 实验充分性 | 两个机器人、一次窗口是否足以支持一般化 claim？ | 重复窗口、更多任务/对象/初态或收紧 claim；报告 run duration、负载、版本、随机化/顺序与不确定性 |
| Baseline fairness | Flow-KTO 与 MIST 或其他 baseline 是否只改变 policy update？ | checkpoint/config/code/data 版本；其他 perception/controller/speed 设置；相同预算；借用与复现结果分开标注 |
| 适用性和效率 | 方法的实际收益、代价与 failure mode 是什么？ | throughput、double-grab/reflow 等明确定义指标；训练/部署 compute；代表性成功与失败；安全停止条件 |
| 可复现/完整性 | 专家不看视频或 supplement 时能否核验？ | 主文中的任务图、协议、核心数字、关键消融与限制；supplement 提供匿名视频、完整细节和扩展结果 |

**实机证据不是 RSS 的普遍形式要求。** RSS 接收理论、科学和系统类型的机器人工作；不能声称“RSS 必须有 hardware”。但 Flow-KTO 自身以真实机器人轨迹、robot policy 和 whole-robot behavior 为中心，因此若稿件要声称实际机器人改善，闭环实机证据是该 claim 的直接验证，而不是可由纯仿真替代的装饰。

## Accepted Paper Patterns

### Local exemplar inventory and status calibration

| Source | PDF status and pages | Official match | Appropriate use |
|---|---|---|---|
| REF002, *DiffusionNFT: Online Diffusion Reinforcement with Forward Process* | 22-page local PDF; header says “Published as a conference paper at ICLR 2026” | Matched on the official 2026 paper list and poster page [O7, O9] | Primary modern accepted-paper exemplar |
| REF003, *TROLL: Trust Regions Improve Reinforcement Learning for Large Language Models* | 40-page local PDF; header says “Published as a conference paper at ICLR 2026” | Matched on the official 2026 paper list and poster page [O7, O8] | Primary modern accepted-paper exemplar |
| REF005, *Continuous Control with Deep Reinforcement Learning* | 14-page local PDF; header says “Published as a conference paper at ICLR 2016” | Officially named an ICLR 2026 Test of Time winner [O21] | Historical final-paper and durable-contribution exemplar; not a current-format template |
| REF004, *Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks* | 16-page local PDF; retained header says “Under review as a conference paper at ICLR 2016” | Officially named an ICLR 2026 Test of Time winner [O21] | Historical argument/durability exemplar; local-version caveat retained |
| REF001, *Compositional Diffusion with Guided Search for Long-Horizon Planning* | 38-page local PDF marked “Pre-print” | Matched to the official ICLR 2026 poster page [O7, O20] | Modern accepted-paper exemplar; verify camera-ready wording before attributing a specific textual choice |

### Patterns supported by the three verified ICLR 2026 exemplars

1. **The first two pages close the contribution loop.** Both papers move from a dominant current practice, to a precise structural failure, to a replacement principle, to practical feasibility, to broad validation. TROLL ends its introduction with three explicit contribution units. DiffusionNFT states the forward-process question, its method, four practical benefits, and exact headline evidence before background.

2. **Abstracts carry problem, mechanism, and evidence.** TROLL names the weakness of clipping, the differentiable trust-region projection, the sparsification needed for scale, and the axes on which it improves. DiffusionNFT identifies likelihood/reverse-process restrictions, introduces forward-process negative-aware fine-tuning, and reports both efficiency and benchmark effects. Neither abstract is a generic topic summary.

3. **The contribution is a causal chain, not a bundle of modules.** TROLL connects principled KL constraints to a projection, sparsification, differentiability, and observed stability. DiffusionNFT connects positive/negative distributions to an improvement direction, a supervised-form objective, solver flexibility, and efficiency. Each implementation device answers a constraint created by the central principle.

4. **An opening figure compresses method and outcome.** Within its first two pages, TROLL places the projection intuition and performance curves together. DiffusionNFT's first figure foregrounds efficiency and multi-metric improvement, followed by a process-comparison diagram. The figure earns space by helping reviewers understand both “what changes” and “why it matters.”

5. **Related-work placement is flexible; argumentative function is not.** TROLL puts Related Work before the method and uses it to isolate the exact opening. DiffusionNFT places it after experiments and organizes alternatives by likelihood-free and likelihood-based mechanisms. A rigid section order is not the pattern; precise contrast with the nearest methods is.

6. **Experiments are organized by claims and coverage axes.** DiffusionNFT separates multi-reward performance, head-to-head efficiency, and design ablations. TROLL tests model families, sizes, datasets, advantage estimators, and then analyzes KL bounds, sparsity, batch size, entropy, response length, memory, and runtime. The main paper shows the decisive comparisons; appendices expand coverage.

7. **Mechanism and cost evidence matter alongside quality.** Both accepted examples quantify training efficiency or overhead and isolate core design choices. This makes the paper informative even beyond a single leaderboard number and directly supports claims such as “drop-in,” “efficient,” “stable,” or “solver-flexible.”

8. **The ten-page final main text remains self-contained.** Both 2026 PDFs complete conclusion-level claims by page 10, then use references and long appendices for proofs, derivations, implementation details, complete results, and examples. Their appendices strengthen auditability but do not introduce the paper's basic method or only evidence for the headline conclusion.

9. **Limitations are scoped, not performative.** TROLL names its evaluated model scale/architecture boundary and future modality extensions. It does not retract the demonstrated result. The local DiffusionNFT final copy gives a focused conclusion and discloses LLM writing assistance. A limitation should mark where evidence stops and why, rather than list generic future work.

10. **Camera-ready identity/code is not an anonymity precedent.** Both final PDFs expose authors and project/code links, as expected after acceptance. Those features cannot be copied into a double-blind initial submission without applying the Author Guide's anonymity rules.

### Weaker historical and preprint observations

- The ICLR 2016 continuous-control final PDF uses a durable structure: concrete gap, minimal algorithmic idea, broad task suite, controlled component removals, strong baseline interpretation, and a short limitation paragraph. It is useful as a clarity example but not evidence of 2026 policy or current evidentiary sufficiency.
- The local DCGAN file explicitly lists contributions, gives implementable architecture guidelines, describes data/training choices, and validates representations through several complementary probes. Because this copy is marked “Under review” and was not independently matched in this task, these are draft observations only.
- The local preprint version of *Compositional Diffusion with Guided Search for Long-Horizon Planning* uses a modern ten-page body with cross-domain validation, limitations, reproducibility, and LLM-use sections. The title is officially an ICLR 2026 poster, but any difference between this local preprint and the accepted version must be checked before attributing a specific textual choice to the camera-ready paper.

### Recommended ICLR argument architecture (inference, not a rule)

1. Abstract: setting, exact failure, contribution principle, implementation, strongest bounded evidence.
2. Introduction: community problem, closest approaches and failure mechanism, central question, method intuition, contributions, evidence map.
3. Background/problem formulation: only definitions needed to see why the gap exists.
4. Method: principle first, then algorithm; assumptions and computational implications stated where used.
5. Experiments: explicit questions mapped to headline effectiveness, fair comparison, mechanism ablations, robustness/generalization, and efficiency/cost.
6. Related work: compressed around the closest mechanisms, wherever it best clarifies novelty.
7. Conclusion and limitations: answer the opening question, restate evidence boundaries, avoid new claims.
8. Reproducibility/ethics/LLM disclosure and appendix: follow the target-year rules; make the appendix navigable from main-text claims.

## RSS Accepted Paper Patterns

### 两篇指定 RSS 样例与接收状态

| Source | 本地 PDF 观察 | 官方核验 | 合理用途 |
|---|---|---|---|
| REF006, *Generalizing from References using a Multi-Task Reference and Goal-Driven RL Framework* | 11 页 PDF；结构为 Introduction -> Methodology -> Evaluation -> Conclusion；首图为 humanoid parkour 硬件/任务场景 | RSS 2026 官方 Accepted Papers 页面列出完全相同题目 [O17] | 机器人学习、robustness/generalization、simulation-to-hardware 证据结构样例 |
| REF007, *DexImit: Learning Bimanual Dexterous Manipulation from Monocular Human Videos* | 12 页 PDF；结构为 Introduction -> Related Works -> Method -> Experiments -> Limitations -> Conclusion；首图为 dexterous manipulation 任务画廊 | RSS 2026 官方 Accepted Papers 页面列出完全相同题目 [O17] | 数据/系统 pipeline、长时程任务、zero-shot real-world validation 与 failure analysis 样例 |

只有这两篇 `/home/robotera/文档/RSS` PDF 用作本节场景样例。官方列表确认的是 RSS 2026 acceptance，不是 award，也不证明它们的每个结构选择都是 RSS 硬规则。

### REF006：Generalizing from References 的结构与证据模式

1. **第一屏呈现机器人能力而非抽象框图。** 标题、首图和摘要直接建立 humanoid walking/jumping/climbing 的物理任务，以及 reference tracking 与 task-driven RL 之间的实际矛盾。
2. **Related work 承担 gap decomposition。** 论文在 Introduction 中按 motion tracking、distillation、adversarial imitation 等路线解释各自约束，然后才提出“reference as behavioral prior rather than deployment-time constraint”的中心设计。
3. **方法以一个可解释 principle 统领组件。** shared policy、imitation/generalization tasks、curriculum 和 initialization 分别服务“自然动作 + goal-driven adaptability”，不是没有因果关系的模块清单。
4. **Evaluation 开头先列科学问题。** 论文明确问 robustness/generalization、alternative training paradigms、long-horizon composition、key components 和 method extensions，再按问题组织结果，而不是按数据集顺序堆表。
5. **物理证据分层。** 主文包含 simulation、beyond-nominal initializations、清楚的 success criterion、每任务千次 simulation trials、真实硬件行为、long-horizon skill composition 和跨 physics engine 的观察。
6. **指标覆盖任务与动作质量。** baseline comparison 同时讨论 task success、root orientation 和 joint position error，避免只用单一成功率掩盖动作不自然或不稳定。
7. **消融对应机制。** 去除 task curriculum、imitation 或 generalization 分别验证学习稳定性、动作结构与 OOD adaptability；每个 ablation 都能回到贡献逻辑。
8. **结论划定系统边界。** 论文说明当前 high-level composer 仍是规则系统，并把 learned composer/perception expansion 留作未来工作，而不是暗示已实现完全 autonomy。

### REF007：DexImit 的结构与证据模式

1. **首图先显示任务覆盖与真实对象交互。** tool use、long-horizon、fine-grained manipulation 让 reviewer 在读公式前理解系统的目标难度。
2. **贡献与四阶段 pipeline 一一对应。** Reconstruction -> Scheduling -> Action -> Augmentation；每一阶段都针对 monocular video-to-robot data 的可测障碍。
3. **Experiments 由 Q1-Q4 驱动。** data usability、relative data quality、complex-task ceiling、zero-shot real-world deployment 对应从上游数据到下游 policy 的完整验证链。
4. **先验证中间产物，再验证最终行为。** 论文不只报 real-robot success，还检查 trajectory reconstruction、不同 input-quality/task-difficulty 组合和 generated data 的 policy usability，便于定位性能来源。
5. **Baseline adaptation 写明。** 对原本不是 bimanual dexterous setting 的方法说明如何扩展；对无官方代码的方法说明重实现来源。这类披露是公平性证据的一部分。
6. **难度轴有实际含义。** 任务按 unimanual/bimanual、cooperative/independent、short/long horizon、tool-use/fine-grained 等物理属性展开，而不是只换对象名称。
7. **真实部署消融直接测试 design choice。** object scale、grasp/motion regeneration、point-cloud noise 等变体在真实任务中评估，使 augmentation claim 不只依赖 simulation。
8. **单列 Limitations 与 failure breakdown。** 模块误差传播、不可用数据和不支持 complex in-hand manipulation 被明确指出，避免把 pipeline success 泛化成所有 dexterous tasks。

### 两篇 RSS 接收样例的共同模式

- **机器人问题是第一叙事对象。** 方法的新颖性要能回到真实物理约束、数据约束或系统能力，而非只在 loss 形式上成立。
- **首图压缩“任务 + 系统 + 结果边界”。** 对 Flow-KTO，RSS 版首图应优先展示 unary-labeled offline trajectory、update mechanism 与真实机器人行为对照，而不是只有 loss 曲线。
- **正文按问题/claim 组织实验。** 每个实验块明确回答一个 reviewer question；主表、关键消融和代表性失败在正文闭环。
- **证据形成阶梯。** 输入/中间机制 -> policy behavior -> robustness/generalization -> hardware -> failure/limitation，而不是从一个 offline metric 直接跳到机器人系统结论。
- **多轴评测比单一平均分更可信。** task success、动作质量、效率、安全/错误类型、不同初态或难度共同解释系统价值与 trade-off。
- **视频增强而不替代主文。** 两篇 final PDF 有项目/视频链接，但 camera-ready 身份与链接不能作为 blinded submission 先例；2026 初稿规则仍要求去外链 [O15]。

### 推荐的 RSS 论证骨架（分析推断，不是官方格式）

1. Abstract/Introduction：真实机器人数据约束、现有路线为何失效、中心 principle、可核验实机证据及边界。
2. Related Work/Problem：用最接近机制界定新颖性；明确 unary feedback、single trajectory per observation、flow policy 可用量。
3. Method：policy-centered score 的来源、scale-calibrated margin update、算法与实际计算；不以 A+B 叙述贡献。
4. Evaluation Questions：end-to-end improvement、fair baselines、mechanism、robustness、efficiency/safety、failure。
5. Real-Robot Evidence：任务与指标定义、试验协议、raw counts/denominators、repeated windows、代表性视频/失败。
6. Limitations/Conclusion：区分已证明的 deployment observation、统计支持范围和未覆盖机器人/任务。

## ICLR vs RSS Comparison and Flow-KTO Fit

### 场景对照（规则行仅采用 2026 官方基线）

| 对比轴 | ICLR 场景 | RSS 场景 | Flow-KTO 写作决策 |
|---|---|---|---|
| 核心受众 | 学习表征、RL、generative model、optimization 等 ML community [O1] | robotics science and systems community [O15] | ICLR 先讲一般 learning principle；RSS 先讲真实机器人数据/部署瓶颈 |
| 首要贡献偏好 | 新的、相关且有影响力的 ML knowledge；SOTA 不是必要条件 [O3] | novel scientific and systems contribution，且 central claims 可由专家核验 [O15] | 同一方法应选择一个主叙事，不能只换模板/标题 |
| 方法证据 | 数学动机、correctness、机制、跨 model/task/regime 的一般性 | 设计与物理约束的匹配、闭环可靠性、实际 trade-off 和 failure | score 原理适合 ICLR；BOT 部署链适合 RSS；两者仍需互相支撑 |
| 实机证据 | 对机器人主题有价值，但不是普遍硬要求；可作为一个 validation domain | 也不是普遍形式要求；对声称 real-robot policy improvement 的稿件是直接 claim evidence | 当前 BOT154/BOT159 观察提高 RSS fit，但协议未闭环，不能独立支撑 broad claim |
| 第一图模式 | 已接收样例常压缩 method mechanism + headline result | 两篇指定样例都先呈现机器人/任务与系统能力 | 准备 venue-specific first figure，而不是用同一图强行服务两种叙事 |
| 2026 初稿正文 | 9 页，references 不计；appendix 可长但 reviewer 不必读 [O2] | 8 页，references 不计；主文自包含，扩展文本入 supplement [O15] | 在 2027 规则发布前按 8 页核心设计只是内部保守预算 |
| 匿名链接 | 2026 允许经匿名处理的 code/demo 方案，但需防 visitor tracking [O2] | 2026 blinded submission 禁止外链，且建议避免匿名链接 [O15] | RSS 分支默认无 URL/QR；ICLR 分支也须以 2027 新规为准 |
| Supplement/video | 与 paper 同截止；code encouraged，reviewer 可不看 [O2] | paper 后一周；video/proof 可上传，zip 100MB，reviewer 可不看 [O15] | 两版都必须在主文放决定性数字与定义；附件只增强审计和动态展示 |
| Review 交互 | 2026 public review/discussion，可有限修订 [O2] | 2026 private review；只有部分稿件获邀一页 rebuttal [O15] | 两者都不能依赖 rebuttal 补中心实验；RSS 首稿尤其需一次性自足 |
| 双投 | 禁止 identical/substantially similar parallel conference/journal submission [O2] | 同样禁止，并明确举例 ICLR [O15] | 同一实质 Flow-KTO 稿件不得同时投两会；先选 venue，再提交 |

### 已有 BOT154/BOT159 实机证据

冻结记录 `paper_rewriting_output/user_supplied_real_robot_evidence.md` 保存了用户直接提供的 deployment comparison。下表只复述已记录数字，不新增统计推断：

| Robot | Flow-KTO version | Baseline version | Flow-KTO duration / efficiency | Baseline duration / efficiency | 其他已报指标 |
|---|---|---|---|---|---|
| BOT154 | `Flow-KTO_new_release_0624` | `MIST_package_release_0622` | 60:00 / 887 per hour | 153:00 / 666 per hour | double-grab 4.2% vs 1.8%；reflow 9.4% vs 9.9% |
| BOT159 | `Flow-KTO_new_release_0624` | `MIST_package_release_0622` | 77:13 / 1116 per hour | 90:00 / 895 per hour | double-grab 1.6% vs 1.0%；reflow 5.2% vs 6.6% |

可直接计算且已经冻结的事实是：两台机器人上 efficiency 都是 **+221/hour**；相对差分别为 +33.2% 和 +24.7%。用户还确认 complete robot 的动作改善清晰、具有实际可见性。其证据等级是 **user-authoritative real-robot observation**，而不是统计显著性结论。

发表前必须保留以下边界：

- baseline 行在聊天表格中没有重复站点/机器人标识；当前按紧邻 robot block 映射，必须再次确认。
- `efficiency`、`double-grab rate`、`reflow rate` 的 numerator、denominator 和优劣方向尚未完整定义。Reflow 仅能写“数值更低”；double-grab 仅能写“数值更高”，不能预先标为改善或退化。
- 四个 run 的 duration 不同；hourly normalization 不能排除时段、货物/任务 mix、负载、operator、hardware、perception/controller 或其他 software changes。
- 当前是两台 robot-level comparison，表面上每版本/机器人一个窗口；没有 raw event counts、variance、confidence interval、significance test 或 repeated-window evidence。
- 用户的“动作改善明显”可作为 deployment observation 和视频/定性分析动机，但需要预定义 behavior rubric、blinded rating 或可复算运动指标才能升级为审稿可检验结论。

### Flow-KTO 的 RSS 适配优势

1. **问题天然属于机器人数据约束。** Single trajectory per observation + unary quality label 对应真实部署中难以获得 pairwise preference、counterfactual action 或大规模在线 rollout 的条件。
2. **已有真实系统信号。** BOT154/BOT159 均报告更高 hourly efficiency，且用户观察到 whole-robot action improvement；这比只有 simulation/offline loss 更接近 RSS systems contribution。
3. **flow policy 的 intractable action likelihood 提供科学障碍。** 如果 policy-centered CFM score 能从可用量推出并预测实际行为，就能把机器人系统现象提升为可迁移的 scientific insight。
4. **margin calibration 可连接跨任务部署。** 若真实标签尺度/任务分布变化的证据支持，adaptive update 可被解释为减少 hand tuning 和 instability，而不只是附加 trick。

### Flow-KTO 的 RSS 主要风险与闭环动作

| 风险 | 当前状态 | RSS-ready 闭环 |
|---|---|---|
| 贡献被视为 KTO + CFM + adaptive margin | 标题和组件名容易触发该判断 | 用问题 -> principle -> method 证明 score/update 的必要性；与最近 unary/preference/flow-policy 方法做数学与等预算实证对照 |
| 实机 protocol 不完整 | 指标定义、raw counts、run mapping、confounders 未核验 | 固化 metric spec；导出 raw logs；确认 checkpoint/config/robot/site mapping；记录唯一变化项 |
| 样本层级太少 | 两台机器人、有限窗口，无法估计 robot/window variance | 增加 repeated/interleaved windows；条件允许时增加机器人、任务/对象/负载；否则收紧到这两个 deployment cases |
| 指标存在 trade-off | efficiency 更高；reflow 数值更低；double-grab 数值更高，方向尚未定义 | 预先定义主/安全指标与优劣方向；报告 Pareto/trade-off，不只突出 efficiency |
| 动作改善只有用户定性观察 | 有直接现场价值，但不可复算 | 设计动作质量 rubric、blinded video evaluation 或 trajectory-level smoothness/safety metric；报告代表性失败 |
| Unary label cost/quality 未透明 | 论文动机已给出，真实标注协议未在本 dossier 核验 | 说明标签来源、尺度、错误/缺失处理、每条数据成本；测试 label noise/scale/imbalance |
| RSS 匿名泄露 | 真实 site、robot ID、版本名、画面可能识别作者/机构 | blinded 稿匿名化 site/IDs/version ownership、logo、dashboard、metadata；按 2027 新规决定哪些细节交 confidential supplement |
| 关键行为只在视频可见 | RSS 2026 reviewer 不必看 supplement | 主文放静态序列、protocol 和定量表；视频作为匿名补充，不作为唯一证据 |

### 主投选择门槛

- 若最终最强证据是一般化的 improvement-score 原理、性质和跨 flow architecture/task/label regime 的一致规律，**ICLR 叙事更自然**；机器人部署是 validation domain。
- 若最终最强证据是 unary feedback 在真实机器人上带来可重复、协议可审计的 closed-loop improvement，并覆盖关键 trade-off、扰动和 failure，**RSS 叙事更自然**；理论解释服务机器人科学结论。
- 当前 BOT154/BOT159 evidence 已使 RSS 成为真实候选，而不再是“没有实机证据的假设 venue”。但在 raw logs、metric definition、repeated windows 与 confounder control 完成前，不能写成 broad real-world superiority 或 statistical significance。
- **两种叙事不能转化为同一实质稿件的并行投稿策略。** ICLR 2026 与 RSS 2026 都禁止 identical/substantially similar parallel submission [O2, O15]；RSS 2026 还明确举例 ICLR。2027 规则发布后必须重查，但在此之前也不得规划“双投后择一撤稿”。

## Constraints for This Paper

The Scene Analyst context identifies the proposed Flow-KTO problem/method direction and user-supplied preliminary real-robot evidence, but it does not establish a confirmed contribution or publication-verified result set. The BOT154/BOT159 record is valid as user-authoritative deployment evidence while its definitions, raw logs, protocol, confounders, replication, and statistical support remain pending. The constraints below preserve that distinction rather than inventing additional data or upgrading observations into claims.

### Non-negotiable content constraints

1. **Contribution first.** State one controlling contribution: what new knowledge the paper adds, what precise gap makes it necessary, which evidence validates it, and where the claim stops. Do not equate a new name or combination of components with novelty.
2. **A genuine abstract.** The abstract must accurately represent the submitted paper because ICLR uses it for bidding. It must not promise experiments, theory, code, or generality that the evidence does not contain.
3. **Main-text closure.** The problem definition, essential method, closest comparisons, decisive results, and principal limitations must be assessable without opening the appendix or code.
4. **Claim-to-evidence mapping.** Every major claim must point to a main-text theorem, table, figure, or controlled analysis. Every Results subsection must validate a stated contribution promise rather than merely report a metric.
5. **Fair experimental comparisons.** Record data, model, optimization, tuning, compute, and evaluation budgets. Explain borrowed results versus local reproductions. Include repeated trials or another justified uncertainty treatment where stochasticity matters.
6. **Mechanism tests.** If the paper claims stability, efficiency, generality, robustness, scalability, or a principled property, include a measurement designed for that exact property. A headline score alone is insufficient.
7. **Honest boundaries.** Separate demonstrated facts, interpretation, and hypothesis. Report relevant failure cases and limitations. Do not generalize from one dataset/model/domain unless evidence supports that scope.
8. **Reproducibility by construction.** Preserve algorithms, assumptions, data provenance/splits, preprocessing, hyperparameters, evaluation protocols, compute, and seeds while drafting; do not try to reconstruct them only at camera-ready time.
9. **Citation integrity.** Use the target-year official citation setup, cite the closest work completely, and verify every bibliographic record. Under double blind, refer to the authors' own related work in the third person.
10. **No fabricated content.** Venue examples cannot supply this paper's data, metrics, p-values, comparisons, citations, or experimental outcomes.
11. **Fixed title.** The paper title is *Flow-KTO: Learning Flow-Based Robot Policies from Unary Feedback*.
12. **Problem-principle-method-validation narrative.** Define the contribution through the information constraint, improvement principle, implementable update, and validating evidence. Do not define novelty as “based on” prior work or an A+B combination, while still citing all relevant prior mechanisms honestly.
13. **Real-robot claim boundary.** BOT154/BOT159 may be described as two user-reported deployment comparisons. Until the protocol is verified, do not claim statistical significance, broad generalization, causal isolation, or unqualified real-world superiority.
14. **Venue-specific contribution test.** An ICLR version must make the general ML knowledge explicit; an RSS version must make the robotics science/system contribution and physical evidence explicit. Formatting alone cannot turn one contribution into the other.

### Submission and anonymity constraints

- The target years are already fixed as ICLR 2027 and RSS 2027, but neither target-year rule set was verified. Maintain a venue-neutral source and use an **eight-page core** only as a conservative internal budget derived from the tighter RSS 2026 baseline. Do not label 9 pages as an ICLR 2027 rule or 8 pages as an RSS 2027 rule.
- For an initial double-blind build, remove author names, affiliations, acknowledgments, funding text, identity-revealing self-reference, organization/repository ownership, logos, QR codes, PDF metadata, and supplemental-file metadata. Inspect anonymous links for analytics or access logs that can expose reviewers.
- Keep `\iclrfinalcopy` disabled in the applicable official template for submission. Enable it only for the accepted camera-ready version.
- Treat code as encouraged but not mandatory under the verified 2026 policy. If code is submitted for review, anonymize it and make the paper understandable without it.
- For the RSS branch, the verified 2026 baseline is stricter than ICLR on links: remove all external URLs from the blinded initial/revised paper, even anonymous project/video links, unless RSS 2027 explicitly changes that rule. An uploaded anonymous video/supplement still cannot replace main-text evidence.
- Maintain a truthful LLM-use record for research ideation, analysis, writing, translation, coding, and figure generation. Apply the target-year disclosure rule at submission; the use of PaperSpine/Codex must not be silently denied.
- Check substantial overlap, prior publication, accepted work, and parallel submissions before registration. The verified ICLR 2026 and RSS 2026 policies both prohibit identical/substantially similar parallel submissions; RSS explicitly names ICLR as an example. Select one primary venue before submitting the substantive Flow-KTO paper and recheck both 2027 policies.
- Verify all authors' OpenReview profiles, author set/order, and reciprocal-review obligations before the applicable deadlines.

### Internal page and evidence budget based on the 2026 baseline

This is an engineering recommendation for the confirmed ICLR 2027/RSS 2027 targets, not an official rule for either 2027 venue:

| Main-text unit | Required function |
|---|---|
| Abstract + Introduction | Complete problem-contribution-evidence loop; no deferred motivation |
| Problem/Background | Minimum formal context needed to distinguish the contribution from closest work |
| Method | Principle, algorithm, assumptions, complexity, and claim boundary |
| Experiments | Headline evidence, fair baselines, mechanism ablation, robustness/generalization as claimed, efficiency/cost as claimed |
| Related Work | Direct contrast with closest mechanisms; full references remain outside the page count under 2026 rules |
| Conclusion + Limitations | Answer the opening question and state exactly where evidence ends |
| Appendix/Supplement | Complete proofs, pseudocode, hyperparameters, extended tables/figures, additional examples; never the sole location of a central definition or result |

### Final target-cycle audit

Before producing a submission-ready PDF, re-open the official target-year CFP, Author Guide, Reviewer Guide, Dates page, template archive, OpenReview venue, and proceedings destination. Record the access date and verify page limits, deadlines, anonymity, author changes, supplement/code/demo handling, ethics/reproducibility/LLM sections, reciprocal reviewing, dual submission/preprints, revision/rebuttal, withdrawal, formatting, and citation style. Any difference from the 2026 baseline overrides this dossier.
