Remote Repo, Local Repo
porcelain commands are built upon plumbing commands
git is a persistent map at its core, the next layer has git as a content tracker (like a file system)
 
Workspace reflects whatever is in our local repository. All changes you make happens in the workspace.
git clone – just clone to local machine from remote
git commit – copies changes from workspace to local repository
git push – push from local repo to remote repo. “–u origin” sets origin as the upstream remote
git pull – during push, if remote and local not in sync, then this will pull all changes from remote not in local repo
git pull - -rebase – will make sure all changes from local will be placed on top of all changes done in remote. Rebase will make branch look like this | -- | -- |, else it will look like this. | ------- | and below | -- | -- |
rebase will take the current branch and apply on top of the provided branch (master, if command is git rebase master) with new SHA1. Have to resolve conflicts thought.
A commit will have parent commit id too.
A reference is just a point to a commit Ex: Branch, HEAD
HEAD points to the branch you are on.
Index is also called the staging area. Index is a proposal for the next commit.
Merge is a commit that has two parents.
git –version à gives you the version of git running
git config –global user.name ‘name’
git config --l àlook at all config information
git config –system à system level
git config –global à user level
git config à repository level
git config --global help.autocorrect 1 à will autocorrect typos. 1 means wait 0.1 second before executing the correct command.
Git config –global core.autoclrf true|false|Input à true to convert carriage return to be compatible with all OS version. False means you are working on with windows. Input means only when its imported into repository and not the way out. All these actions are taken on text files only and not binary files.
to change editor type à git config –global core.editor emacs
initializing a git repository à git init or git init project
create a .git directory without a working directory using à git init --bare barerepo
display a graph of the entire history à git log –oneline –graph. Adding –decorate will add branch names, head, tag to the log.
GIT Configuration à 3 levels, system level, global level, local level
Using “alias” for commands like git config –global alias.lg ‘log –graph –online – decorate’
For abbreviated git status output use à git status –sb (s – summary, b – branch)
git diff  à shows the difference, git diff –cached shows the difference in staging
git commit –av à a means commit all and v means verbose. Shows the difference too.  M means add commit message
git add –patch à selective committing patches of code which are related.
Git add –u à option will add only updated files.
Git add –A à option will add all files.
 
.gitignore is a part of repository and will include files / directories you don’t want to track.
However, there is a exclude file (just for the user) in path .git/info/exclude which will exclude files from git itself.
Configure a global exludes file using git config core.excludesfiles.
Git branch <branchname> create the branch and git checkout <branchname> points the head to the branch. Instead of two command, we can try git checkout –b <branchname>
For merging, first checkout the branch and then merge it with master. Master changes will be merged into branch and branch will advance. However, master will not move. Now checkout master and merge again. Head, master and branch will be the same.
Branching models à top of trunk, master and topic, progressive stability
Git branch –a lists the remote branches too which are present in .git folder. The remote branches are present in packed-refs file.
Git branch –r shows only remote branches.
Git branch –no-merged will list branches which have not been merged or just –merged to say which ones have been merged
Git show <branchname> will show the difference between branch and before branch was created. Meaning what all changed in this branch.
Rename a branch name by using git branch –m <curr name> <new name>. use –d for delete. –D for force delete
git show –pretty=”” –name-only <hash-value> à no formatting but display only file names that changed in this branch
Git cherry-pick <commit id>. What this does is copies the changes for that commit and merges it to current head.
Git rebase master à takes all changes from current branch and applied these changes to master and progress the head and any other branch name from current branch. Does not move the master.
Rebase and merge are two ways to merge branch changes.
To continue rebasing, use git rebase –continue
Git distributed workflow à centralized, integration manager, dictator & lieutanants.
Git hosting à SSH server, internet hosts, on-premise hosts
Git remote –v à verbose remote listing
To add a new remote à git remote add <name> <url>
Git checkout <brachname> - from the remote it pulls the branch and tracks it and also switches to it.
Git push –all <backup repository name> à this will backup the current branch onto a new bare repository.
Git fetch à without branch name will update the current branch with remote branch. However contents will not be updated, you will have to do a merge to origin/master
Git pull à if in remote the branch has diverged  then just use pull, instead of fetch and merge
Git branch –set-upstream master origin/master à will set the remote from which pull should default take the changes.
Git pull –rebase à instead of merge, it will do rebase. Gives a linear output, instead of create branches.
Git commit –am “message” à can add and commit at the same time
Git tag –s v1.0_signed à allows to verify who tagged it.  Use –v option on tag to check if its verified
When you do git push we need to provide origin and branch. But if we want to link it permanently, then give option flag –u. thereafter just use git push.
Tagging commit id is done as à git tag tagname
Git tag –a mytag –m “I love cheese” à this is an annotated tag. (tag with message). Tag cannot move, branches can.
To push all tags to remote use, git push origin –tags or pushing just one, instead of –tags, use tagname
If by mistake you have changes the file but not committed it, you can just use git checkout <filename>
If you have staged a file (using add command), use git reset head <filename> to un-stage it. Git reset –hard to go back to HEAD and ignore all changes. Git reset –soft HEAD~1 will move head back and get the working folder updated too.
If you already committed, but missed to include a file, then stage it first and then use git commit –amend. This will amend the last commit and add this file.
Use rebase to merge multiple local commits into single commit before pushing. Use squash.
git show –stat – will show the difference in last commit
git show --pretty="" --name-only SHA1 à shows the files which were committed as part of this SHA1
git internals
git cat-file –t <hashvalue> à will tell you what type of object it is. It can be tree, blob, commit, tag annotation. use –p switch to show the contents.
tree .git/refs à will give you all the reference. These are however loose references as it might not reflect what actually in the remote. Master branch file is in .get/refs/heads.
Less .git/packed-refs à all references which came down from repository when I cloned it.
Sometime there are symbolic refs, ex: cat .git/HEAD à this lists down name of another ref.
To Undo merges, first option is to use revert. Git revert head –m 1. This will move head to one level before where head was. 2 means head will move to the branch which was merged (usually not the head). Introduces a new commit. However, the branch which was merged is lost. So other option is to use reset
Git reset –hard <commit id> - will move the points to commit id and updates index and working directory
git checkout –p à checkout a patch from the difference
git checkout –f à will force the working directory to revert to original state. However, only tracked files get changes. New files / directories, will not be reverted.
Git clean -f à force remove untracked files. However, to clean directories use, git clean –fd. This still does not remove the ignored files, then use git clean –fdx. –n for safe preview. Limit cleaning to a directory provide a directory name too.
Git clean –idx means interactively clean files.
Git reset –soft HEAD~ à moved head to parent commit, ~ means parent
Git reset –mixed HEAD~ à moved head to parent and well as update index with last commit
Git reset –hard HEAD~ à moved head to parent and well as update index with last commit and well as working directory. No backup is taken for working directory, so be careful.
Git log -1 à start log from HEAD and displays one commit
Git log -1 <branchname> or <hash value> à starts from branch and displays one commit
Git lg1 HEAD^1 à gives parent to the left
Git lg1 HEAD^2 à gives parent to the right
After ^, if you want to advance further then use ~. ^ just gives the branch but to advance, use ~
Git lg master..featureA à gives all commits in featureA which is not visitable from master branch
Git diff master..featureA à shows differences of all commits in featureA which is not visitable from master branch. Tell you what will change is merge happens.
The above is 2 dot notation
Git lg master…featureA à gives what is reachable from each branch but not both
Git lg master…featureA –left-right à option makes its more use saying which commit / side is in which branch. Tell what diverged.
This is 3 dot notation
Update history
Git filter-branch –env-filter ‘GIT_AUTHOR_NAME=Me’ HEAD~10..HEAD à this changes last 10 commits on master branch name. but the refs are not lost entirely, they are present in original folder which gets newly created.
Git filter-branch –f –tree-filter ‘rm –rf package.json’ -- --all à force to ignore original folder already created, remove package.json reference from the repository and then deletes the file. All specifies to apply on all commits.
Git filter-branch –f –subdirectory-filter script –prune-empty -- --all à make the script direct as the root directory and update all references across the repository. Prune empty will leave those commits those does not introduce any changes, means there are changes which does not touch files in script directory.
Interactive rebasing using –i option àgit rebase -i master.
git rebase -i HEAD~3 à Use this to change the commit message of 3 steps.
In git shell, tab completion saves time. Use as à . contrib/completion/git-completion.bash à this one take the bash script and run it on the command line.
Export PS1=’foo ’ à changes the prompt
Export GIT_PS1_SHOWDIRTYSTATE=1 à if I changes any file in the repository, then * will show in prompt
Export PS1=’\w$(__git_ps1 “(%s)”)\$ ‘ à changes the command line to show current directory short version and also the current branch.
Zsh is more powerful à super charge your terminal look at oh-my-zsh
Reflog à git reflog featureA à gives you all places where featureA was committed. Similar you can do for HEAD, in case you want to get SHA after a branch has been deleted
If we want to move to this commit, then use git rebase –hard featureA@{1
Reflog is stored in .git/logs/ à they are local
Gem install git-smart à install smart-pulls, which will do merges.
Gem install omglog à shows commit graph with live updating as commits are made, merged and branched. It’s a ruby code.
Git reflog shows only you commits, which reduces the amount of history shown. It’s a short history.
Gbrt – show git branches sorted by time (copy of code can be found on peepcode)
Git status –short à gives a short status
Git add –update à stage all changes from tracked files
When correcting conflicts, search for merge conflicts markers <<< or >>> like grep –r’<<<<’ * or >>>>
Enhanced git prompt info à ~/bin/git_cwd_info
Git checkout –B <branch> <SHA> àcreate a new branch to the SHA. Override existing branch.
Git push :branch-name à delete a remote branch
Git log –patch filename à shows all the commits happened to this file or directory
Git stash or git stash pushà record the current status of the working directory and index and stash it to html file.
git stash list à to list all stashes
git stash show à to inspect a stash
git stash apply à to apply stash onto different commit
Git stash pop à same as apply but will also remove it from the listing.
Git stash branch <branchname> -> it would create a new branch and apply the stash to it. It will also pop.
echo “apple pie” | git hash-object –stdin   à this prints out SHA1. If included –w option, then the content will be written to a file with the SHA1 hash.
Contents of a SHA1 commit, has just the commit message and the reference to the SHA1 of the object. Since the commit message has different content, the SHA1 will be different. However, the references from commit’s SHA1 will have same SHA1
Contents of commit SHA1 will also have parent commit SHA1
Git count-object will give number of objects in the git directory
Detached HEAD is something where you point the head to the commit id rather than the branch (ex: master) git checkout <sha1>. You can continue make commits, and HEAD moved. But when you checkout back to master. Then HEAD moves back. The commits cannot be reached unless you have noted down their SHA1
GIT’s garbage collecter will look at commits which cannot be reached by branch, head and tag, and then it will remove it. In order to save that work, you can make that commit as a branch. GC now no longer can delete it.
Git show-ref master à will show commits have master in them and which commits they are pointing at.
B4 you do push, first you fetch from remote, do merges and then push. Fetch and merge is combined and called pull.
Never do rebase when it’s a shared repository. People will have conflicts during merges and would not know what happened.
When working on somebody else github repository, you can fork it to your account so that you can make changes and push changes from local. The main repository can be tagged as upstream so that you can fetch changes from there, do merges into local and push it to your github repository.
Pull request is not a git feature but a github feature. It’s an email sent to main account and they can choose to merge it.
Git shortlog – to display authors in asc order of name
Git shortlog –sne – to display authors summary, numeric decreasing of commits and email.
Git can use http(s)(80,443), git(9418), ssh(22) and file(for local)
For resolving conflicts with merge, can use GUI called mergetool. Use git mergetool.
To delete a remote branch, do à git push origin :v1.0_fix_remote_branch name. to copy the current branch into a remote branch with a different name, the fill in the current branch name before the :
Show only  tracked files à git ls-tree --full-tree --name-only -r HEAD
