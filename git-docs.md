- [Add an existing project to GitHub from command line](#addexistingproject)
- [Clone a remote git repository on your local machine](#cloneremoterepository)
- [Git commands](#gitcommandsheading)



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



###### pull from remote branch (master)  to local (origin)

	git pull origin master

###### push from local branch (origin) to remote branch (master)

	git push origin master

###### create new branch

	git checkout -b test-branch-1

###### switch to another branch

	git checkout test-branch-2

###### push a new local branch to remote git repository

	git push -u origin test-branch-2

###### pull from remote branch (test-branch)  to local (origin)

	git pull origin test-branch

###### push from local branch (origin) to remote branch (test-branch)

	git push origin test-branch

###### merge local branch with master:

	git checkout master
	git pull origin master
	git merge test-branch

###### rename local branch
if you are on the branch you want to rename:

		git branch -m new-name

if you are on a different branch

		git branch -m old-name new-name

###### delete file from git repository

	git rm file.txt

###### delete directory from git repository

	git rm -r folder-name


###### create git branch from another branch

If you want to create a new branch branch2 from existing branch branch1

	git checkout branch1
	git checkout -b branch2 branch1 

###### merge two local branches
https://stackoverflow.com/questions/25053697/git-merge-two-local-branches/25053738
If you have branch Master, branch1 and branch2. To merge branch2 into branch1

    git checkout branch1
    git merge branch2

###### git add all

Stage all files in your repository, which includes all new, modified and deleted files.

    git add -A
or

    git add --all

Add all files under folder vendor

    git add -A vendor

###### undo git add

	git reset <file_name>

###### undo all files that were added

	git reset	

###### remove all local untracked files
remove all local untracked files (local changes that have not yet been commited) from a dir, so only git tracked files remain

    git clean -fd <some-dir>

    options:
    -d  recurse into untracked directories. -d is irrelevant if any paths are specified.
    -f  --force
    -i  --interactive Show what would be done and clean files interactively
    -n  --dry-run show what would be done. Don't actually remove anything

###### unstage a staged file
(staged file is a file that has been added but not commited)

    git restore --staged <file_name> 

###### revert uncommited changes
Revert uncommitted changes only to particular file or directory:

    git checkout [some_dir|file.txt]

###### undo file delete

    git checkout HEAD <filename>

Restoring file delete: https://www.git-tower.com/learn/git/faq/restoring-deleted-files/

###### Delete local branch
The local branch should not be current while deleting it. Switch to some other branch before deleting it.

	git branch -d <branch_name>

###### Delete remote branch

	git push origin --delete <branch_name>

###### Show history of changes on a file

	git annotate <file-name>

###### Change commit message (when commit has not been pushed online)

	git commit --amend
press Enter. In the vi editor edit the commit message and save

###### See the remote repository your project is pointing to

 	git remote -v

###### Stage a file for removal
file is not removed from the working dir. The file will then be shown as untracked.

    untrack all files
 	    git rm -r --cached .
 	    
 	untrack specific file
 	    git rm --cached foo.txt

###### Remove all version tracking from a projrcts directory

    rm -rf .git

###### Find hash of branch

    git rev-parse <branch>
    
    example: 
        git rev-parse master
        17f2303133734f4b9a9aacfe52209e04ec11aff4

###### Revert a git merge <a href="https://mijingo.com/blog/reverting-a-git-merge" target="_blank">(link)</a>

    Example: 
    1. find hash of the branch you want to revert 
        git rev-parse master
        17f2303133734f4b9a9aacfe52209e04ec11aff4
    
    2. Use the hash to revert a merge
        git revert -m 1 17f2303133734f4b9a9aacfe52209e04ec11aff4






[Revert a Git Merge]: https://mijingo.com/blog/reverting-a-git-merge

##### Deploy your static website with <a href="https://pages.github.com/" target="_blank">Github Pages</a>



    Push your static website to a git repository

    Go to the settings page of your repository and scroll to the bottom where it says Danger Zone. Change the visibility to public. 

    Scroll down to the GitHub Pages section and chose the source branch. (example - master). Select folder root and click "Save" button.

    A message with a url where your site is published at will appear under the GitHub Pages section of the settings page.

    Enter the URL link in a browser to launch your static website.


