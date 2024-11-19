name

### **Task List: Focused on Advanced Git Operations**

### **Part 1: Understanding and Using `git stash`**

#### **Task 1: Save Changes Temporarily with `git stash`**
1. Make changes to a file without committing:  
   ```bash
   echo "Temporary changes" >> temp-file.txt
   ```
* Answer:- make changes in file.

2. View the status of changes:  
   ```bash
   git status
   ```
* Answer:- this command shows the current state of the working directory and staging area. also tells that which files are modifieded,untracked,stage for commit.

3. Stash the changes:  
   ```bash
   git stash
   ```
* Answer:- it saves uncommitted changes,which means It allows you to switch branches or work on something else.

4. View the stashed changes:  
   ```bash
   git stash list
   ```
* Answer:- it shows all the stashed changes which are saved in repository.

#### **Task 2: Apply and Drop Stashed Changes**
1. Apply the most recent stash:  
   ```bash
   git stash apply
   ```
* Answer:- it's restores the recent stashed changes to your working directory without removing them from the stash list.

2. Drop the most recent stash after applying it:  
   ```bash
   git stash drop
   ```
* Answer:-it's removes stash from the stash list.like its delete stash from list.

3. Alternatively, to apply a specific stash:  
   ```bash
   git stash apply stash@{1}
   ```
* Answer:-

  * stash@{1}: Refers to the second stash in the stash list (stashes are indexed starting at 0).

  * git stash apply: Applies the changes from the specified stash without removing it from the stash list.

#### **Task 3: Stash Untracked Files**
1. Stash changes, including untracked files:  
   ```bash
   git stash -u
   ```
* Answer:- this command stashes both tracked and untracked files,allowing to save all the work in progress while keeping working directory clean.
   
   * -u : Includes untracked files in the stash.
   * By default, git stash only stashes changes to tracked files.

2. Apply stashed changes including untracked files:  
   ```bash
   git stash apply
   ```
* Answer:- it's restores the recent stashed changes to your working directory without removing them from the stash list.

---

### **Part 2: Rewriting History with `git rebase`**

#### **Task 4: Rebase Commits to a New Base**
1. Rebase the current branch onto `main`:  
   ```bash
   git rebase main
   ```
* Answer:- this command is used to reapply commits from current branch on top of the main branch, effectively "rebasing" your work onto main.

2. Resolve any conflicts that may arise during rebase, and continue:  
   ```bash
   git rebase --continue
   ```
* Answer:- this command is used after resolving conflicts during a rebase. It tells Git to proceed with the rebasing process from where it was paused.

#### **Task 5: Canceling a Rebase**
1. If a rebase goes wrong, abort it:  
   ```bash
   git rebase --abort
   ```
* Answer:- this command is used to cancel an ongoing rebase process and return branch to the state it was in before the rebase started.

---

### **Part 3: Interactive Rebase (`git rebase -i`)**

#### **Task 6: Use Interactive Rebase to Modify Commit History**
1. View the last few commits:  
   ```bash
   git log --oneline
   ```
* Answer:- this command shows a condensed summary of the commit history, with each commit displayed as a single line.

2. Start an interactive rebase for the last 3 commits:  
   ```bash
   git rebase -i HEAD~3
   ```
* Answer:- This command opens an editor with the list of commits in the last 3 commits.

   -i :- it means that it allows you to modify,reorder ,give full control over how the commit history looks.

   HEAD~3 :-This specifies The interactive rebase will only apply to last 3 commits.

3. Modify the commits by changing `pick` to one of the following:
   - `squash` (combine commits)

      * Answer:- this command is used to Combines the selected commit into the previous one.use this to merge multiple commits into a single,cleaner commit.during a process we also have option to modify message.

   - `reword` (edit commit message)

     * Answer:- this command allows to edit the commit message of the selected commit.

   - `edit` (edit commit content)

     * Answer:- this command Lets you pause the rebase and edit the changes in the commit.use git commit --amend to update the commit, then git rebase --continue to proceed.

   - `drop` (remove commit)
     * Answer:- this command is used to deletes the commit from the history.use this to remove unwanted commits entirely.

4. Example of squashing two commits:
   - Change the second commit from `pick` to `squash` and save.
   - Git will combine the commit messages for the squashed commit.

#### **Task 7: Complete Interactive Rebase**
1. After modifying the commits, save and close the editor.
2. Resolve any conflicts if prompted, then continue the rebase:  
   ```bash
   git rebase --continue
   ```

---

### **Part 4: Cherry-Picking Commits (`git cherry-pick`)**

#### **Task 8: Pick a Specific Commit**
1. View the commit history to find the commit hash you want to cherry-pick:  

   ```bash
   git log --oneline
   ```
* Answer:- for view commit history.

2. Cherry-pick a specific commit by its hash:  

   ```bash
   git cherry-pick <commit-hash>
   ```
* Answer:- This command takes a specific commit from another branch and applies it to current branch.in short it means that its copy text from another branch without merging it.

3. Resolve conflicts if any, then commit the changes:  
   ```bash
   git add .
   git cherry-pick --continue
   ```
* Answer:- this command is used to resume the cherry-pick process after resolving conflicts that occurred during the cherry-picking of a commit.

---

### **Part 5: Tagging Commits (`git tag`)**

#### **Task 9: Tag a Commit**
1. Tag the current commit with a version number:  
   ```bash
   git tag -a v1.0 -m "Initial release"
   ```
* Answer:- creates an annotated tag named v1.0 with a message "Initial release".

2. List all tags:  
   ```bash
   git tag
   ```
* Answer:- this command is used to create, list, delete, or manage tags in Git. Tags are markers used to label specific points in your commit history, often for releases or milestones.

#### **Task 10: Tag a Specific Commit**
1. Tag a specific commit by its hash:  
   ```bash
   git tag -a v1.1 <commit-hash> -m "Bug fix"
   ```
* Answer:- this command creates an annotated tag on a specific commit identified by <commit-hash> and associates it with the message "Bug fix".

    * git tag -a v1.1: Creates an annotated tag v1.1.
    
    * commit-hash: Specifies the commit on which the tag will be applied. 

    * -m "Bug fix": Adds a message to the tag to describe the reason for the tag.

#### **Task 11: Push Tags to Remote**
1. Push a specific tag to the remote repository:  
   ```bash
   git push origin v1.0
   ```
* Answer:- push the tag v1.0.

2. Push all tags to the remote repository:  
   ```bash
   git push --tags
   ```
* Answer:- this command is used to push all tags in local repository to the remote repository.

---

### **Part 6: Working with Remote Repositories**

#### **Task 12: Add a Remote Repository**
1. Add a remote repository URL to the project:  
   ```bash
   git remote add origin https://github.com/username/repo.git
   ```
* Answer:- add remote repo.

#### **Task 13: Fetch Changes from Remote**
1. Fetch changes from the remote repository without merging them:  
   ```bash
   git fetch origin
   ```
* Answer:- this command git fetch origin is used to retrieve updates from the remote repository (in this case, origin) without merging them into your local branch.

2. View fetched branches:  
   ```bash
   git branch -r
   ```
* Answer:- this command lists all remote branches of repository.

#### **Task 14: Pull Changes from Remote**
1. Pull the latest changes from the remote repository and merge them into the local branch:  
   ```bash
   git pull origin main
   ```
* Answer:- pull changes from remote repo.

#### **Task 15: Push Changes to Remote**
1. Push local changes to the remote repository:  
   ```bash
   git push origin main
   ```
* Answer:- push change to remote repo.

2. Push a new branch to the remote repository:  
   ```bash
   git push origin feature-branch
   ```
* Answer:- push second branch's change to remote repo.

#### **Task 16: Delete Remote Branch**
1. Delete a remote branch:  
   ```bash
   git push origin --delete feature-branch
   ```
* Answer:- delete feature-branch from repo.

---

### **Part 7: Forking and Contributing to Open-Source Projects**

#### **Task 17: Fork a Repository on GitHub**
1. Go to a repository on GitHub and click **Fork** in the top right corner to create your own copy of the repository.

2. Clone the forked repository to your local machine:  
   ```bash
   git clone https://github.com/your-username/repo.git
   ```
* Answer:- make copy of repo from remote to local.

#### **Task 18: Make Changes and Commit**
1. Create a new branch for your changes:  
   ```bash
   git checkout -b fix-typo
   ```
* Answer:- create new branch and directly switch to it.

2. Make changes to the code (e.g., fix a typo in `README.md`), stage, and commit them:  
   ```bash
   git add README.md
   git commit -m "Fixed typo in README.md"
   ```
* Answer:- make changes in file,stage it and commit it.

#### **Task 19: Push Changes to Your Fork**
1. Push the changes to your remote fork:  
   ```bash
   git push origin fix-typo
   ```
* Answer:- push change to remote repo.

#### **Task 20: Create a Pull Request**
1. Go to your forked repository on GitHub, click on **Compare & Pull Request**.
2. Write a description of your changes and submit the pull request to the original repository.

#### **Task 21: Sync Your Fork with the Original Repository**
1. Add the original repository as a remote source:  
   ```bash
   git remote add upstream https://github.com/original-owner/repo.git
   ```
* Answer:- This command adds a new remote repository named upstream to the local Git project and points it to the specified URL.

2. Fetch changes from the original repository:  
   ```bash
   git fetch upstream
   ```
* Answer:- this command upstream retrieves the latest changes from the remote repository named upstream without modifying working directory.

3. Merge changes from the original repository into your local branch:  
   ```bash
   git checkout main
   git merge upstream/main
   ```
* Answer:- switch into main branch after that merge two branches.

4. Push the changes to your fork:  
   ```bash
   git push origin main
   ```
* Answer:- push the changes into main branch.

---

