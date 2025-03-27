# Git Hooks Guide: Enforcing Commit Messages

## Introduction
Git hooks are scripts that Git executes before or after certain important repository events. One common use case is enforcing commit message policies to ensure meaningful commit messages.

In this guide, we'll create a pre-commit Git hook to prevent commits without a commit message.

## Understanding Git Hooks
Git hooks are located in the `.git/hooks/` directory of a repository. By default, this folder contains sample hook scripts. Hooks can be written in shell, Python, or any other scripting language.

## Creating a Pre-Commit Hook
A pre-commit hook runs before a commit is created, allowing us to validate commit messages.

### Steps to Implement
1. Navigate to your Git repository:
   ```sh
   cd /path/to/your/repository
   ```

2. Create a `pre-commit` hook script:
   ```sh
   nano .git/hooks/pre-commit
   ```

3. Add the following script to enforce commit messages:
   ```sh
   #!/bin/bash

   COMMIT_MSG=$(git log -1 --pretty=%B)

   if [[ -z "$COMMIT_MSG" || "$COMMIT_MSG" =~ ^\s*$ ]]; then
       echo "Error: Commit message cannot be empty. Please provide a meaningful commit message."
       exit 1
   fi

   exit 0
   ```

4. Make the script executable:
   ```sh
   chmod +x .git/hooks/pre-commit
   ```

## Testing the Hook
1. Try committing without a message:
   ```sh
   git commit --allow-empty -m ""
   ```
   You should see an error message preventing the commit.

2. Try committing with a valid message:
   ```sh
   git commit --allow-empty -m "Added security checks"
   ```
   The commit should succeed.

## Conclusion
Git hooks are a powerful way to enforce repository standards. By using a `pre-commit` hook, we ensure that every commit has a meaningful message, improving collaboration and history tracking.
