# User Guide for GIT

## Introduction

Git is a distributed version control system that helps manage source code efficiently. It allows developers to track changes, collaborate, and maintain code history.

----

## Installation

### Linux (Ubuntu/Debian)

```sh
sudo apt update
sudo apt install git
```
### Windows

Download and install Git from [git-scm.com](https://git-scm.com/downloads).

---

## Basic Git Configuration

```sh
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Initializing a Repository

```sh
git init my_project
cd my_project
```

## Cloning a Repository

```sh
git clone https://github.com/user/repo.git
```

---

## Basic Workflow

### Checking Status

```sh
git status
```

### Adding Files

```sh
git add file.txt
```

### Committing Changes

```sh
git commit -m "Added file.txt"
```

### Pushing Changes

```sh
git push origin main
```

### Pulling Updates

```sh
git pull origin main
```

---

## Branching

### Creating a New Branch

```sh
git branch feature-branch
```

### Switching to a Branch

```sh
git checkout feature-branch
```

### Merging a Branch

```sh
git checkout main
git merge feature-branch
```


---

## Undoing Changes

### Reset Last Commit

```sh
git reset --soft HEAD~1
```

### Discard Changes in a File

```sh
git checkout -- file.txt
```

---

## Working with Remote Repositories

### Adding a Remote

```sh
git remote add origin https://github.com/user/repo.git
```

### Viewing Remotes

```sh
git remote -v
```

### Removing a Remote

```sh
git remote remove origin
```

## Stashing Changes

```sh
git stash
```

----

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Git Guide](https://docs.github.com/en/get-started/using-git)

## Conclusion

Git is a powerful tool for version control and collaboration. Mastering its core features will improve your workflow and code management.
