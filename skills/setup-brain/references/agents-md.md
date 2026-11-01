Skeleton for the brain's `AGENTS.md`. Fill it from the interview, keep it under 120 lines.

```markdown
# <First name>'s brain

Personal command center, run by agents. Everything is organised by **project**. Claude Code and Codex both read this file natively, so it is the single guide for every agent. Never create a `CLAUDE.md`.

## <First name>

- <What they do>, based in <place> (<time zone>).
- Products: <list, or "none yet">.
- Tech level: <not technical | tinkers | developer (stack)>. How to talk to them and how much to do alone is in the `## Output style` of the global rules: follow it here too.
- Tools every day: <list from the interview>.
- Never without asking: <their rules, or "nothing special">.
- Goals and notes live in <tool>. Read them when priorities matter.

## Layout

- `AGENTS.md`: this guide.
- `projects/`: one folder per project, each with its `About.md`.
- `notes/`: `journal/` (one file per day, `YYYY-MM-DD.md`), `ideas/` (ideas not yet started), `todos/` (loose todos not tied to a project).
- `archives/`: finished projects, read-only (created with the first archive).
- `.tmp/`: scratch, logs, screenshots, delete freely (created when needed, ignored by git).

Nothing else belongs at the root. No loose files, no new top-level folders. Never create a folder before there is something to put in it.

## Projects

Every piece of work belongs to a project folder in `projects/<slug>/` (lowercase, dashes). Before creating one, look for an existing project or hub that fits.

Hubs (sub-projects go inside, not next to them):

- <one hub per business or big area, e.g. `my-saas/`: product, marketing, ops>
- `perso/`: health, finance, home, travel (only once there is something personal)

Each project has:

- `About.md` (required): status + what it is, key ids/links, current state. Read it first, update it when something important changes.
- `Roadmap.md` (optional): plain checkbox todo list, only if the project has real open tasks.
- `files/` for text notes, `assets/` for inputs, `output/` for deliverables, each created with its first file only.

Status lifecycle: `active` while working, `paused` when parked, `done` when shipped. A `done` project moves to `archives/<slug>/` (keep the folder intact).

## Hygiene

- A todo for a project goes in its `Roadmap.md`. An idea not yet started goes in `notes/ideas/`, a loose todo in `notes/todos/`.
- A process to repeat later becomes a skill (with `skill-manager`), never a saved prompt: no `prompts/` folder.
- One fact, one place. Update `About.md` or an existing file before creating a new one.
- Every decision is written with its reason in the project's `About.md` (`## Decisions`), and so is every option that was rejected, so no agent redoes it. Read those lines before proposing a change.
- No per-step reports, status dumps or `final-v2.md` files. When a task is finished, fold the useful result into `About.md` and delete the rest.
- Scratch, screenshots and logs go in `.tmp/` or the project `output/`, never at the root.
- File names: `Title Case.md` or lowercase-with-dashes, `.md` for text.
- Delete by moving to the trash, never permanently. Archive instead of deleting anything with value.
- When you notice duplicates or a project living outside its hub, move it and fix the paths that pointed to it.

## Working in the brain

- New project ("new project: ..."): ask 3 to 5 short questions (goal, deadline, what done looks like), then create `projects/<slug>/` (inside the right hub) with its `About.md` and, if there are real next steps, `Roadmap.md`.
- Load a project ("load project X"): read its `About.md` and `Roadmap.md`, then sum up in 3 lines where it stands and what comes next.
- Save ("save", or at the end of a work session): update the project's `About.md` (each decision with its reason), `Roadmap.md` and today's journal in `notes/journal/`, then commit the brain.
- A process to repeat becomes a skill with `skill-manager`; a tool to plug in goes through `/connect-tool`.
```
