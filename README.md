# RepoNo4

Branching, Merging and Feature Branch Workflow

### Branching

"When working with Git, you can create a separate branch from the main branch. Instead of adding commits directly to the main branch, you add them to the new branch. The advantage of this approach is that you can make multiple commits for your feature or changes without affecting the main branch. This allows you to work independently on the feature, and once it's ready, you can merge it back into the main branch."

"Instead of adding commits directly to the main branch, you add them to this new branch. This is beneficial whether you're working on a new feature or a bug fix."


#### If You Add `README.md` to .gitignore After Tracking It?

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