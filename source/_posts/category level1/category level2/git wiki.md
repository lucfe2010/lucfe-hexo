## git commit



Typically, you’ll want to start making changes and committing snapshots of those changes into your repository each time the project reaches a state you want to record.

each file in your working directory can be in one of two states: tracked or untracked. 

Tracked files are files that were in the last snapshot, as well as any newly staged files; they can be unmodified, modified, or staged.In short, tracked files are files that Git knows about.

Untracked files are everything else — any files in your working directory that were not in your last snapshot and are not in your staging area. When you first clone a repository, all of your files will be tracked and unmodified because Git just checked them out and you haven’t edited anything.

As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.

![Alt text](</assets/images/git wiki/image.png>)