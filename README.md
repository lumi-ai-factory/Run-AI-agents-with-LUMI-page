# Run AI agents with LUMI — workshop site

![LUMI AI Factory logo](public/assets/LAIF_logo_dark_white_background.jpg)

The LUMI AI Factory branded website for the **Run AI agents with LUMI** workshop. It is built from the [LUMI AI Factory course template](https://github.com/lumi-ai-factory/course-template).

## Where the content lives

All text on the site comes from the workshop repository, [lumi-ai-factory/Run-AI-agents-with-LUMI-Workshop](https://github.com/lumi-ai-factory/Run-AI-agents-with-LUMI-Workshop) (branch `main`). Participants clone that repository to get the exercise code.

[`scripts/sync-workshop.ts`](scripts/sync-workshop.ts) fetches the workshop repo and turns it into pages:

| Site page | Source |
|---|---|
| Home | `README.md`, from the top to the `## Setup` heading |
| Setup | `README.md`, the `## Setup` section |
| Exercises | `README.md`, from the `## … Exercises` heading to `## After the workshop` |
| Exercise 0, 1, … (subpages) | `Exercise0.md`, `Exercise1.md`, … |
| After the workshop | `README.md`, from `## After the workshop` to the end |

The workshop repo is used exactly as it is. On the way, the script:

- splits the README at the headings above (to change the split, edit `README_PAGES` at the top of the script; any other new `##` section stays on the page before it),
- adds every new `ExerciseN.md` as a subpage automatically,
- rewrites links: `ExerciseN.md` and `#section` links point to the right site page, and links to anything else in the repo (e.g. `materials/…`) open the file on GitHub,
- turns blockquotes into branded callouts: a first line like `> Before you start:` or `> **Before you start:**` becomes the callout's title, and labels that sound like a warning give a warning box (otherwise a note). GitHub alerts (`> [!WARNING]`) are kept as they are.

## Publishing

The site is rebuilt and deployed to GitHub Pages:

- on every push to this repository,
- by hand: **Actions → Deploy to GitHub Pages → Run workflow**.

## Preview locally

```bash
bun install
bun run dev                     # fetches the workshop repo's main branch into .workshop/, then serves the site
```

To preview unpushed edits from your own checkout of the workshop repo:

```bash
WORKSHOP_DIR=../Run-AI-agents-with-LUMI-Workshop bun run dev
```

`WORKSHOP_DIR` reads that folder exactly as it is, on whatever branch is checked out. `WORKSHOP_REF=<branch>` instead fetches another branch from GitHub.

## Getting template updates

Follow the steps in the [template's README](https://github.com/lumi-ai-factory/course-template#getting-template-updates-into-your-course). After pulling, re-apply the changes this repository makes to template files, which the update overwrites:

- `package.json`: the `sync` script, and `bun scripts/sync-workshop.ts && ` at the start of `dev` and `build`,
- `.gitignore`: the `content/` and `.workshop/` entries.
