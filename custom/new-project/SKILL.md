---
name: new-project
description: Create a new private repo from the working-open/project-starter template and start its devcontainer. Use when the user wants to start a new project.
---

# New Project Setup

Creates a new private GitHub repo from the `working-open/project-starter` template (which includes a devcontainer), clones it, and starts the devcontainer.

The canonical implementation is the fish function `new-project` in `/repos/dotfiles/fish/functions/new-project.fish` (symlinked into `~/.config/fish/functions/` by the dotfiles ansible playbook). Keep that file as the single source of truth — if the process changes, update the function, not this skill.

## Steps

1. **Check GitHub auth first.** The gh keyring token goes stale regularly. Run `gh auth status -h github.com`. If it fails, authentication is interactive and cannot be done by the agent — ask the user to run it themselves in this session:

   ```
   ! gh auth refresh -h github.com
   ```

   Wait for them to confirm before continuing.

2. **Pick the location.** New repos are cloned under `/home/repos` unless the user says otherwise.

3. **Run the function** with the project name the user gave (ask if they didn't give one):

   ```
   cd /home/repos && new-project <name>
   ```

   This runs `gh repo create <name> --template working-open/project-starter --private --clone` followed by `devcontainer up --workspace-folder <name>`.

4. **Report the result**: the repo URL, the local path, and whether the devcontainer came up cleanly. If `devcontainer up` fails, show the error — it usually means Docker isn't running or the template's devcontainer config has an issue.
