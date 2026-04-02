---
name: codebase-explore
description: Use when the task is to understand an unfamiliar repository, discover relevant files before editing, trace where a symbol or feature lives, or narrow context without opening many files. Prefer rg over grep, git ls-files in Git repos, fd in non-Git directories, git grep for tracked-code-only searches, and sg or ctags only when structural or symbol-aware navigation is needed.
---

# Codebase Explore

Use this skill for repository exploration before broad edits or when the user asks where something lives.

## Goal

- Reduce context waste by narrowing from surface map to candidate files to targeted snippets.
- Avoid broad recursive scans, ignored noise, hidden files, binary files, and sensitive files by default.
- Keep the default exploration stack predictable and reviewable.

## Default exploration order

1. Read only top-level orientation files first.
   - `README*`, `AGENTS.md`, `CLAUDE.md`
   - `pyproject.toml`, `package.json`, `Cargo.toml`, `go.mod`, `CMakeLists.txt`, `Makefile`
2. Build a file surface map.
   - In a Git repo, prefer `git ls-files`.
   - Outside Git, prefer `fd`.
3. Narrow text candidates.
   - Prefer `rg -n -S`.
   - Use `git grep -n` when only tracked files should count.
4. Inspect only local context first.
   - Prefer `rg -n -C 3` or nearby-line reads with `sed -n`.
5. Open full files only after narrowing to a small set.
   - As a default, avoid opening more than 3 to 7 full files before summarizing findings.
6. Switch tools when plain text search becomes noisy.
   - Use `sg` for syntax-aware matching if available.
   - Use `ctags` for symbol jumps if available.
7. Debug unexpected omissions only after a narrow search fails.
   - Use `rg --debug`.
   - Use `git check-ignore -v <path>`.

## Tool preferences

- `rg`
  - Preferred over `grep` for recursive text search.
  - By default, it respects `.gitignore`, `.ignore`, and `.rgignore`.
  - By default, it skips hidden files/directories and binary files.
  - Use `rg --files` when a fast file list is enough.
- `git ls-files`
  - Preferred file listing in Git repositories.
  - Use it when you want the repository's tracked surface area rather than generated noise.
- `fd`
  - Preferred file listing outside Git or when path glob filtering matters.
  - By default, it skips hidden files/directories.
  - By default, it respects `.gitignore`, `.ignore`, `.fdignore`, and related ignore sources.
  - Use `-E` for explicit excludes.
- `git grep`
  - Prefer when only tracked files should be searched.
  - Useful when generated outputs or temp files would pollute `rg` results.
- `sg`
  - Use for AST-aware queries when string search is ambiguous.
- `ctags`
  - Use only if installed and symbol navigation is the real bottleneck.
- `repomix`
  - Optional packaging tool for external LLM workflows, not the default for local exploration.

## Guardrails

- Do not start with `grep -R`, `find /`, or a recursive scan rooted at the filesystem root.
- Do not disable ignore rules or include hidden files unless the user explicitly asks or the narrower search has already failed.
- Treat `.env`, `.env.*`, key material, credential files, `.git/`, `.codex/`, and `.agents/` as sensitive or non-routine.
- Prefer path-scoped searches when the likely subsystem is already known.
- Prefer `rg` over `grep`. Fall back only if `rg` is unavailable.
- Prefer `fd` over `find` for exploratory listing. Use `find` only for specific predicates or when `fd` is unavailable.
- When a search returns too much, narrow by path, file type, exact token, or context before opening files.

## Recommended command shapes

```bash
git ls-files
git ls-files | rg 'py$|cpp$'
rg -n -S "symbol_name" src tests
rg -n -C 3 "feature_flag" .
rg --files src
git grep -n "ExactClassName"
fd -tf -E .git -E node_modules
sg -p 'foo($X)' src
git check-ignore -v path/to/file
rg --debug -n "needle" path/to/subtree
```

## Escalation and reporting

- If the user wants "just find the files", stop after the candidate list and summarize the likely ownership.
- If the user wants a code explanation, move from candidates to small snippets before opening full files.
- If search misses expected files, report whether the likely cause is ignore rules, hidden files, generated output layout, or tool availability.
