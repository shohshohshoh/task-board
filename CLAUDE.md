# Task Board

## Project Overview

This is a task board project managed under `c:\Users\shoh0\Claude\task-board`.

## Git Rules

### Commit and Push on Every Change

After every code change, always commit and push to GitHub:

```powershell
git add <changed-files>
git commit -m "<message>"
git push origin <branch>
```

- Stage specific files by name — never use `git add -A` or `git add .` unless intentional.
- Write concise commit messages focused on *why*, not *what*.
- Push immediately after every commit. Do not batch multiple commits before pushing.
- Never force-push to `main`/`master`.
- Always confirm with the user before running destructive git operations (reset --hard, force push, branch delete).

### Branch Strategy

- `main` — stable, always deployable
- Feature work goes on a branch; merge via PR when complete

### Commit Message Format

```
<type>: <short summary>

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
```

Types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`

## Development Notes

- Platform: Windows 11, PowerShell
- Use PowerShell syntax in all shell commands (`$env:VAR`, backtick for line continuation)
