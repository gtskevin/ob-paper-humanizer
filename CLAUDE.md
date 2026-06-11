# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

OB Paper Humanizer is a **portable AI skill** (not a software application). It detects and removes AI-detectable patterns from Organizational Behavior academic manuscripts. The entire project is documentation — there is no executable code, no build system, and no runtime dependencies.

**Repository**: `git@github.com:gtskevin/ob-paper-humanizer.git`

## What's Here

| File | Purpose |
|------|---------|
| `SKILL.md` | The skill definition — 17 AI pattern categories, workflow algorithms, OB writing norms, journal voice calibration. This is the core deliverable. |
| `README.md` | Installation instructions for Claude Code, Codex, Gemini CLI, Cursor, Windsurf. Feature overview and FAQ. |
| `CONTRIBUTING.md` | Contribution guidelines and scope of welcome contributions. |
| `assets/banner.svg` | Project branding. |
| `.github/ISSUE_TEMPLATE/` | Bug report and feature request templates. |

## Development Workflow

There are no build, test, or lint commands. All changes are edits to markdown files.

**Validation**: The only meaningful validation is reading SKILL.md carefully for internal consistency — pattern numbers, severity levels, and workflow steps must stay aligned across the file.

## Key Concepts (for editing SKILL.md)

- **17 pattern categories** numbered 1–17, each with a severity (P0–P7). The Quick Reference table at the bottom must stay in sync with the category sections.
- **Three workflow modes**: Suggestion (default), Auto (opt-in), Diagnostic. Steps 0–6 in the Workflow section are sequential.
- **Journal voice calibration**: AMJ, ASQ, Org Science, JAP, OBHDP, JOM, JOB, PP — each with distinct writing characteristics.
- **Surgical principle**: Edits should remove AI fingerprints without changing meaning. This principle appears in multiple places and is the primary design constraint.
- **Baseline test findings** (2020–2022 AMJ/JAP papers): The improvement rules (11–13 in Common Traps) were derived from these tests and must not be removed without new evidence.

## Integration Points

SKILL.md references four companion skills. Changes to skill names or scope should update these references:

- `intro-master` — introduction structure
- `ob-methods-results-check` — statistical audit
- `response-letter-audit` — R&R responses
- `survey-scale-review` — questionnaire validation
