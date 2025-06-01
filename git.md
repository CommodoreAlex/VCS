### **Git & GitHub Cheat Sheet**

---
#### Setup & Authentication

| Command                                                      | Description                                                 |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| `ssh-keygen -t ed25519 -C "your_email@example.com"`          | Generate a new SSH key for GitHub authentication.           |
| `eval "$(ssh-agent -s)"`                                     | Start the SSH agent to manage your SSH keys.                |
| `ssh-add ~/.ssh/id_ed25519`                                  | Add your SSH key to the agent for automatic authentication. |
| `git remote set-url origin git@github.com:<user>/<repo>.git` | Switch from HTTPS to SSH for GitHub interactions.           |
| `git push https-origin main`                                 | Push using HTTPS instead of SSH.                            |
| `git push origin main`                                       | Push using SSH (default if remote is set to SSH).           |
| `ssh -T git@github.com`                                      | Test your SSH connection to GitHub.                         |

---
#### Setting Up & Managing Your Git Repo

|Command|Description|
|---|---|
|`git init`|Initialize a new Git repository.|
|`git remote add origin git@github.com:<user>/<repo>.git`|Connect the local repo to GitHub.|
|`git branch -a`|List all local and remote branches.|
|`git checkout -b main`|Create and switch to the `main` branch.|
|`git push origin main`|Push `main` to GitHub.|
|`git push origin --delete master`|Delete `master` remotely after switching to `main`.|

---
#### Tracking & Committing Files 

| Command                        | Description                                      |
| ------------------------------ | ------------------------------------------------ |
| `git status`                   | Check the status of modified/untracked files.    |
| `git add .`                    | Stage all changes for commit.                    |
| `git commit -m "Your message"` | Commit staged changes with a message.            |
| `git log --oneline`            | View commit history in a compact format.         |
| `git diff`                     | See differences between files before committing. |

---
#### Merging & Syncing Branches

|Command|Description|
|---|---|
|`git merge master`|Merge `master` into the current branch.|
|`git merge master --allow-unrelated-histories`|Merge branches with unrelated histories (fix for errors).|
|`git push origin main --set-upstream`|Set `main` as the upstream default branch.|

---
#### Handling Errors & Fixes

|Command|Description|
|---|---|
|`git branch -a`|Verify branch names if `git push origin main` fails.|
|`git fetch origin`|Retrieve remote branches and updates.|
|`git checkout main`|Switch to the `main` branch if it exists remotely.|
|`git branch -d master`|Delete `master` locally after migrating to `main`.|

---

## Most Common Workflow After Establishing SSH Keys

See which files have been modified:
```bash
git status
```

Then, add all files:
```bash
# This needs to be run from the root directory of your GIT repository
git add .
```

Commit your changes with a message describing your update:
```bash
git commit -m "Updated MiniGit functionality"
```

Push your changes to the repository:
```bash
git push origin main
```

(Replace `main` with the branch you're working in.)

Go to your GitHub repository and check if your changes are reflected.

#### If you receive errors when pushing changes to the repo

Pull the latest changes from GitHub:
```bash
git pull origin main --rebase
```

`--rebase` will ensure your local changes apply **ON TOP** of the latest remote updates.

Resolve any merge conflicts if any appear:
```bash
git add <conflicted file>
git rebase --continue
```

Push your changes after syncing:
```
git push origin main
```
