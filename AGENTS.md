# AGENTS.md

Core generates the published startr.style sheet and `props.json`. The site and releases live in [WEB-Startr.Style](https://github.com/Startr/Style).

## Commands

- `bun install` once per clone.
- `bun run build` writes `dist/`. Build into a scratch folder for checks; leave the untracked `dist/` alone.
- `bun run serve` and `bun run watch` are the dev loops.

## Gates

- `bun test scripts`
- `bun run parity` compares the build with `test/fixtures/published-1.3.2.css`. It must print PARITY OK.

## Probes

- `bun run probe:hover`, `probe:tap` and `probe:diff` live in `scripts/`. They take seconds against a real page.
- `docs/design-ingest.md` is the manual for re-cutting a page onto the kit.

## Merges

Master is merge-only, through PRs. Core CI cannot push `dist/`, so never rely on it for built files.

## Releases

Releases happen in WEB-Startr.Style: a git-flow release branch, a subtree pull of core, `make core_publish`, `make version_snapshot`. Bump `package.json` "version" with each release; it moved 1.2.2, 1.4.0, 1.4.1, 1.4.2.

## Board

`TODO.md` follows the shared rules below. Dossiers live in `docs/board-dossiers.md`.

## Shared rules

The same block sits in every Sage.is and Startr repo's AGENTS.md; change it everywhere or nowhere.

- **Git.** Agents commit and push only when the person they work for says so in that session. Commits are authored as that person and carry an AI co-author trailer. Subjects read `type(scope): subject` (`feat`, `fix`, `docs`, `refactor`, `test`, `chore`).
- **Design.** startr.style inline props in `style` attributes, never classes. Write the base (phone) value first; add an `-sm`/`-md`/`-lg`/`-xl` tier only where the layout changes, and never repeat the base value in a tier. New pages ship plain HTML first; never a third visual language. The kit's manual is [design-ingest.md](https://github.com/Startr/WEB-startr.style.core/blob/master/docs/design-ingest.md).
- **Browser checks are scripts.** `bun run probe:hover`, `probe:tap` and `probe:diff` run from a WEB-startr.style.core checkout and take seconds; they replace long agent sessions clicking through pages.
- **Board.** `TODO.md` sections are the kanban columns. Each card is one short claim line (under about 350 characters) with a sub-checklist; narration goes to `board-dossiers.md` in the docs folder. `KANBAN.canvas` is generated from `TODO.md`; never hand-edit it.
- **Names.** Tracked files name work paths, not people; only Alexander is named. Clients go by codename.
- **Secrets.** In the environment or the team vault; never in chat, a command line or a tracked file.
