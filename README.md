# Run AI agents with LUMI — workshop

![LUMI AI Factory logo](public/assets/LAIF_logo_dark_white_background.jpg)

Website and exercise materials for the **Run AI agents with LUMI** workshop, built from the [LUMI AI Factory course template](https://github.com/lumi-ai-factory/course-template).

## What is where

| Folder | Contents |
|---|---|
| `content/` | The website pages, one Markdown file per page |
| `materials/` | The exercise code that participants clone on LUMI |

Participants get only `materials/`, with this command from the Setup page:

```bash
git clone --depth 1 --filter=blob:none --sparse https://github.com/lumi-ai-factory/Run-AI-agents-with-LUMI-page.git agent-workshop
git -C agent-workshop sparse-checkout set --no-cone /materials/
```

The branch `NAIFS-2026-10-workshop` keeps the materials of the Nordic AI Factory Summit workshop (October 2026) exactly as they were, with their history from the former `Run-AI-agents-with-LUMI-Workshop` repository.

## Publishing

The site is rebuilt and deployed to GitHub Pages on every push to `main`. To redeploy by hand: **Actions → Deploy to GitHub Pages → Run workflow**.

## Preview locally

```bash
bun install
bun run dev
```

## Getting template updates

Follow the steps in the [template's README](https://github.com/lumi-ai-factory/course-template#getting-template-updates-into-your-course). The update leaves `content/`, `public/`, `materials/` and this README alone, so nothing needs re-applying afterwards.
