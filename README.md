<div align="center">

<img src="assets/banner.svg" alt="OB Paper Humanizer — De-AI your OB manuscripts" width="800">

<br/>

[\![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)
[\![Skill Type](https://img.shields.io/badge/Type-AI%20Skill-6366f1?style=for-the-badge)]()
[\![Compatibility](https://img.shields.io/badge/Works%20with-Claude%20%7C%20Codex%20%7C%20Gemini-059669?style=for-the-badge)]()
[\![Journals](https://img.shields.io/badge/Target-AMJ%20%7C%20ASQ%20%7C%20JAP%20%7C%20OBHDP-d97706?style=for-the-badge)]()

</div>

> [\!NOTE]
> **Writing an OB paper with AI assistance?** Your draft reads smooth — but reviewers can *tell*. This skill detects 17 categories of AI-detectable patterns in academic prose and transforms them into writing that sounds like a seasoned OB scholar.

---

## Highlights

| | Feature | Why it matters |
|---|---------|---------------|
| 🔍 | **17 AI Pattern Categories** | Catch hollow framing, transition monotony, hedging overload, and 14 more signals reviewers are trained to spot |
| 🎯 | **Journal-Calibrated Voice** | Tailored for AMJ, ASQ, Org Science, JAP, OBHDP, JOM, JOB, PP — each journal has a distinct voice |
| ✂️ | **Surgical Edits, Not Rewrites** | Preserves your argument, structure, and meaning — only removes the AI fingerprints |
| 🔬 | **Baseline-Tested** | Validated against 2020–2022 AMJ/JAP papers (pre-ChatGPT era) with three-way comparison |
| 🛡️ | **Academic Integrity Guard** | Never fabricates data, never misrepresents citations, never adds false precision |

## Quick Start

> ⏱️ **Get started in 30 seconds, no coding required**

### Method 1: Tell Your AI (Recommended)

Just send this message to your AI tool:

| Platform | Copy this and send to your AI |
|----------|-------------------------------|
| **Claude Code** | `Install ob-paper-humanizer from https://github.com/gtskevin/ob-paper-humanizer` |
| **OpenAI Codex** | `Install ob-paper-humanizer from https://github.com/gtskevin/ob-paper-humanizer` |
| **Gemini CLI** | `Install ob-paper-humanizer from https://github.com/gtskevin/ob-paper-humanizer` |
| **Cursor** | Download and place files in `.cursor/rules/` |
| **Windsurf** | Download and place files in `.windsurf/rules/` |
| **Other AI** | Place files in your AI's custom instructions directory |

> 💡 **Never used a terminal?** Open your AI tool (e.g. Claude Code), paste the command above, and the AI handles everything. Then just paste your manuscript section and say "humanize this."

### Method 2: Manual Install

<details>
<summary>Claude Code</summary>

```bash
mkdir -p ~/.claude/skills/ob-paper-humanizer
curl -sL https://raw.githubusercontent.com/gtskevin/ob-paper-humanizer/main/SKILL.md \
  -o ~/.claude/skills/ob-paper-humanizer/SKILL.md
```
</details>

<details>
<summary>OpenAI Codex</summary>

```bash
mkdir -p ~/.codex/skills/ob-paper-humanizer
curl -sL https://raw.githubusercontent.com/gtskevin/ob-paper-humanizer/main/SKILL.md \
  -o ~/.codex/skills/ob-paper-humanizer/SKILL.md
```
</details>

<details>
<summary>Gemini CLI</summary>

```bash
mkdir -p ~/.gemini/skills/ob-paper-humanizer
curl -sL https://raw.githubusercontent.com/gtskevin/ob-paper-humanizer/main/SKILL.md \
  -o ~/.gemini/skills/ob-paper-humanizer/SKILL.md
```
</details>

---

## How It Works

```
1. Paste your manuscript section (intro, theory, methods, results, discussion)
2. The skill scans for 17 categories of AI-detectable patterns
3. You get a structured suggestion list: each change shows original → suggested → risk → confidence
4. Accept, reject, or modify each suggestion individually
5. Quality check runs automatically on approved changes
```

### Example: Before vs After

**Before (AI-sounding):**
> It is important to note that employee voice plays a crucial role in organizational functioning. Furthermore, previous research has demonstrated that voice behavior has gained significant attention in the literature.

**After (Human-sounding):**
> Employee voice shapes how organizations function. A surge of recent studies examines when and why employees speak up — and what happens when they do.

### 17 AI Pattern Categories

| # | Category | Severity | Example Signal |
|---|----------|----------|---------------|
| 1 | Hollow Framing Phrases | **P0** | "It is important to note that..." |
| 2 | Transition Monotony | **P3** | "Furthermore, Moreover, In addition" |
| 3 | Generic Contribution Claims | **P1** | "contributes to the literature in several ways" |
| 4 | Hedging Overload | **P2** | "may possibly potentially suggest" |
| 5 | Sentence Structure Monotony | **P4** | Every sentence 25-35 words |
| 6 | Lack of Scholarly Voice | **P5** | No evaluative language, no intellectual stance |
| 7 | Formulaic Section Patterns | **P6** | Cookie-cutter intros and discussions |
| 8 | Post-Hypothesis Summaries | **P6** | "These hypotheses collectively contribute..." |
| 9 | Methods Without Rationale | **P6** | Procedures listed, no justification |
| 10 | Implications Inflation | **P1** | "Organizations should consider..." |
| 11 | Decorative Citations | **P7** | Citations that do no intellectual work |
| 12 | Mechanical Replacement | **P4** | Second-order AI signal in revisions |
| 13 | Gloss Parentheses | **P4** | "(reduced vigilance)" re-defining what was just explained |
| 14 | Metacommentary Announcements | **P4** | "This section proceeds in four steps." |
| 15 | False Precision | **P0** | Fabricated beta values or statistics |
| 16 | Trichotomy Framing | **P5** | "cognitive, affective, or both" |
| 17 | Post-Hoc Rationalization | **P5** | Cross-sectional data described as temporal sequence |

## Usage

Once installed, just paste your text and ask:

- **"Humanize this paragraph"** — scan and suggest changes
- **"De-AI my introduction"** — process a full section
- **"Does this sound like AI?"** — diagnostic scan only
- **"Just fix it"** — auto mode, apply all changes (opt-in)

### Workflow Modes

| Mode | When | What happens |
|------|------|-------------|
| **Suggestion** (default) | You want control | Shows each change for accept/reject/modify |
| **Auto** | You say "just fix it" | Applies all changes, provides summary |
| **Diagnostic** | You ask "does this sound like AI?" | Reports patterns found, no changes made |

## Why This vs Alternatives

| Approach | Problem |
|----------|---------|
| **Generic AI detectors** (Turnitin, GPTZero) | Tell you *if* text is AI-like, but not *how to fix it* |
| **Paraphrasing tools** (QuillBot, etc.) | Swap words but don't address structural AI patterns |
| **Manual editing** | You may not know what to look for — 17 categories is a lot |
| **OB Paper Humanizer** | Detects *and* fixes, journal-calibrated, surgical not destructive |

## FAQ

<details>
<summary>Will this help me pass AI detectors like Turnitin?</summary>

The goal is not to "trick" detectors — it is to **write well**. Good academic writing in OB naturally differs from AI-generated text. When you fix the writing, the detector problem dissolves. This skill makes your paper sound like a *seasoned OB scholar wrote it*, which is what reviewers want regardless of AI involvement.
</details>

<details>
<summary>Which journals does this cover?</summary>

The skill is calibrated for: **AMJ** (narrative-driven), **ASQ** (bold claims), **Org Science** (cross-disciplinary), **JAP** (precise, formal), **OBHDP** (balanced theory-empirics), **JOM** (accessible), **JOB** (practical), **PP** (psychology-forward). It also works for dissertation chapters, conference submissions, and R&R revisions.
</details>

<details>
<summary>Can it fabricate data or statistics to make my paper sound more specific?</summary>

**Absolutely not.** This is Rule #1 (literally): never fabricate data, effect sizes, sample sizes, or p-values. The skill uses directional language ("more strongly predicted") or references tables/figures. Fabricated data is academic misconduct, not humanization.
</details>

<details>
<summary>Does it change my argument or findings?</summary>

No. The surgical principle preserves your theoretical claims, empirical findings, and logical argument. It removes AI fingerprints *without* changing meaning. If any revision alters meaning, it is flagged and reverted.
</details>

<details>
<summary>I'm not technical. Can I still use this?</summary>

Yes. The easiest way: open Claude Code, type `Install ob-paper-humanizer from https://github.com/gtskevin/ob-paper-humanizer`, then paste your text and say "humanize this." No terminal skills needed.
</details>

## Contributing

1. Fork the repo
2. Create a feature branch: `git checkout -b my-feature`
3. Commit: `git commit -m 'Add feature'`
4. Push: `git push origin my-feature`
5. Open a Pull Request

Look for issues labeled `good first issue`.

## License

MIT — use freely in your research workflow.

---

<div align="center">
Built for OB researchers who use AI writing tools and want their manuscripts to sound like <em>them</em>, not <em>it</em>.
</div>
