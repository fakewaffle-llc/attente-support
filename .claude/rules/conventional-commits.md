# Commit messages: Conventional Commits

<!-- Managed in fakewaffle-llc/claude-plugins (rules/). Edit it there; a sync overwrites local edits. Repo-specific scopes and how work lands on main go in .claude/rules/commits-here.md. -->

Every commit on every branch of every fakewaffle repository uses [Conventional Commits](https://www.conventionalcommits.org/) (owner, 2026-10-23). `/release` and the Release Notes Writer read the types to pick the next version and write the notes.

```
<type>(<optional scope>): <summary>

<optional body: why, one paragraph per line>
```

Types:

- `feat` — something new a player, a staff member or a developer can use
- `fix` — a bug fix
- `perf` — faster or cheaper, same behaviour
- `refactor` — restructuring, same behaviour
- `test` — tests, probes, checks and gates only
- `docs` — documentation and designs only
- `chore` — tooling, dependencies, config, `.uid` files, engine upgrades
- `ci` — CI workflows and deploy scripts
- `build` — export, packaging, vendored binaries
- `style` — formatting only
- `revert` — undoing an earlier commit

Rules:

- The summary is lower case after the colon, has no trailing period, and says what changed and why in plain words: `fix: a sunk boat refuses the anchor`, not `fix: update anchor.gd`.
- A scope is optional unless this repo's `commits-here.md` says otherwise, and names the area changed. Use the scopes listed there.
- A breaking change to a save, a wire message, a schema, a public API or a CLI flag gets `!` after the type and a `BREAKING CHANGE:` line in the body saying what must change.
- Reference an issue in the summary or body as `(#123)`; another repository's as `owner/repo#123`.
- A merge commit takes the type of the work it brings in.
- Agent branches are squashed before they reach main: one conventional commit per change, not the wip messages joined together. No `wip:` or temporary-instrumentation commit reaches main.
- Squash onto your branch's own recorded base (`git merge-base HEAD origin/main` when you start), never `git reset --soft origin/main`: another session moves that ref, and the squash then reverts its work.
- Keep the attribution trailers the session asks for at the end of the body.
- Never force-push, amend a pushed commit to fix its message, or skip hooks; the next commit follows the rule.
