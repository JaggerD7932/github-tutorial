# GitHub Tutorial

_by Jagger D'Ugo_

---
## Git vs. GitHub

Git is version control, like taking snapshots of code.  
Github is a cloud for git, which allows us to see these snapshots. It also has the added bonus of being a great way for people to collaborate with each other on their code as well.  

> A good way to think of the two is like Git being a photographer who takes photos, where Github is like the album where you keep all the photos you've taken.

---
## Initial Setup

Before doing anything else, you'll need to have an IDE, and a Github account.  
There are several IDEs to choose from, but there's only one Github.  
To make a Github account, you first need to navigate to Github and click the create an account icon.  
From there, follow the steps, making sure to use your HSTAT email username if you're from HSTAT.  
Once you're done there, you can get your SSH key set up.
> For those who don't know, an SSH key is used because it is a "Secure Shell", which means that it will keep your files scure even if your network isn't.  
> It's also great becuase you won't need to log in every time you want to access what you use SSH with, which makes getting into your IDE's code way easier.  

To do that, you'll want to follow these steps:
1. Look at the top right corner, and click the profile icon, and navigate to settings.
2. On the left sidebar, click on SSH and GPG.
3. Assuming you're using Cloud9, add the title "cloud9" to the setup.
4. Continuing with this assumption, go to your Cloud9, and find the gear icon on the top right, and go to the SSH keys tab.
5. After that, copy and paste the second SSH key into Github (it should start with ssh-rsa), and then add your SSH key.
6. Once you're done all that, you should see "Hi <your username>! You've successfully authenticated, but GitHub does not provide shell access._" in your c9, after inputting "ssh -T git@github.com"

After finishing that, you're ready to move on to your **Repository Setup!**

---
## Repository Setup

If you're ready to make a repository, you'll first want to navigate to your IDE (we'll continue to use Cloud9 as the example), and get into whatever folder you want to work in.
Simply enter in `git init`, and your folder will be converted into a repository.  
What this now means is that your "repo" can save changes to github, and you can even see these when logged in.
> Note: Make sure you use `git init` within the actual folder you want to work in, not your whole workspace, otherwise you'll have to commit changes within every folder you have, instead of being able to do it with individual repos.  

Now that you've initialized, try creating a file (we'll use a basic text file for this example), and add something to it.  
After doing this, you'll want to add this file to the stage.  
Going back to our photograph analogy from before, adding a file to the stage is like moving it into the shot the photographer will take.  
To do this, type in `git add <filename>`, with `<filename>` being whatever you've called the file.

With the file on the stage, you can now "commit" your changes, which is taking the actual picture.  
You'll want to enter `git commit -m "<message>"` to do this, again with `<message>` being replaced by an appropriate message.
> Note: Standard syntax for messages is to speak in the present tense, and to always be descriptive with changes.  
For example, a good message for what we've done now might be "first initialize and commit", as it is in the present tense and describes what we're doing.  
A bad commit message, on the other hand, might be "initizled and committed", as it is the opposite.

Now that you've committed your changes, you've effectively taken your photograph you wanted, but unfortunatly, you cannot see your whole album now.  
If you want to do that, you'll want to set up a "remote repository".  
As stated before, this is basically a photo album in which we can visually see all of the changes we have made since our first commit until now, it's effectively another repository, just on Github.  
To set up your remote, you'll first want to create a repository on Github, making sure to use the same name as your local one.  
After doing this, you'll need to copy the URL on the Github repository, making sure to use the SSH link again, and then navigate back to Cloud9.  
Now, enter in `git remote add -origin URL`, replacing `"URL"` with the URL you copied from Github.  
Once you've done this, you can try entering the command `git remote -v`, just to make sure there's a place to push things to.  
You can also use this command in the future to just generally see where we'll push our changes to.  
Speaking of pushing changes...

Once you have a remote, we can finally push our changes to it (which is sort of the whole point of Github in the first place).  
To do this, we simply need to enter the command `git push -u origin master`, only using `git push` every subsequent time.  
You can look back on your remote and refresh the page to see that we've now successfully pushed our changes.  
Now that we've finished here, we can move to the workflow of Github and its commands.

---
## Workflow & Commands

### Command summary:
Command Line commands:
* `cd`: change directory (used to navigate between directories)
    * Use cd .. to go back a directory (needs to be done before moving to a level equal or greater than the current one)
* `mkdir`: make a new directory
* `rmdir`: delete a directory (will not work if done within the directory being deleted)
* `touch`: make a new file
* `c9`: will open a file is using Cloud9
* `rm -rf`: will remove a directory, even if it has subdirectories/files within it
* `mv`: move or rename a file (result will change depending on whether the desired input already exists as a directory or not)

Git commands:
* `git status`: show any changed files in red, and any changed files on the stage in green, so that you know what needs to be committed
* `git init`: initializes your repository, making it ready to save changes (only needs to be done once)
* `rm -rf .git`: essentially does the oposite of git init, by deleting the .git file made by that command
* `git add`: moves a file onto the stage before a commit
* `git commit -m <message>`: commits the changes made to a file in the staging area
* `git push`: moves new commits to the remote
* `git remote add -origin URL`: creates a remote repository on Github for your local repo to connect to
* `git remote -v`: shows where your changes will be pushed to (useful if you have multiple remotes)
* `git push -u origin master`: will push your changes "upstream", meaning any future pushes will be added with...
* `git push`: does the same as the previous command, but with added convenience
* `git reset HEAD`: used to "un-add" a file from the stage
* `git checkout --`: used to discard changes in the working directory (like an open file in c9)
* `git reset soft HEAD~1`: used to remove a commit, but keep your changes in your working directory  
* `git reset hard HEAD~1`: used to remove a commit, **and** remove your changes from the working directory
* `git push -f origin <last known good commit:branch name>`: used to completely remove a push from your Github repository
>Be careful with this one, because if used on a repo with multiple users who frequently push and pull, you will likely corrupt your repo

### Basic workflow in Github:
A good routine to follow when working with Github is as follows:
1) Enter your desired command, and make some kind of change
2) Enter `git status`, just to see what's happened, and if you need to backtrack
    * Follow steps 1 and 2 over and over again as necessary, but every so often (every few minutes, or at least once per session), you'll want to move on
3) You'll want to `git add` your changes to the stage, s go ahead and do that
4) Now you can `git commit` whatever you need to, making sure to use an appropriate message, and then...
5) Use `git push`, and check to make sure your changes went through. If they did, you're golden! If not, remember, always use `git status` to see where you go wrong before things get out of hand

---
## Rolling Back Changes

If you took a look at the command list already, you might have a bit of an idea of what's coming next...  
We're going to be looking at how to rollback (or undo) changes using Github.  

Let's start at the smallest level, which would be rolling back changes made in a file.  
To do this, simply add in `git checkout -- <file>`, substituting `<file>` with the name of your file.  
You should see the changes erase themselves instantly, which is what we want.  
Once you've gotten this to work, we'll try something a little bigger.  

If you want to remove a file from the stage, you'll want to use `git reset HEAD <file>`, which will remove your desired file from the stage, as promised.

Perhaps you've already committed a change, however, and want to undo this commit.  
It might seem impossible to do, but there are commands for this, and the first one is `git reset --soft HEAD~1`  
Using this command will basically undo your commit, but keep your changes on your working directory.  
While this is useful, we might want to delete our changes in our own directories as well.  
To do this, we use a similar command, `git reset --hard HEAD~1`.  
> To make sure this command works, we can try using `git status`, only to see that we have no changes.

There is but one command more powerful than this one... One that can remove even a pushed commit from a repo...  
This command... is `git push -f origin <last known good commit:branch name>`  
*Use its power wisely, for it can corrupt any repos used by more than one mere mortal...*