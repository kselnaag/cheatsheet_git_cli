# **My git CLI sheatsheet for everyday usage.**

## BASICS
```
git clone $REPO					- copy existing repo
git init					- init empty repo
git commit --allow-empty -m "Initial commit"	- you first commit
git status					- show local folder changes
git log --graph --oneline --all 		- show all local commits in tree
git add .					- add all in current folder
git rm $FILE					- delete file in stage
git commit --amend				- change last local commit
git diff					- show changes after adding in stage
git tag 					- show local tags
git tag -a $LABEL -m $DESCRIPTION	        - set the TAG
git show HEAD					- show diff in commit
```
## JUMPS
```
git checkout .					- rebuild local folder with last commit
git checkout $FOLDER				- in subfolder
git checkout -b $BRANCH $REPO			- create branch and switch here

git reset HEAD~3				- go to 3 commit backwards
git reset HEAD^2			        - go to 2-nd parent
```
## REMOTES
```
git remote --verbose				- show remote repos
git remote remove $REPO				- delet remote repo link
git remote set-head $REPO $BRANCH		- seting default remote tracking branch
git remote add $NAME $REPO			- link local to remote repo
```
## BRANCHES
```
git branch 					- show local branches
git branch -d|D $BRANCH				- delete $BRANCH label (-D - force delete)
git branch -f $BRANCH $COMM			- relocate $BRANCH to commit $COMM
git branch -m $NEW_BRANCH			- rename
git branch -r					- show remote branches
git branch --all				- show local and tracking branches
git branch -u $REM_BRANCH $BRANCH		- link to remote branch
```
## MERGES
```
git merge $BRANCH			- merge branche to current with new commit
git merge --no-ff $BRANCH		- without fast-forwarding
git merge --squash $FEATUREX		- merge with squash side branch (staged area, commit after)

git cherry-pick $COMM1 $COMM2		- coherently move some commits in current branch

git rebase --continue			- after fixing conflicts and ADD
git rebase --abort			- abort rebase operatoin
git rebase $BRANCH $FEATUREX        	- rebase featureX to branch top 
                                        	(if $BRANCH only - rebase current branch)
git rebase -i $COMM			- interactive rebase for all childrens in current branch
```
## GET FROM SERVER
```
git fetch $REPO $BRANCH			- syncronize with remote repo
git fetch $REPO $BRANCH:$NAME2		- syncronize with renaming

git pull --rebase			- get remote changes (with rebase)
git pull $REPO <src>:<dst>          	- pull is 2 operations worked with <src> and <dst> branches
	=
	git fetch $REPO <src>:<dst>
	+
	git merge <dst>
git pull $REPO :<dst>			- delete localy when copy "none" branch
```
## SET TO SERVER
```
git push --set-upstream $REPO $BRANCH   	- set your commits to the remote repo
git push $REPO <src>:<dst>		        - set src-branch in created dst-branch
git push -u $REPO $BRANCH               	- set to remote repo (repo link + branch)
git push --tags                                 - set tags to remote repo
git push $REPO --delete $BRANCH                 - delete branch in repo
git push $REPO :<dst>				- delete on server when copy "none" branch
```
## CONFIGS
```
git config --global user.name $NAME                     - set username(--system|--global|--local)
git config user.name                                    - get username
git config --global user.email $EMAIL                   - set email
git config --global core.editor $EDITOR                 - set editor
git config --global credential.helper libsecret         - save login|pass in encrypted file
    || git config --global credential.helper store	- opened file
    || git config --global credential.helper "cache --timeout=86400")	
    							- temp memory in secs, 24 hours
```
## BASH
With `nano ~/.bashrc` do:
```
alias glog='git log --graph --oneline --all'
alias gch='git checkout'
alias gst='git status'
```
Then `source ~/.bashrc`.
## GITFLOW

![gitflow scheme](https://raw.githubusercontent.com/kselnaag/git_CLI_cheatsheet/master/gitflow.png "gitflow scheme")

----
## Links:
[ProGit](https://git-scm.com/book/ru/v2 "git book") | [learngitbranching.js.org](https://learngitbranching.js.org/?locale=ru_RU "git game") | [dillinger.io](https://dillinger.io "MD-editor")
