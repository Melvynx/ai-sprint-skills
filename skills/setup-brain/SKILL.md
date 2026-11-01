---
name: setup-brain
description: Set up the user's "brain", a single folder where their agent organises everything by project (an AGENTS.md, one folder per project and notes), after an interview about who they are, their technical level and how they want their agent to work. Writes that working style into the global rules of every agent (and Hermes on their server). Use when the user wants to set up or initialize their brain, organise their work with their agent, or starts from zero.
argument-hint: "[path, default ~/brain]"
metadata:
  internal: true
---

Set up the user's brain: one folder, run by their agent, where every piece of work lives in a project, so any future session can read one file and know who the user is, what they work on and where everything is. Before building anything, interview them, then write how they want to be talked to into the global rules, so every agent in every folder (and Hermes on their server) works their way from now on. Talk to the user in their language, one short question at a time, with no jargon (never say "frontmatter", "kebab-case", "symlink" or "repo" to them). Write every file in English, whatever language you talk in: the global rules, `AGENTS.md`, every `About.md` and `Roadmap.md`, the skills. Translate their answers; only names (products, people, tools) stay as they wrote them.

If you got this skill from a link instead of a local folder, install nothing else from the repo than the skills of step 8: download a file it links only when a step needs it, with `curl -fsSL https://raw.githubusercontent.com/Melvynx/ai-sprint-skills/main/skills/setup-brain/<path> -o <scratch>/<file>` (for example `references/agents-md.md` or `references/about-md.md`).

1. **Folder.** Use the argument as the target folder, otherwise `~/brain`, and confirm it in one line. If it already exists and is not empty, overwrite nothing: read its `AGENTS.md` and projects, tell the user what you found, skip the questions it already answers, and only add what is missing.
2. **Interview.** Say in one line why you ask (so the agent knows them and works their way), then ask the questions below, one per message, and wait for each answer. Give the choices or an example with every question so they never have to guess what you mean; use your multiple-choice question tool for 2, 3 and 4 when you have one. Accept short answers, rephrase once if an answer is unclear, never ask again what an earlier answer already told you, and move on if they skip one.
   1. Your first name, what you do in one sentence, and the city or time zone you work from?
   2. Your level with tech? Pick the closest: "I don't code and never use a terminal", "I tinker (no-code tools, tutorials, a terminal now and then)", or "I'm a developer". For a developer, ask their main languages and tools in the same message.
   3. How should your agent work? "Do everything for me and only ask what truly needs me" (recommended when they don't code), or "Step by step: show me the plan and I approve each step".
   4. In which language should it answer, and how: short and direct, or detailed?
   5. Your businesses or products, a name and one line each? "None yet" is fine.
   6. What are you working on right now? 3 to 5 things, work or personal.
   7. Which tools do you use every day? For example email (Gmail, Outlook), calendar, notes (Notion, Obsidian, Apple Notes), payments (Stripe), social networks, a newsletter tool.
   8. Where do your goals, plans or notes already live? A tool from question 7, somewhere else, or nowhere.
   9. Is there anything your agent must never do without asking you first? For example send an email in your name, pay for something, publish a post. "Nothing special" is fine.
   10. If your agent could take one task off your plate this week, which one would it be?
3. **Check.** Sum it up in 5 short lines (who they are, their level, how the agent will work, their businesses and current work, the never rules) and ask if it is right. Fix what they correct before writing anything.
4. **Global rules.** Build the `## Output style` block from answers 2, 3, 4 and 9 with [references/output-style.md](references/output-style.md). The global rules live in one file, `~/.agents/AGENTS.md`, and every agent reads that same file. First make it the single source: create it when missing, then for `~/.claude/CLAUDE.md` (Claude Code) and `~/.codex/AGENTS.md` (when the `~/.codex` folder exists), unless it is already a link to `~/.agents/AGENTS.md`, add its sections that the source does not have yet to `~/.agents/AGENTS.md` (each section once), trash the file and replace it with `ln -sfn ~/.agents/AGENTS.md <file>`. Do this without asking the user: a beginner does not know what Codex or CLAUDE.md are, and the link only makes every agent follow the same rules. Then write the block in `~/.agents/AGENTS.md`: when it already has a `## Output style` section, replace that section up to the next `## ` heading and keep every other line; otherwise add the block at the end, after one blank line. In the same file, write a `## Brain` section the same way (replace it when present), so every agent finds the brain from any folder:
   ```markdown
   ## Brain

   My brain is `<full path of the brain>`: every piece of work lives in a project there. Before working on a project, read the brain `AGENTS.md`, then the project's `About.md`. At the end of a work session, save what changed into the right project.
   ```
   Then tell the user in one plain line what changes: for a non-technical user, "From now on your agents do the technical part themselves and explain things simply."
5. **Folders.** Create only what the tree below shows: `AGENTS.md`, `projects/`, `notes/` with its three folders and a `.gitignore` with `.tmp/`, `.DS_Store`, `node_modules/`, `.env*`. Nothing else.
6. **AGENTS.md.** Write it from the interview with [references/agents-md.md](references/agents-md.md). It is the single guide for every agent working in the brain: never create a `CLAUDE.md` inside the brain.
7. **Projects.** For each business from question 5, create a hub in `projects/<slug>/`; for each item from question 6, create a project inside the right hub (or at `projects/` root if none fits). Create a `perso/` hub only when one of their answers is personal (health, home, travel, finance). Give every hub and project an `About.md` from [references/about-md.md](references/about-md.md). Write only what the user told you and leave "To fill" rather than guess a fact, number or link. Put the task from question 10 as the first line of the `Roadmap.md` of the project it belongs to (create `perso/` for it only when it fits no project). Add `Roadmap.md` only for real next steps, and `files/`, `assets/`, `output/` only when there is something to put in them.
8. **Skills.** The kit has three skills for every folder: `setup-brain` (this one), `connect-tool` (plugs a tool such as Notion or Stripe into the agent) and `skill-manager` (installs, removes, creates and fixes their skills). When `~/.agents/skills/connect-tool` or `~/.agents/skills/skill-manager` is missing, take it fresh from the package: `mkdir -p <scratch>/pkg && curl -fsSL https://github.com/Melvynx/ai-sprint-skills/archive/refs/heads/main.tar.gz | tar -xz -C <scratch>/pkg`, copy `<scratch>/pkg/ai-sprint-skills-main/skills/<name>/` to `~/.agents/skills/<name>/` with its scripts, and link it for Claude Code with `mkdir -p ~/.claude/skills && ln -sfn ~/.agents/skills/<name> ~/.claude/skills/<name>` unless `~/.claude/skills` already links to `~/.agents/skills`. Install nothing else: the brain itself holds no skill on day one.
9. **Save.** Run `git init` and a first commit "brain: initial setup". Ask if they want a private copy on GitHub so they never lose it; create and push only on yes, always private.
10. **Hermes.** If they already have a server agent (`ssh -o BatchMode=yes hermes true` works and `ssh hermes 'command -v hermes-setup' < /dev/null` finds it), give Hermes the same style: `awk '/^## Output style[[:space:]]*$/{f=1;print;next} f&&/^## /{f=0} f' ~/.claude/CLAUDE.md | ssh hermes 'hermes-setup style'`. It answers `style ok`, and `ssh hermes 'hermes-setup check' < /dev/null` then shows `style=set`. Without a server, skip this step: `setup-vps` does it when they set one up.

```text
<brain>/
├── AGENTS.md          The single guide for every agent
├── .gitignore
├── projects/          One folder per project, each with its About.md
└── notes/
    ├── journal/       Daily notes, one file per day (YYYY-MM-DD.md)
    ├── ideas/         Ideas not yet started
    └── todos/         Loose todos not tied to a project
```

That is the whole brain on day one. Never create a folder before there is something to put in it: `archives/` appears with the first archived project, `.tmp/` with the first scratch file, `files/`, `assets/` or `output/` inside a project with their first file. No `prompts/` or `scripts/` folder: a process the agent should repeat later becomes a skill (with `skill-manager`), never a saved prompt.

Finish with a short check list, a check or a cross on each line: interview done and confirmed, `## Output style` and `## Brain` in `~/.agents/AGENTS.md`, with `~/.claude/CLAUDE.md` (and `~/.codex/AGENTS.md` if Codex is there) a link to it, `AGENTS.md` exists and there is no `CLAUDE.md` in the brain, only the tree above in the brain (no empty folder anywhere), every project has an `About.md` with a status, `/connect-tool` and `skill-manager` open in `~/.claude/skills`, git is initialised (and pushed if they chose GitHub), Hermes has the style (or "no server yet"). Then tell the user in 3 lines where their brain is, that from now on, with Claude opened in the brain, they ask for "new project: ..." for something new, "load project X" to pick one up and "save" at the end of a conversation to file it into the project, that `/connect-tool <tool>` plugs in their tools, and offer to start on their answer to question 10 right now.
