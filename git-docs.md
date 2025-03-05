- [Add an existing project to GitHub from command line](#add-existing-project)
- [Clone a remote git repository on your local machine](#clone-remote-repository)
- [Git commands](#gitcommandsheading)
    - [pull from remote branch (main)  to local (origin)](#pull-from-main-to-local)
    - [pull from remote branch (test-branch)  to local (origin)](#pull-from-remote-branch)
    - [create new branch](#create-new-branch)
    - [switch to another branch](#switch-to-another-branch)
    - [push a new local branch to remote git repository](#push-new-local-branch)
    - [push from local branch (origin) to remote branch (test-branch)](#push-from-local-branch)
    - [merge local branch with main](#merge-local-branch-with-main)
    - [rename local branch](#rename-local-branch)
    - [delete file from git repository](#delete-file-from-repository)
    - [delete directory from git repository](#delete-directory-from-repository)
    - [create git branch from another branch](#create-branch-from-another-branch)
    - [merge two local branches](#merge-local-branches)
    - [git add all](#gitadd-all)
    - [undo git add](#undo-gitadd)
    - [undo all files that were added](#undo-all-added-files)
    - [remove all local untracked files](#removeall-local-untracked-files)
    - [unstage a staged file](#unstage-staged-file)
    - [revert uncommited changes](#revert-un-commited-changes)
    - [undo file delete](#undo-file-del)
    - [Delete local branch](#del-loc-branch)
    - [Delete remote branch](#del-rem-branch)
    - [Show history of changes on a file](#show-file-change-history)
    - [Change commit message](#change-commit-msg)
    - [See the remote repository your project is pointing to](#show-remote-repository)
    - [Stage a file for removal](#stage-file-for-removal)
    - [Remove all version tracking from a projects directory](#remove-all-version-tracking-info)
    - [Find hash of branch](#find-hash-branch)
    - [Revert a git merge](#revert-git-merge)
    - [Stash changes](#stash-the-changes)
    - [Fetch command](#fetch)
    - [Rebase command](#rebase)
    - [Cherry pick commits](#cherrypick)
    - [Deploy static website](#deploy-static-site)


### Add an existing project to GitHub from command line: <a name="addexistingproject"></a>
https://help.github.com/en/articles/adding-an-existing-project-to-github-using-the-command-line

Create a new repository on GitHub   
https://github.com/test-user?tab=repositories

Open terminal and change the current working directory to your local project

1. git init
2. git commit -m "first commit"
3. git remote add origin git@github.com:test-user/test_project.git
4. git push -u origin master

In step 3 the URL can be obtained from the GitHub repositories Quick Setup page. Copy the ssh link which has this format:
git@github.com:test-user/test_project.git

(Do not use the https url. You will be asked to enter username and password with the https url)

verify new remote url
git remote -v


### Clone a remote git repository on your local machine: <a name="cloneremoterepository"></a>


git clone <remote_repo>

        git clone -b <branch> <remote_repo>

Example

        	git clone -b develop git@github.com:user/myproject.git


https://coderwall.com/p/y7hf6w/how-to-clone-a-specific-branch-in-git



### Git commands: <a name="gitcommandsheading"></a>

###### pull from remote branch (main)  to local (origin): <a name="pull-from-main-to-local"></a>

	git pull origin master

###### push from local branch (origin) to remote branch (main)

	git push origin main

###### create new branch: <a name="create-new-branch"></a>

	git checkout -b test-branch-1

###### switch to another branch: <a name="switch-to-another-branch"></a>

	git checkout test-branch-2

###### push a new local branch to remote git repository: <a name="push-new-local-branch"></a>

	git push -u origin test-branch-2

###### pull from remote branch (test-branch)  to local (origin): <a name="pull-from-remote-branch"></a>

	git pull origin test-branch

###### push from local branch (origin) to remote branch (test-branch): <a name="push-from-local-branch"></a>

	git push origin test-branch

###### merge local branch with main: <a name="merge-local-branch-with-main"></a>

	git checkout main
	git pull origin main
	git merge test-branch

###### rename local branch: <a name="rename-local-branch"></a>
if you are on the branch you want to rename:

		git branch -m new-name

if you are on a different branch

		git branch -m old-name new-name

###### delete file from git repository: <a name="delete-file-from-repository"></a>

	git rm file.txt

###### delete directory from git repository: <a name="delete-directory-from-repository"></a>

	git rm -r folder-name


###### create git branch from another branch: <a name="create-branch-from-another-branch"></a>

If you want to create a new branch branch2 from existing branch branch1

	git checkout branch1
	git checkout -b branch2 branch1 

###### merge two local branches: <a name="merge-local-branches"></a>
https://stackoverflow.com/questions/25053697/git-merge-two-local-branches/25053738
If you have branch main, branch1 and branch2. To merge branch2 into branch1

    git checkout branch1
    git merge branch2

###### git add all: <a name="gitadd-all"></a>

Stage all files in your repository, which includes all new, modified and deleted files.

    git add -A
or

    git add --all

Add all files under folder vendor

    git add -A vendor

###### undo git add: <a name="undo-gitadd"></a>

	git reset <file_name>

###### undo all files that were added: <a name="undo-all-added-files"></a>

	git reset	

###### remove all local untracked files: <a name="removeall-local-untracked-files"></a>
remove all local untracked files (local changes that have not yet been commited) from a dir, so only git tracked files remain

    git clean -fd <some-dir>

    options:
    -d  recurse into untracked directories. -d is irrelevant if any paths are specified.
    -f  --force
    -i  --interactive Show what would be done and clean files interactively
    -n  --dry-run show what would be done. Don't actually remove anything

###### unstage a staged file: <a name="unstage-staged-file"></a>
(staged file is a file that has been added but not commited)

    git restore --staged <file_name> 

###### revert uncommited changes: <a name="revert-un-commited-changes"></a>
Revert uncommitted changes only to particular file or directory:

    git checkout [some_dir|file.txt]

###### undo file delete: <a name="undo-file-del"></a>

    git checkout HEAD <filename>

Restoring file delete: https://www.git-tower.com/learn/git/faq/restoring-deleted-files/

###### Delete local branch: <a name="del-loc-branch"></a>
The local branch should not be current while deleting it. Switch to some other branch before deleting it.

	git branch -d <branch_name>

###### Delete remote branch: <a name="del-rem-branch"></a>

	git push origin --delete <branch_name>

###### Show history of changes on a file: <a name="show-file-change-history"></a>

	git annotate <file-name>

###### Change commit message (when commit has not been pushed online): <a name="change-commmit-msg"></a>

	git commit --amend
press Enter. In the vi editor edit the commit message and save

###### See the remote repository your project is pointing to: <a name="show-remote-repository"></a>

 	git remote -v

###### Stage a file for removal: <a name="stage-file-for-removal"></a>
file is not removed from the working dir. The file will then be shown as untracked.

    untrack all files
 	    git rm -r --cached .
 	    
 	untrack specific file
 	    git rm --cached foo.txt

###### Remove all version tracking from a projects directory: <a name="remove-all-version-tracking-info"></a>

    rm -rf .git

###### Find hash of branch: <a name="find-hash-branch"></a>

    git rev-parse <branch>
    
    example: 
        git rev-parse main
        17f2303133734f4b9a9aacfe52209e04ec11aff4

###### Revert a git merge <a href="https://mijingo.com/blog/reverting-a-git-merge" target="_blank">(link)</a><a name="revert-git-merge"></a>

    Example: 
    1. find hash of the branch you want to revert 
        git rev-parse main
        17f2303133734f4b9a9aacfe52209e04ec11aff4
    
    2. Use the hash to revert a merge
        git revert -m 1 17f2303133734f4b9a9aacfe52209e04ec11aff4

#### Stash changes:<a name="stash-the-changes"></a>

If you want to temporarily remove the changes from your working directory and apply them later, you can stash them:

Do this in current_branch

    git stash
    git checkout <other_branch>

Return back to current_branch

    git stash apply

List what is in stash

	git stash list


#### Fetch command:<a name="fetch"></a>
Fetch a single branch

	git fetch origin test-branch


Create a new local branch test-branch to track the remote branch origin/test-branch and switch to the newly created local branch test-branch

If you were in main when you ran this command, the content of test-branch will match the content of origin/test-branch. It does not bring any changes from the main branch.

	git checkout -b test-branch origin/test-branch


list local and remote branches

	git branch -vv

Fetch all remote branches:

	git fetch origin

This ensures that your local Git repository is aware of all branches on the remote repository

Create and switch to the new local branch: You can create a new branch locally and set it to track the remote test-branch by using git checkout -b

	git checkout -b test-branch origin/test-branch

Verify the branch

	git branch -vv


### Rebase:<a name="rebase"></a>

Rebase local branch on to main

    git checkout main
    git pull origin main
    git rebase test-branch

Set git to use rebase by default for current directory:

	git config pull.rebase true

You can verify wether the default is set to merge or rebase in your git directory:

	git config --get pull.rebase

If it returns true, rebase is enabled; if false, merge is used.


To set rebase globally

	git config --global pull.rebase true


### Cherry pick:<a name="cherrypick"></a>

Example workflow for git cherry-pick

Switch to the target branch
  
    git checkout test-branch

List commits on the main branch to find the ones you want

    git log main

Cherry-pick a specific commit

    git cherry-pick abc1234

Cherry-pick multiple commits

    git cherry-pick def5678 ghi9012

Resolve any conflicts (if prompted) and continue

    git cherry-pick --continue

##### Deploy your static website with <a href="https://pages.github.com/" target="_blank">Github Pages</a><a name="deploy-static-site"></a>

    Push your static website to a git repository

    Go to the settings page of your repository and scroll to the bottom where it says Danger Zone. Change the visibility to public. 

    Scroll down to the GitHub Pages section and chose the source branch. (example - main). Select folder root and click "Save" button.

    A message with a url where your site is published at will appear under the GitHub Pages section of the settings page.

    Enter the URL link in a browser to launch your static website.
