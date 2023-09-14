---
title: git wiki
excerpt: Commits are shown in green as 5-character IDs, and they point to their parents. Branches are shown in orange, and they point to particular commits. The current branch is identified by the special reference HEAD, which is "attached" to that branch. In this image, the five latest commits are shown, with ed4
---

![Alt text](</assets/images/git wiki/image-1.png>)

Commits are shown in green as 5-character IDs, and they point to their parents. Branches are shown in orange, and they point to particular commits. The current branch is identified by the special reference HEAD, which is "attached" to that branch. In this image, the five latest commits are shown, with ed489 being the most recent. main (the current branch) points to this commit, while stable (another branch) points to an ancestor of main's commit.

How does Git know what branch you’re currently on? It keeps a special pointer called HEAD.

## git basic

Typically, you’ll want to start making changes and committing snapshots of those changes into your repository each time the project reaches a state you want to record.

each file in your working directory can be in one of two states: tracked or untracked.

Tracked files are files that were in the last snapshot, as well as any newly staged files; they can be unmodified, modified, or staged.In short, tracked files are files that Git knows about.

Untracked files are everything else — any files in your working directory that were not in your last snapshot and are not in your staging area. When you first clone a repository, all of your files will be tracked and unmodified because Git just checked them out and you haven’t edited anything.

As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.

![Alt text](</assets/images/git wiki/image.png>)

- Checking the Status of Your Files
The main tool you use to determine which files are in which state is the git status command. If you run this command directly after a clone, you should see something like this:

```bash
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   _posts/category level1/category level2/git wiki.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   _posts/category level1/category level2/temp002.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        assets/images/git wiki/
```

- Tracking New Files
In order to begin tracking a new file, you use the command git add. To begin tracking the README file, you can run this:

`$ git add README`

- Staging Modified Files

“Changes not staged for commit” — which means that a file that is tracked has been modified in the working directory but not yet staged. To stage it, you run the git add command.

git add is a multipurpose command — you use it to begin tracking new files, to stage files, and to do other things like marking merge-conflicted files as resolved. It may be helpful to think of it more as “add precisely this content to the next commit” rather than “add this file to the project”.

Git stages a file exactly as it is when you run the git add command. If you commit now, the version of CONTRIBUTING.md as it was when you last ran the git add command is how it will go into the commit, not the version of the file as it looks in your working directory when you run git commit. If you modify a file after you run git add, you have to run git add again to stage the latest version of the file:

- Ignoring Files
Often, you’ll have a class of files that you don’t want Git to automatically add or even show you as being untracked. These are generally automatically generated files such as log files or files produced by your build system. In such cases, you can create a file listing patterns to match them named .gitignore.

Setting up a .gitignore file for your new repository before you get going is generally a good idea so you don’t accidentally commit files that you really don’t want in your Git repository.

---

The rules for the patterns you can put in the .gitignore file are as follows:

Blank lines or lines starting with # are ignored.

Standard glob patterns work, and will be applied recursively throughout the entire working tree.

You can start patterns with a forward slash `/` to avoid recursivity.

You can end patterns with a forward slash `/` to specify a directory.

You can negate a pattern by starting it with an exclamation point `!`.

```gitignore
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

- Viewing Your Staged and Unstaged Changes
If the git status command is too vague for you — you want to know exactly what you changed, not just which files were changed — you can use the git diff command.

- Committing Your Changes
Now that your staging area is set up the way you want it, you can commit your changes. Remember that anything that is still unstaged — any files you have created or modified that you haven’t run git add on since you edited them — won’t go into this commit. They will stay as modified files on your disk.

Alternatively, you can type your commit message inline with the commit command by specifying it after a -m flag, like this:

`$ git commit -m "Story 182: fix benchmarks for speed"`

- Removing Files
To remove a file from Git, you have to remove it from your tracked files (more accurately, remove it from your staging area) and then commit. The git rm command does that, and also removes the file from your working directory so you don’t see it as an untracked file the next time around.

If you simply remove the file from your working directory, it shows up under the “Changes not staged for commit”

Then, if you run git rm, it stages the file’s removal:

---

Another useful thing you may want to do is to keep the file in your working tree but remove it from your staging area. In other words, you may want to keep the file on your hard drive but not have Git track it anymore. This is particularly useful if you forgot to add something to your .gitignore file and accidentally staged it, like a large log file or a bunch of .a compiled files. To do this, use the --cached option:

$ git rm --cached README

You can pass files, directories, and file-glob patterns to the git rm command. That means you can do things such as:

`$ git rm log/\*.log`

Note the backslash `\` in front of the *. This is necessary because Git does its own filename expansion in addition to your shell’s filename expansion. This command removes all files that have the .log extension in the log/ directory.

- If you rename a file in Git, no metadata is stored in Git that tells it you renamed the file. However, Git is pretty smart about figuring that out after the fact

`$ git mv file_from file_to`

However, this is equivalent to running something like this:

$ mv README.md README
$ git rm README.md
$ git add README
Git figures out that it’s a rename implicitly, so it doesn’t matter if you rename a file that way or with the mv command.

you can use any tool you like to rename a file, and address the add/rm later, before you commit.

### github git vsCode proxy setting

1. vsCode setting

   ```yml
   "http.proxyAuthorization": null,
   "http.proxy": "http://127.0.0.1:8000",
   "https.proxy": "http://127.0.0.1:8000"
   ```

2. git bash command

   ```bash
   git config -global http.proxy http://127.0.0.1:8000
   git config -global https.proxy http://127.0.0.1:8000
   ```

## basic commands

![Alt text](</assets/images/git wiki/image-19.png>)

1. The four commands above copy files between the working directory, the stage (also called the index), and the history (in the form of commits).

- `git add` *files* copies files (at their current state) to the stage.
- `git commit` saves a snapshot of the stage as a commit.
- `git reset` -- *files* unstages files; that is, it copies files from the latest commit to the stage. Use this command to "undo" a git add files. You can also git reset to unstage everything.
- `git checkout -- *files*` copies files from the stage to the working directory. Use this to throw away local changes.

ou can use git reset -p, git checkout -p, or git add -p instead of (or in addition to) specifying particular files to interactively choose which hunks copy.

1. It is also possible to jump over the stage and check out files directly from the history or commit files without staging first.

![Alt text](</assets/images/git wiki/image-20.png>)

- `git commit -a` is equivalent to running git add on all filenames that existed in the latest commit, and then running git commit.
- `git commit *files*` creates a new commit containing the contents of the latest commit, plus a snapshot of files taken from the working directory. Additionally, files are copied to the stage.
`git checkout HEAD -- *files*` copies files from the latest commit to both the stage and the working directory.

### git diff

There are various ways to look at differences between commits. Below are some common examples. Any of these commands can optionally take extra filename arguments that limit the differences to the named files.

![Alt text](</assets/images/git wiki/image-18.png>)

### git commit

When you commit, git creates a new commit object using the files from the stage and sets the parent to the current commit. It then points the current branch to this new commit. In the image below, the current branch is main. Before the command was run, main pointed to ed489. Afterward, a new commit, f0cec, was created, with parent ed489, and then main was moved to the new commit.

![Alt text](</assets/images/git wiki/image-2.png>)

This same process happens even when the current branch is an ancestor of another. Below, a commit occurs on branch stable, which was an ancestor of main, resulting in 1800b. Afterward, stable is no longer an ancestor of main. To join the two histories, a merge (or rebase) will be necessary.

![Alt text](</assets/images/git wiki/image-3.png>)

Sometimes a mistake is made in a commit, but this is easy to correct with git commit --amend. When you use this command, git creates a new commit with the same parent as the current commit. (The old commit will be discarded if nothing else references it.)

![Alt text](</assets/images/git wiki/image-4.png>)

### git branch

git branch name will create a new branch named "name". Creating branches just creates a new tag pointing to the currently checked out commit.

### git checkout

git checkout has many uses, but the main one is to switch between branches.
For example, to switch from master branch to dev branch, I would type git checkout dev.

The checkout command is used to copy files from the history (or stage) to the working directory, and to optionally switch branches.

1. When a filename is not given but the reference is a (local) branch, HEAD is moved to that branch (that is, we "switch to" that branch), and then the stage and working directory are set to match the contents of that commit. Any file that exists in the new commit (a47c3 below) is copied; any file that exists in the old commit (ed489) but not in the new one is deleted; and any file that exists in neither is ignored.

![Alt text](</assets/images/git wiki/image-5.png>)

1. When a filename is not given and the reference is not a (local) branch — say, it is a tag, a remote branch, a SHA-1 ID, or something like main~3 — we get an anonymous branch, called a detached HEAD. This is useful for jumping around the history. Say you want to compile version 1.6.6.1 of git. You can git checkout v1.6.6.1 (which is a tag, not a branch), compile, install, and then switch back to another branch, say git checkout main. However, committing works slightly differently with a detached HEAD; this is covered below.

![Alt text](</assets/images/git wiki/image-6.png>)

1. When a filename (and/or -p) is given, git copies those files from the given commit to the stage and the working directory. For example, git checkout HEAD~ foo.c copies the file foo.c from the commit called HEAD~ (the parent of the current commit) to the working directory, and also stages it. (If no commit name is given, files are copied from the stage.) Note that the current branch is not changed.

![Alt text](</assets/images/git wiki/image-7.png>)

1. When HEAD is detached, commits work like normal, except no named branch gets updated. (You can think of this as an anonymous branch.)

![Alt text](</assets/images/git wiki/image-8.png>)

Once you check out something else, say main, the commit is (presumably) no longer referenced by anything else, and gets lost. Note that after the command, there is nothing referencing 2eecb.

![Alt text](</assets/images/git wiki/image-9.png>)

---
In addition to checking out branches, you can also checkout individual commits.

git checkout bb92e0e
git commit
Not a good idea to make commits while in a detached HEAD state.

git checkout bb92e0e
git branch branchname1
git commit

---

You can combine git branch and git checkout into a single command by typing git checkout -b branchname. This will create the branch if it does not already exist and immediately check it out.when you commit, the HEAD is the new branch.

## undo commit

### git reset

git reset will move HEAD and the current branch back to wherever you specify, abandoning any commits that may be left behind. This is useful to undo a commit that you no longer need.

This command is normally used with one of three flags: "--soft", "--mixed", and "--hard". The soft and mixed flags deal with what to do with the work that was inside the commit after you reset, and you can read about it here. Since this visualization cannot graphically display that work, only the "--hard" flag will work on this site.

The ref "HEAD^" is usually used together with this command. "HEAD^" means "the commit right before HEAD. "HEAD^^" means "two commits before HEAD", and so on.

!!Note that you must never use git reset to abandon commits that have already been pushed and merged into the origin. This can cause your local repository to become out of sync with the origin. Don't do it unless you really know what you're doing.

---

The reset command moves the current branch to another position, and optionally updates the stage and the working directory. It also is used to copy files from the history to the stage without touching the working directory.

If a commit is given with no filenames, the current branch is moved to that commit, and then the stage is updated to match this commit. If --hard is given, the working directory is also updated. If --soft is given, neither is updated.

![Alt text](</assets/images/git wiki/image-10.png>)

If a commit is not given, it defaults to HEAD. In this case, the branch is not moved, but the stage (and optionally the working directory, if --hard is given) are reset to the contents of the last commit.

![Alt text](</assets/images/git wiki/image-11.png>)

### git revert

To undo commits that have already been pushed and shared with the team, we cannot use the git reset command. Instead, we have to use git revert.

git revert will create a new commit that will undo all of the work that was done in the commit you want to revert.

![Alt text](</assets/images/git wiki/image-12.png>)

## combine branches

### git merge

git merge will create a new commit with two parents. The resulting commit snapshot will have the all of the work that has been done in both branches.

If there was no divergence between the two commits, git will do a "fast-forward" method merge.

A merge creates a new commit that incorporates changes from other commits. Before merging, the stage must match the current commit. The trivial case is if the other commit is an ancestor of the current commit, in which case nothing is done. The next most simple is if the current commit is an ancestor of the other commit. This results in a fast-forward merge. The reference is simply moved, and then the new commit is checked out.

![Alt text](</assets/images/git wiki/image-13.png>)

Otherwise, a "real" merge must occur. You can choose other strategies, but the default is to perform a "recursive" merge, which basically takes the current commit (ed489 below), the other commit (33104), and their common ancestor (b325c), and performs a three-way merge. The result is saved to the working directory and the stage, and then a commit occurs, with an extra parent (33104) for the new commit.

![Alt text](</assets/images/git wiki/image-14.png>)

"git merge" used to allow merging two branches that have no common base by default, which led to a brand new history of an existing project created and then get pulled by an unsuspecting maintainer, which allowed an unnecessary parallel history merged into the existing project. The command has been taught not to allow this by default, with an escape hatch --allow-unrelated-histories option to be used in a rare event that merges histories of two projects that started their lives independently.

### git rebase

git rebase will take the commits on this branch and "move" them so that their new "base" is at the point you specify.

The reason I put "move" in quotations because this process actually generates brand new commits with completely different IDs than the old commits, and leaves the old commits where they were. For this reason, you never want to rebase commits that have already been shared with the team you are working with.

A rebase is an alternative to a merge for combining multiple branches. Whereas a merge creates a single commit with two parents, leaving a non-linear history, a rebase replays the commits from the current branch onto another, leaving a linear history. In essence, this is an automated way of performing several cherry-picks in a row.

![Alt text](</assets/images/git wiki/image-15.png>)

The above command takes all the commits that exist in topic but not in main (namely 169a6 and 2c33a), replays them onto main, and then moves the branch head to the new tip. Note that the old commits will be garbage collected if they are no longer referenced.

## remote server

- Showing Your Remotes
To see which remote servers you have configured, you can run the git remote command. It lists the shortnames of each remote handle you’ve specified.

If you’ve cloned your repository, you should at least see origin — that is the default name Git gives to the server you cloned from:

```bash
$ git clone https://github.com/schacon/ticgit
Cloning into 'ticgit'...
remote: Reusing existing pack: 1857, done.
remote: Total 1857 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (1857/1857), 374.35 KiB | 268.00 KiB/s, done.
Resolving deltas: 100% (772/772), done.
Checking connectivity... done.
$ cd ticgit
$ git remote
origin
```


You can also specify -v, which shows you the URLs that Git has stored for the shortname to be used when reading and writing to that remote:

`$ git remote -v`
`origin	https://github.com/schacon/ticgit (fetch)`
`origin	https://github.com/schacon/ticgit (push)`


- Adding Remote Repositories
We’ve mentioned and given some demonstrations of how the git clone command implicitly adds the origin remote for you. Here’s how to add a new remote explicitly. To add a new remote Git repository as a shortname you can reference easily, run git remote add <shortname> <url>:

$ git remote
origin
$ git remote add pb https://github.com/paulboone/ticgit
$ git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
pb	https://github.com/paulboone/ticgit (fetch)
pb	https://github.com/paulboone/ticgit (push)

 if you want to fetch all the information that Paul has but that you don’t yet have in your repository, you can run git fetch pb:

 $ git fetch pb
remote: Counting objects: 43, done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 43 (delta 10), reused 31 (delta 5)
Unpacking objects: 100% (43/43), done.
From https://github.com/paulboone/ticgit
 * [new branch]      master     -> pb/master
 * [new branch]      ticgit     -> pb/ticgit

Paul’s master branch is now accessible locally as pb/master — you can merge it into one of your branches, or you can check out a local branch at that point if you want to inspect it.


### git fetch

As you just saw, to get data from your remote projects, you can run:

`$ git fetch <remote>`


git fetch will update all of the "remote tracking branches" in your local repository. Remote tracking branches are tagged in grey.

It’s important to note that the git fetch command only downloads the data to your local repository — it doesn’t automatically merge it with any of your work or modify what you’re currently working on. You have to merge it manually into your work when you’re ready.

![Alt text](</assets/images/git wiki/image-16.png>)

![Alt text](</assets/images/git wiki/image-17.png>)

### git pull

A git pull is a two step process that first does a git fetch, and then does a git merge of the remote tracking branch associated with your current branch. If you have no current branch, the process will stop after fetching.

If your current branch is set up to track a remote branch, you can use the git pull command to automatically fetch and then merge that remote branch into your current branch.

If you have a tracking branch set up as demonstrated in the last section, either by explicitly setting it or by having it created for you by the clone or checkout commands, git pull will look up what server and branch your current branch is tracking, fetch from that server and then try to merge in that remote branch.



---

Tracking branches are local branches that have a direct relationship to a remote branch. If you’re on a tracking branch and type git pull, Git automatically knows which server to fetch from and which branch to merge in.

If you clone a repository, the command automatically adds that remote repository under the name “origin”

by default, the git clone command automatically sets up your local master branch to track the remote master branch (or whatever the default branch is called)

you can set up other tracking branches if you wish — ones that track branches on other remotes, or don’t track the master branch. The simple case is the example you just saw, running git checkout -b <branch> <remote>/<branch>.

$ git checkout -b sf origin/serverfix
Branch sf set up to track remote branch serverfix from origin.
Switched to a new branch 'sf'
Now, your local branch sf will automatically pull from origin/serverfix.

If you already have a local branch and want to set it to a remote branch you just pulled down, or want to change the upstream branch you’re tracking, you can use the -u or --set-upstream-to option to git branch to explicitly set it at any time.

$ git branch -u origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.

If you want to see what tracking branches you have set up, you can use the -vv option to git branch. This will list out your local branches with more information including what each branch is tracking and if your local branch is ahead, behind or both.


hint: If you are planning on basing your work on an upstream
hint: branch that already exists at the remote, you may need to
hint: run "git fetch" to retrieve it.
hint:
hint: If you are planning to push out a new local branch that
hint: will track its remote counterpart, you may want to use
hint: "git push -u" to set the upstream config as you push.

$ git push
fatal: The current branch newbrachname has no upstream branch.
To push the current branch and set the remote as upstream, use
    git push --set-upstream origin newbrachname

```bash
$ git branch -vv
  iss53     7e424c3 [origin/iss53: ahead 2] Add forgotten brackets
  master    1ae2a45 [origin/master] Deploy index fix
* serverfix f8674d9 [teamone/server-fix-good: ahead 3, behind 1] This should do it
  testing   5ea463a Try something new
```

So here we can see that our iss53 branch is tracking origin/iss53 and is “ahead” by two, meaning that we have two commits locally that are not pushed to the server. 
We can also see that our master branch is tracking origin/master and is up to date.
Next we can see that our serverfix branch is tracking the server-fix-good branch on our teamone server and is ahead by three and behind by one, meaning that there is one commit on the server we haven’t merged in yet and three commits locally that we haven’t pushed.
Finally we can see that our testing branch is not tracking any remote branch.

It’s important to note that these numbers are only since the last time you fetched from each server. This command does not reach out to the servers, it’s telling you about what it has cached from these servers locally. If you want totally up to date ahead and behind numbers, you’ll need to fetch from all your remotes right before running this. You could do that like this:

$ git fetch --all; git branch -vv

### git push

A git push will find the commits you have on your local branch that the corresponding branch on the origin server does not have, and send them to the remote repository.

By default, all pushes must cause a fast-forward merge on the remote repository. If there is any divergence between your local branch and the remote branch, your push will be rejected. In this scenario, you need to pull first and then you will be able to push again.

If you have a branch named serverfix that you want to work on with others, you can push it up the same way you pushed your first branch. Run git push <remote> <branch>:

$ git push origin serverfix

You can also do `git push origin serverfix:serverfix`, which does the same thing — it says, “Take my serverfix and make it the remote’s serverfix.” You can use this format to push a local branch into a remote branch that is named differently. If you didn’t want it to be called serverfix on the remote, you could instead run `git push origin serverfix:awesomebranch` to push your local serverfix branch to the awesomebranch branch on the remote project.


### example

you have a Git server on your network at git.ourcompany.com. If you clone from this, Git’s clone command automatically names it origin for you, pulls down all its data, creates a pointer to where its master branch is, and names it origin/master locally. Git also gives you your own local master branch starting at the same place as origin’s master branch, so you have something to work from.

![Alt text](</assets/images/git wiki/image-21.png>)

If you do some work on your local master branch, and, in the meantime, someone else pushes to git.ourcompany.com and updates its master branch, then your histories move forward differently. Also, as long as you stay out of contact with your origin server, your origin/master pointer doesn’t move.

![Alt text](</assets/images/git wiki/image-22.png>)

To synchronize your work with a given remote, you run a git fetch <remote> command (in our case, git fetch origin). This command looks up which server “origin” is (in this case, it’s git.ourcompany.com), fetches any data from it that you don’t yet have, and updates your local database, moving your origin/master pointer to its new, more up-to-date position.

![Alt text](</assets/images/git wiki/image-23.png>)

you have another internal Git server that is used only for development by one of your sprint teams. This server is at git.team1.ourcompany.com. You can add it as a new remote reference to the project you’re currently working on by running the git remote add command.Name this remote teamone, which will be your shortname for that whole URL.

![Alt text](</assets/images/git wiki/image-24.png>)

Now, you can run git fetch teamone to fetch everything the remote teamone server has that you don’t have yet. Because that server has a subset of the data your origin server has right now, Git fetches no data but sets a remote-tracking branch called teamone/master to point to the commit that teamone has as its master branch.

![Alt text](</assets/images/git wiki/image-25.png>)

It’s important to note that when you do a fetch that brings down new remote-tracking branches, you don’t automatically have local, editable copies of them. In other words, in this case, you don’t have a new serverfix branch — you have only an origin/serverfix pointer that you can’t modify.

To merge this work into your current working branch, you can run `git merge origin/serverfix`.

If you want your own serverfix branch that you can work on, you can base it off your remote-tracking branch:

`$ git checkout -b serverfix origin/serverfix`
Branch serverfix set up to track remote branch serverfix from origin.
Switched to a new branch 'serverfix'
This gives you a local branch that you can work on that starts where origin/serverfix is.


- How to create a new repository which is a clone of another repository

1. There's probably several ways to do this, including a smarter one, but this is how I would do this:

Make a new repo on Github called SecondProject.
Locally clone your MyfirstProject, either from disk or from Github. Then use git pull on the branches you need to move to the second repo.
git remote set-url origin git@github.com:yourname/SecondProject.git
Push it.
Note that the clone retains a shared history with MyfirstProject, which is useful if you change your mind about the "never merge" bit.

1. 

Clone your MyfirstProject to your local machine.
Delete .git folder
git init
Publish your new project


2. lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test (newbrachname)
$ cd ../test1

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1
$ git clone git@github.com:lucfe2010/images-1.git
Cloning into 'images-1'...
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 13 (delta 2), reused 9 (delta 2), pack-reused 0
Receiving objects: 100% (13/13), 160.86 KiB | 285.00 KiB/s, done.
Resolving deltas: 100% (2/2), done.

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1
$ cd images-1/

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git remote -v
origin  git@github.com:lucfe2010/images-1.git (fetch)
origin  git@github.com:lucfe2010/images-1.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git branch -vv
* master 0a5aeaa [origin/master] Upload by PicGo

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git remote remove origin

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git remote -v

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git branch -vv
* master 0a5aeaa Upload by PicGo

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git remote add origin git@github.com:lucfe2010/test.git

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git remote -v
origin  git@github.com:lucfe2010/test.git (fetch)
origin  git@github.com:lucfe2010/test.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git branch -v
* master 0a5aeaa Upload by PicGo

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.


lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git push -u origin master
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/lucfe2010/test/pull/new/master
remote:
To github.com:lucfe2010/test.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git remote -v
origin  git@github.com:lucfe2010/test.git (fetch)
origin  git@github.com:lucfe2010/test.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test1/images-1 (master)
$ git branch -vv
* master 0a5aeaa [origin/master] Upload by PicGo


---


lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1
$ cd test3

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3
$ git clone git@github.com:lucfe2010/test.git
Cloning into 'test'...
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 11 (delta 2), reused 11 (delta 2), pack-reused 0
Receiving objects: 100% (11/11), 160.61 KiB | 309.00 KiB/s, done.
Resolving deltas: 100% (2/2), done.

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3
$ git remote -v
fatal: not a git repository (or any of the parent directories): .git

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3
$ cd test

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3/test (newbrachname)
$ git remote -v
origin  git@github.com:lucfe2010/test.git (fetch)
origin  git@github.com:lucfe2010/test.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3/test (newbrachname)
$ git branch -vv
* newbrachname 6c2d445 [origin/newbrachname] 4253

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3/test (newbrachname)
$ git remote set-url origin git@github.com:lucfe2010/images-1.git

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3/test (newbrachname)
$ git remote -v
origin  git@github.com:lucfe2010/images-1.git (fetch)
origin  git@github.com:lucfe2010/images-1.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3/test (newbrachname)
$ git branch -vv
* newbrachname 6c2d445 [origin/newbrachname] 4253

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test3/test (newbrachname)
$ git push
Everything up-to-date


---

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4
$ git clone git@github.com:lucfe2010/test.git
Cloning into 'test'...
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 11 (delta 2), reused 11 (delta 2), pack-reused 0
Receiving objects: 100% (11/11), 160.61 KiB | 261.00 KiB/s, done.

Resolving deltas: 100% (2/2), done.

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4
$ cd test

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (newbrachname)
$ git remote -v
origin  git@github.com:lucfe2010/test.git (fetch)
origin  git@github.com:lucfe2010/test.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (newbrachname)
$ git branch -vv
* newbrachname 6c2d445 [origin/newbrachname] 4253

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (newbrachname)
$ git remote add myrepo git@github.com:lucfe2010/images-1.git

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (newbrachname)
$ git remote -v
myrepo  git@github.com:lucfe2010/images-1.git (fetch)
myrepo  git@github.com:lucfe2010/images-1.git (push)
origin  git@github.com:lucfe2010/test.git (fetch)
origin  git@github.com:lucfe2010/test.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (newbrachname)
$ git branch -vv
* newbrachname 6c2d445 [origin/newbrachname] 4253

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (newbrachname)
$ git branch myb

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (newbrachname)
$ git checkout myb
Switched to branch 'myb'

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (myb) 
$ git fetch myrepo
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 56.66 KiB | 118.00 KiB/s, done.
From github.com:lucfe2010/images-1
 * [new branch]      main         -> myrepo/main
 * [new branch]      master       -> myrepo/master
 * [new branch]      myb          -> myrepo/myb
 * [new branch]      newbrachname -> myrepo/newbrachname


lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (myb)
$ git branch -u myrepo/myb
branch 'myb' set up to track 'myrepo/myb'.

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (myb) 
$ git branch -vv
* myb          6c2d445 [myrepo/myb] 4253
  newbrachname 6c2d445 [origin/newbrachname] 4253


lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test4/test (myb) 
$ git pull
Already up to date.

---

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5
$ git clone git@github.com:lucfe2010/test.git
Cloning into 'test'...
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 11 (delta 2), reused 11 (delta 2), pack-reused 0
Receiving objects: 100% (11/11), 160.61 KiB | 302.00 KiB/s, done.

Resolving deltas: 100% (2/2), done.

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5
$ cd test

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (newbrachname)
$ git remote -v
origin  git@github.com:lucfe2010/test.git (fetch)
origin  git@github.com:lucfe2010/test.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (newbrachname)
$ git branch -v
* newbrachname 6c2d445 4253

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (newbrachname)
$ git remote add myrepo git@github.com:lucfe2010/images-1.git

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (newbrachname)
$ git remote -v
myrepo  git@github.com:lucfe2010/images-1.git (fetch)
myrepo  git@github.com:lucfe2010/images-1.git (push)
origin  git@github.com:lucfe2010/test.git (fetch)
origin  git@github.com:lucfe2010/test.git (push)

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (newbrachname)
$ git fetch myrepo
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 56.66 KiB | 118.00 KiB/s, done.
From github.com:lucfe2010/images-1
 * [new branch]      main         -> myrepo/main
 * [new branch]      master       -> myrepo/master
 * [new branch]      myb          -> myrepo/myb
 * [new branch]      newbrachname -> myrepo/newbrachname

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (newbrachname)
$ git checkout -b myb myrepo/myb
Switched to a new branch 'myb'
branch 'myb' set up to track 'myrepo/myb'.

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (myb) 
$ git branch -vv
* myb          6c2d445 [myrepo/myb] 4253
  newbrachname 6c2d445 [origin/newbrachname] 4253

lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (myb) 
$ git remote -v
myrepo  git@github.com:lucfe2010/images-1.git (fetch)
myrepo  git@github.com:lucfe2010/images-1.git (push)
origin  git@github.com:lucfe2010/test.git (fetch)
origin  git@github.com:lucfe2010/test.git (push)



lcf@DESKTOP-LCF MINGW64 ~/Documents/lucfe_website_test/test_git_1/test1/test5/test (myb) 
$ git pull
Already up to date.