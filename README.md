# doreview

Runs Claude code reviews of GitLab MRs in parallel git worktrees + tmux.

## Setup

```bash
ln -s "$PWD/bin/doreview" ~/.local/bin/doreview
```

## Requires

`bash`, `git`, `glab` (logged in), `claude`, `tmux`, `fzf`, `jq`, `nvim`. Optional: `notify-send`.

## Use

```bash
doreview            # pick MRs with fzf
doreview <branch>   # review one branch
doreview --status   # see/attach/close reviews
```
