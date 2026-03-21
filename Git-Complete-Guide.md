# Git Complete Guide (Command Based)

## Note: You can run these commands on both VS Code and Git Bash

### Git Configuration
1. **How to know your registered Email and username:** `git config --list`  
   **When to use:** To check your current Git configuration settings, such as user name, email, and other global/local options.
2. **How to change the associated Email globally:** `git config --global user.email "you@example.com"`  
   **When to use:** When setting up Git for the first time or changing your email address across all repositories on your system.
3. **How to set the username:** `git config --global user.name "Your Name"`  
   **When to use:** When configuring Git initially or updating your display name for commits across all repositories.

### Initializing and Staging Files
4. **How to initialize the git project:** `git init`  
   **When to use:** To start tracking a new project with Git by creating a .git directory in the project folder.
5. **How to stage files in git:**  
   - For staging all files: `git add .`  
     **When to use:** To stage all modified, new, or deleted files in the working directory before committing.  
   - For staging only some files: `git add [file_name1] [file_name2]...`  
     **When to use:** To selectively stage specific files, allowing you to commit only certain changes while leaving others unstaged.

### Git Branches
6. **How to know the current working branch / List of all branches:** `git branch`  
   **When to use:** To see which branch you're currently on and list all local branches in the repository.
7. **How to rename the branch:** `git branch -m <old-branch-name> <new-branch-name>`  
   **When to use:** To rename a branch, such as correcting a typo in the branch name or updating it for clarity.
8. **How to delete a branch:** `git branch -d <branch-name>`  
   **When to use:** To remove a branch that is no longer needed, provided it has been merged. Use `-D` for force delete if not merged.
9. **To create a new branch:** `git branch <branch-name>`  
   **When to use:** To create a new branch without switching to it, useful for preparing branches in advance.
10. **To change/switch to a branch:** `git switch <branch-name>`  
    **When to use:** To switch your working directory to a different branch, ensuring a clean working tree.
11. **How to create a new branch and switch to it:** `git switch -c <branch-name>`  
    **When to use:** When starting work on a new feature or bug fix, to create and immediately switch to the branch.
12. **To check if branch exists and switch (legacy command):** `git checkout <branch-name>`  
    **When to use:** Legacy way to switch branches; prefer `git switch` for newer Git versions.
13. **To merge a branch:** `git merge <branch-name>`  
    **When to use:** To combine changes from one branch into another, typically merging feature branches into main.

### Git Stash
**Case:** When you stage changes in one branch and try to switch to another branch, Git may give an error like:  
`error: Your local changes to the following files would be overwritten by checkout: One/f1.txt`  
`Please commit your changes or stash them before you switch branches.`  
In such cases, use stash to temporarily store your staged changes.

14. **To stash (store your updates temporarily):** `git stash`  
    **When to use:** To save uncommitted changes (staged or unstaged) when you need to switch branches or pull changes without committing.
15. **Naming the stash:** `git stash save "Work in progress on X feature"`  
    **When to use:** To stash changes with a descriptive name for better organization when you have multiple stashes.
16. **Apply the stash (latest one):** `git stash apply` or `git stash apply stash@{0}` (for specific stash)  
    **When to use:** To reapply stashed changes to your working directory without removing them from the stash list.
17. **Apply the stash and drop from stash list:** `git stash pop`  
    **When to use:** To apply the latest stash and remove it from the stash list in one command.
18. **Drop the stash:** `git stash drop`  
    **When to use:** To delete a stash entry without applying it, useful for cleaning up unwanted stashes.

### Git Rebase
**Purpose:** To avoid unnecessary commits, use rebase.  
**Note:** Do not use rebase on main or master branches due to best practices.

19. **To rebase a branch:** `git rebase <branch-name>`  
    **When to use:** To replay commits from your current branch on top of another branch, creating a linear history (e.g., rebasing a feature branch onto main).

### Git Reflog
Git reflog shows the history of your commits, useful for debugging and understanding project history.

20. **Command:** `git reflog`  
    **When to use:** To view the history of HEAD movements, useful for recovering lost commits or understanding recent actions.
21. **To reset to a specific commit and discard all changes after it:** `git reset --hard <commit-id>`  
    **When to use:** To permanently undo commits and discard all changes after a specific point, use with caution as it's destructive.

### Committing Changes
22. **To commit staged changes:** `git commit -m "Your commit message"`  
    **When to use:** To save staged changes to the repository with a descriptive message.
23. **To commit all tracked files (add and commit in one step):** `git commit -a -m "Your commit message"`  
    **When to use:** To quickly commit all modified tracked files without explicitly staging them first.
24. **To fix the last commit (add missing files or change message):** `git commit --amend -m "Updated commit message"`  
    **When to use:** When you made a typo in the last commit message or forgot to add a small change. Use with caution if already pushed.

### Working with Remotes
25. **Add a remote repository:** `git remote add origin <repository-url>`  
    **When to use:** To connect your local repository to a remote repository (e.g., on GitHub) for the first time.
26. **View remote repositories:** `git remote -v`  
    **When to use:** To list all configured remote repositories and their URLs.
27. **Remove a remote:** `git remote remove <remote-name>`  
    **When to use:** To disconnect a remote repository that is no longer needed.

### Pushing and Pulling
28. **Push changes to remote branch:** `git push origin <branch-name>`  
    **When to use:** To upload your local commits to the remote repository after committing changes.
29. **Push and set upstream (first push):** `git push -u origin <branch-name>`  
    **When to use:** On the first push of a new branch, to set the upstream branch for future pushes.
30. **Pull changes from remote:** `git pull origin <branch-name>`  
    **When to use:** To fetch and merge changes from the remote repository into your current branch.
31. **Fetch changes without merging:** `git fetch origin`  
    **When to use:** To download changes from the remote without automatically merging, allowing you to review before merging.

### Cloning Repositories
32. **Clone a repository:** `git clone <repository-url>`  
    **When to use:** To create a local copy of a remote repository for the first time.

### GitHub-Specific Workflow
33. **Fork a repository on GitHub (via web interface, then clone your fork):** `git clone <your-fork-url>`  
    **When to use:** To contribute to an open-source project by creating your own copy on GitHub and cloning it locally.
34. **Create a pull request (via GitHub web interface after pushing your branch)**  
    **When to use:** After pushing your feature branch, to propose merging your changes into the main repository.
35. **Sync your fork with upstream:**  
    - Add upstream: `git remote add upstream <original-repo-url>`  
      **When to use:** To connect your fork to the original repository for syncing.  
    - Fetch upstream: `git fetch upstream`  
      **When to use:** To download the latest changes from the original repository.  
    - Merge upstream changes: `git merge upstream/main`  
      **When to use:** To incorporate updates from the original repository into your local main branch.

### Advanced Git Commands
36. **Cherry-pick a commit:** `git cherry-pick <commit-id>`  
    **When to use:** To apply a specific commit from one branch to another without merging the entire branch.
37. **Interactive rebase:** `git rebase -i <commit-id>`  
    **When to use:** To edit, reorder, or squash commits in your branch history for a cleaner commit log.
38. **Bisect for finding bugs:** `git bisect start`, `git bisect bad`, `git bisect good <commit-id>`  
    **When to use:** To perform a binary search through commit history to find the commit that introduced a bug.
39. **View commit history (improved):** `git log --oneline --graph --all`  
    **When to use:** To see a visual tree of all branches and commits in a concise list.
40. **View differences:** `git diff` (unstaged), `git diff --staged` (staged)  
    **When to use:** To see changes between working directory and last commit (unstaged) or staged changes before committing.
41. **Undo local changes in a file (modern):** `git restore <file_name>`  
    **When to use:** When you messed up a file and want to revert it back to the last committed state.
42. **Undo last commit (keep changes):** `git reset --soft HEAD~1`  
    **When to use:** To undo the last commit but keep the changes staged, allowing you to recommit with modifications.
43. **Undo last commit (discard changes):** `git reset --hard HEAD~1`  
    **When to use:** To completely remove the last commit and discard all changes, use with extreme caution.
44. **Create and apply patches:** `git format-patch` and `git am`  
    **When to use:** To create patch files from commits and apply them elsewhere, useful for sharing changes without pushing.

### Best Practices
- Always pull before pushing to avoid conflicts.
- Use descriptive commit messages.
- Work on feature branches, not directly on main/master.
- Regularly commit small, logical changes.
- Use `.gitignore` to exclude unnecessary files.
- Review changes with `git diff` before committing.
- Use `git status` frequently to check repository state.
- Avoid force pushing (`git push --force`) unless necessary and communicated.

### Additional Resources
- Git Documentation: https://git-scm.com/doc
- GitHub Guides: https://guides.github.com/
- Pro Git Book: https://git-scm.com/book/en/v2

**Note:** This guide covers essential Git and GitHub commands with situations for use. Practice in a test repository to understand the concepts better. If you encounter issues, use `git status` and `git log` for debugging.