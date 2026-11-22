# AI transparency, open source, and deployment responsibility

**Legal snapshot: 2026-11-22.** This is an engineering learning note, not legal advice, an exhaustive jurisdictional survey, or a compliance certificate. Separate authentic enacted law, application dates, regulator guidance, proposals, and the facts of a particular deployment. A repository licence is not a jurisdiction or an actor role.

**AI-assistance disclosure:** This note was drafted and source-analysed with AI assistance; it has not undergone an independent human legal review. This disclosure is an editorial choice, not a claim that a particular jurisdiction requires it or that technical provenance/compliance has been established. No human-review exception is asserted.

## Why this deserves a separate note

Reliability, security and publication checks answer different questions from regulatory scope. Keep this topic separate from retry/recovery procedures and connect it to the [pattern index](PATTERN_INDEX.md), [agent-skill lifecycle](AGENT_SKILLS.md) and [publication gate](PUBLICATION_SECURITY_GATE.md).

The reusable insight is:

> Determine **actor → activity/intended use → output/audience → jurisdiction → applicable date → exception → evidence** before assigning an obligation. Neither an open-source badge nor an AI label can replace this analysis.

## 1. Open source is not a universal EU AI Act exemption

The relevant legislation is Regulation (EU)2024/1689, as amended by enacted Regulation (EU)2026/1744. The latter was published24 July 2026 and entered into force27 July 2026. Use the authentic acts together; the27 July 2026consolidation is a documentation aid, not an independently authoritative legal act. [EU1–EU3]

### Different objects have different exceptions

| Object / role | Relevant boundary | What must not be inferred |
|---|---|---|
| Documentation, a prompt recipe or a source component | First determine whether the object is itself an AI system/model and what the publisher actually supplies. A document alone does not establish a deployed inference system. Separately assess duties that may attach to publishing AI-generated public-interest text. | Every contributor to every AI-related repository is automatically a regulated provider. |
| An AI system released under a free/open-source licence | Article 2(12) contains an exclusion, **but not** where the system is placed on the market/put into service as high-risk or falls underArticle5or50. | An open-source chatbot, prohibited practice or high-risk service escapes relevant duties merely because its code is public. |
| A qualifying free/open-source general-purpose AI model | Article 53(2) exempts the specified53(1)(a)/(b)documentation duties when licence freedoms and public parameters/weights, architecture and usage information satisfy its conditions. The exception does not apply to systemic-risk GPAI models. | All ofArticle53or the whole Act disappears, or public weights alone establish a qualifying licence. |
| Copyright policy and training-content summary | Article 53(1)(c)/(d)remain distinct from the limited53(2)exception. A training-content summary is not a demand to redistribute an entire dataset. | Open-source release proves lawful training or removes all copyright-related duties. |
| A third-party FOSS component integrated into a high-risk system | Amended25(4)contains a specific exception to its written-assistance-agreement requirement for qualifying public FOSS tools/services/processes/components, **other than GPAI models**. | The finished high-risk product or its integrator inherits a general exemption. |
| Rebranding / materially changing a high-risk deployment | Article 25can make a distributor, importer, deployer or other third party the provider in its specified circumstances. | The upstream project alone carries all downstream responsibility. |

Recitals 102–104help explain the policy and conditions. Recital 103specifically discusses monetised components and notes that making components available in an open repository does not itself constitute monetisation. Do not convert that context into either “all commercial use is forbidden” or “every free download is non-commercial”. Licence freedom, monetisation, the object supplied and the applicable operative provision require separate assessment. [EU1, EU3]

### “Community” is not a single legal role

Separate an individual contributor, project maintainer, foundation, model publisher, hosting platform, own-brand service operator and enterprise customer. A foundation or nonprofit label is not the same thing as a natural person's purely personal use. A code repository and a public inference service are different activities, even when they share a project name.

A public repository with no licence is not automatically free/open-source. A restrictive open-weights licence should not be silently substituted for the freedoms and disclosure conditions inArticle53(2). Conversely, a genuine FOSS licence can permit commercial reuse: copyright permission and regulatory responsibility are separate questions.

## 2. Personal use and professional use are not the same boundary

Article 2(10)excludes the **deployer obligations** of natural persons using AI in a purely personal, non-professional activity. Article 3(4)also frames the deployer definition around this distinction. This is not an exemption for every activity performed by a human, and it does not erase the upstream provider's duties. [EU3]

| Illustrative activity | Scope question, not an automatic compliance verdict |
|---|---|
| Using an AI tool privately for a family task | The personal/non-professional deployer exclusion can be relevant. The tool provider still needs its own analysis; other privacy, fraud, copyright and content laws remain. |
| A freelancer using AI for client work or an economically regular content business | Being an individual rather than a corporation does not by itself make the activity personal. |
| An employee operating a company-controlled AI workflow | Identify the entity under whose authority the system is used; do not automatically treat each employee as an independent deployer. |
| An individual publishing an app/model or running a public AI service | Reassess provider, publication and distribution roles; a personal-use argument is not a blanket exemption for supplying a system. |
| A university or community R&D project | Articles 2(6)/(8)have specific scientific/pre-market research boundaries. Research naming, nonprofit status or public code is not proof that all conditions hold; real-world testing and other laws need separate treatment. |

Do not export this EU distinction as a global rule. Another jurisdiction may impose duties on a person who posts synthetic content to a platform, even when that person is not operating a business.

## 3. Four different transparency work products

1. **Interaction identity:** tell people that they are interacting with AI when the relevant rule is triggered. Reading a generated article is not automatically direct interaction with a system.
2. **Content disclosure and provenance:** distinguish a visible notice from a machine-readable marker, and identify whether the duty belongs to a system provider, publisher, platform or user. A visible disclaimer alone does not establish technical marking.
3. **Model/use documentation and oversight:** explain intended use, limitations, relevant output interpretation and competent intervention where the applicable regime requires them.
4. **Decision explanation and challenge:** explain the actual role/procedure/main decision elements in the legally relevant consequential-decision context. A SHAP chart, raw source code, polished narrative or human sign-off checkbox does not automatically satisfy it.

In the EU these relate to distinct provisions, includingArticles13/14,50and86, with GDPR duties on a separate basis. Article 86does not simply import GDPR22's solely-automated condition. Its transition interaction with deferred classification/legacy rules needs case-specific analysis; do not say that every explanation right was postponed together. [EU3]

Article 50generally applies from2 August 2026. Amended111(4)gives specified systems marketed before that date until2 December 2026for50(2)only. Amended113(c)defers specifiedChapterIIIsections1–3(except6(5))to2 December 2027forAnnexIII/6(2)and2 August 2028forAnnexI/6(1). GPAI models marketed before 2 August 2025 have a separate Article 111(3) transition to 2 August 2027. These are not one universal AI compliance deadline. Relevant Codes are aids, not a presumption of conformity:2026/1744recital41expressly rejects that presumption. [EU2–EU3]

## 4. Selected cross-jurisdiction snapshot

This section is a dated, selected comparison of official sources, not a global equivalence ranking. The final source-backed matrix follows below.

| Jurisdiction / instrument | Binding status and date | Selected actor/output requirements | Boundary that matters |
|---|---|---|---|
| **EU AI Act** | Enacted 2024 law, amended by enacted 2026/1744; application dates vary by provision. | Separate interaction notice, technical synthetic-content marking, specified publication disclosure, high-risk transparency and conditional decision explanation. | FOSS and personal-use exclusions are limited by object, role and activity; see sections 1–3, not a universal community exemption. |
| **US federal — TAKE IT DOWN** | Public Law 119-12, enacted 19 May 2025; covered-platform notice/removal process due 19 May 2026. | Specific nonconsensual intimate imagery/digital-forgery prohibitions; covered platforms must act on valid removal requests as soon as possible and within 48 hours. | Not a general AI-label or every-output explanation law. A private poster is not automatically a platform, but harmful publication can separately fall within the law. [US1] |
| **California — AI Transparency Act** | SB 942/AB 853, materially amended by **SB 1000, urgency statute effective 30 September 2026**. | Publicly accessible covered GenAI providers: image/video/audio provenance and verification duties, subject to exact scope/exceptions. SB 1000 removed the old million-user provider threshold and former manifest-disclosure-option requirement. | Do not copy the original SB 942 deadline/threshold. **Hosting and large-platform provisions start 1 January 2027**: specified model/source-download hosting duties can reach open-model distribution regardless of compensation; this is enacted, not yet operative at this snapshot. Not every repository/contributor is covered. [US2–US3] |
| **Utah — consumer disclosures** | Current §13-77-103 effective 7 May 2025; relevant definitions updated effective 6 May 2026. | Consumer-transaction suppliers disclose AI/not-human status upon the defined clear inquiry; defined high-risk interactions in regulated occupations require prominent advance disclosure. | Not every professional use or AI artifact carries the same proactive notice. A sole practitioner can occupy the regulated role. [US4–US5] |
| **China — 2025 synthetic-content labelling measures** | Binding normative measures, effective **1 September 2025**, operating with mandatory GB 45438-2025 and existing service rules. | Covered providers, dissemination platforms and app distributors have distinct visible/metadata duties. **Article 10 also requires users publishing generated/synthetic content through covered dissemination services to declare it and use supplied labelling functions.** | Do not import the EU personal/non-professional exclusion. Offline code/R&D is not the same as a public GenAI service or content publication. Controlled unlabelled export under Article 9 does not waive later publication declaration. Technical details of the full GB standard were not independently reviewed here. [CN1–CN3] |
| **India — final 2026 SGI amendments** | G.S.R. 120(E), notified 10 February 2026, effective **20 February 2026**; not the 2025 consultation draft. | Covered intermediary resources facilitating realistic synthetic audio/visual/audiovisual information: prominent labelling and technically feasible provenance requirements; significant social-media intermediaries have additional declaration/verification duties. | **Pure text alone is not SGI under this definition**; other rules still apply. Do not import a draft 10%-of-screen rule. Intermediary/user/content roles matter, not simply individual versus enterprise; the significant-platform threshold does not exempt every smaller intermediary. [IN1–IN3] |
| **Japan — AI promotion statute + business guidelines** | Act 53/2025 fully commenced **1 September 2025**. AI Guidelines for Business **v1.2, 31 March 2026**, are expressly non-binding soft law. | The statute includes government measures and a business-cooperation duty; the guidelines recommend contextual transparency, AI-use/limits information and explanations. | The statute is not wholly voluntary, but its reviewed text is not a general product/output labelling law. Non-business users fall outside the business guideline's intended audience; other laws are not waived. [JP1–JP3] |
| **South Korea — AI Basic Act / decree** | Act originally effective **22 January 2026**; current amended law and implementing decree inspected. | Article 31: advance notice for specified high-impact/GenAI products/services, GenAI-result marking, and heightened realistic synthetic-content disclosure. Ordinary GenAI marking may be human-perceivable **or** machine-readable with the decree's explanatory notice. Article 34 includes a high-impact explanation-plan requirement. | Article 31 targets defined AI business operators, not everyone who privately uses a chatbot. Decree 23 includes obvious-use and solely internal-work exceptions. **No statutory deferral to 2027 was verified**; possible enforcement grace policies and later notices were not established and must not be invented. [KR1–KR2] |
| **Taiwan — AI Basic Act** | Enacted, promulgated **14 January 2026**, in force at this snapshot; not the former draft. | Article 4 includes government-directed transparency/explainability principles; Article 5(2) contains a **designated high-risk product/system precautions/warnings** provision. Sectoral classification/rules matter. | Do not turn the framework into “every private output needs a badge”, or omit its narrower warning provision. Relevant sectoral designations were not verified. A two-year legislative-adaptation period is not postponement of the whole Act. [TW1–TW2] |

**What this comparison does not say:** The selected US federal/state examples are not a demonstrated single uniform EU-equivalent regime, but this was not an exhaustive Congress/50-state enactment or litigation search. Other privacy, employment, credit, safety, copyright, election and consumer-protection laws can independently matter in every jurisdiction. These instruments do not all create the same decision-explanation right.

**Open-source distribution needs particular care:** EU exclusions and limited GPAI exceptions are not the same as California's forthcoming defined hosting-platform duties. Nor does a Chinese posting obligation become irrelevant because a generator's source code was freely licensed. Assess the software/model release, hosted service and generated publication separately.


## 5. An applicability record, not a licence-based verdict

Before enabling a feature, shipping a model or publishing generated content, record:

- the artifact/service and intended use, rather than only the repository name;
- the actual actor role and who owns deployment/editorial responsibility;
- the market, audience and output location relevant to jurisdiction;
- the output class: interaction, synthetic media/text, intermediate data or consequential decision;
- the legal source, version, status and applicable date, including legacy conditions;
- the precise exclusion/exception and evidence for it, or the missing facts;
- which controls are required, recommended or not assessed;
- what was actually verified, by whom, and which interpretation still needs qualified review.

A failed scope gate is not permission to invent a legal obligation. Unknown applicability is not compliance. Absence of evidence is not proof that an unstated control was violated. Keep permission to calculate, ability to complete a bounded review, and readiness to publish or deploy as different decisions.

## 6. Engineering implications

### Preserve provenance through the real output path

If a duty actually applies, test its concrete surface: initial chat/voice interaction, export/download, image/video/audio conversion, publication and reposting. Check visible notice and machine-readable metadata separately. Do not promise universal C2PA use or assume that adding a watermark proves every jurisdiction's requirements. Keep versioned origin information and required markers through supported transformations; assess privacy before logging prompts or personal data.

### Maintain an evidence chain that can be contested

Separate:

- input/source lineage and reproducible transformations;
- model version, output, uncertainty and explanation fidelity;
- substantive human review, correction/override and final decision rationale.

A source can be faithfully quoted but wrong; a calculation can be reproducible while its entity match is false; an explanation can be persuasive but unfaithful. A label does not repair any of those defects.

### Keep legal and security claims bounded

An open-source licence, registry scan, schema test, Code signature, model self-report and runtime authorization trace answer different questions. None alone proves whole-law conformity, safe deployment or permission to disclose private data. A legal-readiness checklist does not grant tools, service access or a new disclosure audience.

## 7. Counterexamples for review

These are design questions, not executed tests or legal determinations:

- Does a documentation-only repository correctly distinguish not supplying an AI system from the separate publication of AI-generated public-interest text?
- Does a FOSS chatbot provider incorrectly skip interaction disclosure because the code is public?
- Does an own-brand HR application incorrectly inherit its upstream component's exception?
- Is a free download wrongly treated as proof that there is no provider activity?
- Is a private user incorrectly treated like a professional publisher—or an economic creator incorrectly treated as purely private?
- Is an EU personal-use exclusion incorrectly used to waive another country's posting/platform obligations?
- Does a disclosure rule for public-interest text get applied to every internal draft?
- Does the system confuse an applicable future deadline with a current violation?
- Does an apparently complete checklist hide missing role, date, jurisdiction or evidence?
- Does an “AI-generated” label obscure the absence of a faithful explanation or substantive review?

## Primary sources and status

- **EU1** — Regulation (EU)2024/1689, authentic original OJ; especiallyrecitals102–104: https://eur-lex.europa.eu/eli/reg/2024/1689/oj/eng
- **EU2** — Regulation (EU)2026/1744, authentic amending OJ,8 July 2026/published24 July/inforce27 July: https://eur-lex.europa.eu/eli/reg/2026/1744/oj/eng
- **EU3** — Consolidated documentation27 July 2026; especiallyArticles2(6)/(8)/(10)/(12),3,25(4),53(2),111,113: https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02024R1689-20260727

- **US1** — GPO, Public Law 119-12, sections 2–4: https://www.govinfo.gov/content/pkg/PLAW-119publ12/html/PLAW-119publ12.htm
- **US2** — California, SB 1000 chaptered, 2026 chapter 861 (30 September urgency amendment): https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB1000&search_keywords=
- **US3** — California current Business and Professions Code, division 8, chapter 25: https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=BPC&division=8.&title=&part=&chapter=25.&article=
- **US4** — Utah Code §13-77-103, current disclosure provision: https://le.utah.gov/xcode/Title13/Chapter 77/C13-77-S103_2025050720250507.html
- **US5** — Utah Code §13-77-101, definitions effective 6 May 2026: https://le.utah.gov/xcode/Title13/Chapter 77/C13-77-S101_2026050620260506.html
- **CN1** — CAC, 人工智能生成合成内容标识办法, especially articles 2–10 and 14: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm
- **CN2** — SAMR/SAC record, GB 45438-2025 (identifier/status/dates, not full technical-clause review): https://openstd.samr.gov.cn/bzgk/std/newGbInfo?hcno=F32EA2A561F1886CD8D606513512D547
- **CN3** — CAC official explanation, including export and subsequent publication: https://www.cac.gov.cn/2025-03/14/c_1743654685896173.htm
- **IN1** — MeitY official mirror of final G.S.R. 120(E), 10 February 2026, English pages 8–12: https://www.meity.gov.in/static/uploads/2026/02/f55fe52418b03f58b0669f6a8bc03b6d.pdf
- **IN2** — MeitY consolidated IT Rules, including February 2026 corrigenda: https://www.meity.gov.in/static/uploads/2026/03/0b576f2071694b52e4cd6bb1b6dfab1e.pdf
- **IN3** — MeitY explanatory FAQ dated 10 February 2026 (not legislation; storage-path date is not its effective date): https://www.meity.gov.in/static/uploads/2025/10/065b6deb585441b5ccdf8be42502a49c.pdf
- **JP1** — Japan e-Gov, Act No. 53 of 2025: https://laws.e-gov.go.jp/law/507AC0000000053
- **JP2** — Cabinet Office commencement information: https://www8.cao.go.jp/cstp/ai/ai_act/ai_act.html
- **JP3** — MIC/METI business guidelines v1.2, provisional English translation, 31 March 2026, especially printed pages 2–5 and 19–20; original-language text controls: https://www.soumu.go.jp/main_content/001080990.pdf
- **KR1** — Korean National Law Information Center, current AI Basic Act (law/supplements, especially articles 2, 31 and 34): https://www.law.go.kr/LSW/lsInfoR.do?lsiSeq=282791&efYd=20260721&chrClsCd=010202&nwJoYnInfo=Y
- **KR2** — Current implementing decree, especially article 23: https://www.law.go.kr/LSW/lsInfoR.do?lsiSeq=288781&efYd=20260820&chrClsCd=010202&nwJoYnInfo=Y
- **TW1** — Taiwan national law database, 人工智慧基本法, especially articles 4, 5, 16 and 18: https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=H0160093
- **TW2** — Official promulgation history: https://law.moj.gov.tw/LawClass/LawHistory.aspx?pcode=H0160093

Source-access limits: Direct California rendering returned an anti-bot challenge. Chaptered/current official text was read through a public text proxy; cache freshness is not independently certified, although the chaptered amendment and current-code wording were cross-checked. Some English versions are provisional translations. Korean MSIT enforcement-support notices and later exemption notices, Taiwanese sectoral designations, comprehensive subsequent-amendment/injunction sweeps and full Chinese technical-standard clauses were not verified. Treat these as explicit limits, not assumed exemptions.


## Limits and update discipline

This snapshot does not assess a named product, licence, model, person or deployment, and it is not an exhaustive check of all sector rules, court orders, amendments or enforcement. Recheck the controlling official source and current facts before a consequential decision. Documentation-only publication establishes neither instrumented compliance nor reliable legal reasoning by every model. Keep private operational, participant, research and customer evidence out of a public learning note.

[Publication audit](PUBLICATION_AUDIT_2026-11-22_AI_GOVERNANCE.md) records the bounded documentation checks, not legal certification.
