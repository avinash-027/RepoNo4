# RepoNo4

Branching, Merging and Feature Branch Workflow

## Branching

"When working with Git, you can create a separate branch from the main branch. Instead of adding commits directly to the main branch, you add them to the new branch. The advantage of this approach is that you can make multiple commits for your feature or changes without affecting the main branch. This allows you to work independently on the feature, and once it's ready, you can merge it back into the main branch."

"Instead of adding commits directly to the main branch, you add them to this new branch. This is beneficial whether you're working on a new feature or a bug fix."
```
git branch <name>
git checkout <name>
git commit -m "feature"
```
To fix a bug GoTo main 
```
git checkout main
git commit -m "bug fix"
```

### New Branch Creation in Git
In Git, a new branch is created at the current position of the HEAD pointer, which indicates the current branch and commit you're working on.

* HEAD points to the latest commit in the currently checked-out branch.
* When you create a new branch, Git will base it on the commit that HEAD is currently pointing to.

### What Happens When You Delete the feature Branch:

Deleting a Local Branch (`git branch -d feature`):

- Locally: The branch is deleted, but its commits will remain if they are already merged into other branches.

Deleting a Remote Branch (`git push origin --delete feature`):

- Remotely: The branch is deleted from the remote, but the commits remain in merged branches.

The branch disappears, but the commit history remains accessible in other branches where those commits were merged.

**Important Note:**
If you run `git push origin feature` after deleting the local branch with `git branch -d feature`, Git will throw an **error** because the feature branch no longer exists locally.

If you want to delete the feature branch remotely (from GitHub or another remote), you'd use:
`git push origin --delete feature` 

This will delete the remote branch, but the branch and its history will remain in any commits where it was merged (like in main or another branch).

### List of branches created
```
RepoNo4> git branch 
  conflict
  feature1
* main
  new-feature
```

---

## Merging

* git merge branch-name: Merges the specified branch into your current branch.
* If conflicts happen, resolve them and commit the resolution.

**1. Merging Two Branches:**

- When you merge two branches, the changes from the other branch are added to the current branch you are working on.
- Example: To merge the feature1 branch into the branch you're currently on:
     ```
     git merge feature1 -m "Merge feature1"
     ```

**2. Merge Conflicts:**

- Sometimes, Git can't automatically merge changes and will show a merge conflict.
- If a conflict occurs, you need to manually resolve the conflicts in the affected files.

**3. Resolving Merge Conflicts:**

- After resolving the conflict, use the following commands:
    ```
    git add .
    git commit -m "Merge conflict resolved"
    ```
- This will stage the resolved files and commit the merge.

---

## Feature Branch WorkFlow :

1. Create a feature branch
```
git checkout -b new-feature
git commit -am "new feature"
```
2. Upload feature branch to GitHub
You need to manually push both the main and feature branches to GitHub.
```
git push origin feature-branch
git push origin main
```
3. Create a “Pull Request” (do code reviews)

4. Merge feature branch into master/main branch (merging happens on GitHub)

---

## Pull from github

Switch to the branch you want to pull changes into:
```
git checkout <branchname>
```
Fetch updates from the remote repository (this brings down the latest changes without merging them into your local branch):
```
git fetch origin
```
Pull changes from the remote branch into your local branch:
```
git pull origin <branchname>
```
---

## Merge conflicts in feature branch workflow
```
# Create and switch to feature1 branch
git checkout -b feature1
# Make changes to a file (e.g., `file.txt`)
git commit -am "feature1"

git push origin feature1

# Create and switch to feature2 branch
git checkout -b feature2
# Make changes to the same file (e.g., `file.txt`)
git commit -am "feature2"

git push origin feature2
```

**Workflow Overview**
- Create feature1 and feature2 branches and commit changes to both.
  - Push feature1, feature2 to GitHub and create a PR
- Create a pull request (PR) for feature1 to be merged into main.
- Merge feature1 into main and resolve any conflicts if they arise.
- Create a pull request for feature2.
- Resolve merge conflicts between feature2 and main (which now includes feature1)
  - it will Merge branch 'main' into feature2
  - & merge pull request 

```
git checkout main
git pull origin main
```

## Resolve merge conflicts on our computer
DO THIS STEP LOCALLY
- Merge branch 'main' into feature2
  ```
  git checkout feature2
  git merge main

  Resolve any merge conflicts

  git add .
  git commit
  git push origin feature2
  ```

--- 

### If You Add `README.md` to .gitignore After Tracking It?

If you add `README.md` to .gitignore after it has already been tracked, Git will continue tracking it, and you don't need to worry about .gitignore unless you remove it from tracking.

1. If `README.md` Is Already Tracked and Then Added to .gitignore:

Once a file like `README.md` has been added to the Git repository and is being tracked (i.e., it has been committed at least once), adding it to .gitignore will not stop it from being tracked. Git will continue to track it as normal.

2. What Happens If You Add `README.md` to .gitignore After Tracking It?

If `README.md` was already tracked, adding it to .gitignore will have no effect on the file—it will continue to be tracked by Git as it was before. However, it will not be staged for future commits unless you explicitly add it again (e.g., with git add).

3. If You Want to Stop Tracking a Previously Tracked File (e.g., `README.md`):

If you want Git to stop tracking a file that is already being tracked (like `README.md`), you'll need to remove it from the index (staging area) while leaving it in the working directory. This can be done with the following command:
```
    git rm --cached `README.md`
    git commit -m "Stop tracking `README.md`"
```
* --cached tells Git to stop tracking the file but leave it in your working directory (so it won't be deleted from your local file system).

**To stop tracking a file and also remove it from your filesystem:**
```
git rm README.md
```
* the file will be completely removed both from Git and from your working directory, and this will be reflected in the next commit.

**To stop tracking a file but keep it locally:**
```
git rm --cached README.md
```
* If you want to stop tracking a file but keep it in your working directory, you should use git rm --cached instead.



