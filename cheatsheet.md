* First, generate an ssh key for access. Then, do work

Check for bitbucket here https://support.atlassian.com/bitbucket-cloud/docs/set-up-an-ssh-key/

* For cloning repo with specified branch

` git clone --single-branch --branch <branchname> <remote-repo> `

* For downloading submodules later,

` git submodule update --init --recursive `

* For downloading repo with submodules (Preferred)

` git clone --recurse-submodules -j8 git://github.com/foo/bar.git `

* To remove a submodule you need to:

Delete the relevant section from the .gitmodules file.
Stage the .gitmodules changes git add .gitmodules
Delete the relevant section from .git/config.
Run git rm --cached path_to_submodule (no trailing slash).
Run rm -rf .git/modules/path_to_submodule (no trailing slash).
Commit git commit -m "Removed submodule "
Delete the now untracked submodule files rm -rf path_to_submodule

* Creating new branch from another and switch to that

` git checkout -b <new-branch> `

` git checkout -b <new-branch> <existing-branch> `

* remove changes and delete files

` git clean -df `

* Creating new repo and move to remote server(github/bitbucket)

```
git init 
git add .
git commit 

git remote add origin git@bitbucket.org:MayankB98/unitybroker.git --your repo
git remote -v
git push -u origin master
```

* creating new branch from earlier commit id and switch to that

` git checkout -b new_branch commit_id `

* if you want to undo the local commit but dont change anything with files

` git reset --soft HEAD~1 `

* to merge changes from another branch, if it is n commits behind anotherbranch(dev/master/main)

` git checkout currentbranch `
` git merge anotherbranch `		

* to resolve conflict

do changes
` git commit `
` git push `

* Remove untracked files

` git clean -fd `

* Remove untracked files (including the ones in gitignore)

` git clean -xfd `

* Switch to remote branch

` git checkout --track origin/feature/StateSynchronization `

* revert unstaged files

` git restore . `

* get current commid hash

` git rev-parse HEAD `

* pulling changes

` git pull `

* pulling submodules

` git pull --recurse-submodules `

* pulling for all branches

` git pull --all `

* add submodule

` git submodule add --name sv git@bitbucket.org:gridrasterproduct/mixedreality-spectatorview.git sv `(this_is_path_remove this bracket)

* Skip smudge for lfs

// Skip smudge - We'll download binary files later in a faster batch
` git lfs install --skip-smudge `
// Reinstate smudge
` git lfs install --force `

* if you want to undo the commit changes, better to commit this undo to have record and this is done by revert not reset

` git revert <commit-id> `

* reverting multiple commits	(A <-- B  <-- C <-- D) [A <-- B  <-- C <-- D <-- [(BCD)-1]] [(BCD)-1 = D-1 C-1 B-1]

```
git revert --no-commit D
git revert --no-commit C
git revert --no-commit B
git commit -m "message for all"
```

* to checkout some files from some commit id

` git checkout <commit-id> <path> `

* to checkout some files from some branch

` git checkout <branch-name> -- <path> `

* gitignore ignores the untracked files but committed files it still commits and not ignore. To ignore them,

` git rm -r --cached . `     -> to make git forget.
` git add . ` and ` git commit ` to commit this ignoring

* updating repo ref for merge and other things

` git remote show origin `
` git remote update --prune `

* to check file status of commits 

` git log --stat `

* to change last commit message

` git commit --amend -m "New commit message." `

* to do same command in all submodules

` git submodule foreach --recursive <command> `
eg: ` git submodule foreach --recursive git checkout . `

* to check gitignore files in status

` git status --ignored `

* Execute multiple commands together

` git restore --staged . && git checkout . `

* Checking which commits changes the specific file

` git log -- <filepath> `

* Get the deleted file back

` git checkout <deleted commit hash>~1 -- <filepath> `

* Repeat command for all submodules

` git submodule foreach --recursive <command> `

* For saving changes temporarily

` git stash `

* For getting temporarily changes stashed earlier

` git stash pop`

* For saving unstashed changes temporarily

` git stash --keep-index`

* For resolving merge conflicts

` git mergetool`

* For resolving binary merge conflicts

` git checkout --ours -- path/to/conflicted-file.txt `
