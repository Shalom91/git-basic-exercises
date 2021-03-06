
# Introduction

This little exercise will take you through the basic git mechanisms you need to know about in order to be productive. By the end of this exercise you’ll be able to create and manage your own git repos

## Creating and managing your own repo
Note: you can do all of this stuff from the command line! You should be using linux. Open up a terminal and do the following:

### Your initial commit
- Create a directory named git-basic-exercises
- cd into your new directory
- look at what’s inside using ls -a. It should be empty
- initialize your git repo using git init. Then check ls -a again. Can you spot the difference?
check the status of your repo by typing git status
- type in touch README.md. This creates a new blank file. Then check ls -a and git status again.
- type in git log. The output should make sense to you
- Now add your readme file to your git staging area. Hint: use the git add command
- Then check your git status again. Can you see the difference?
- Try to unstage your file and check your git status again

Ok, now for your first commit: Make sure your readme file is staged then type in git commit -m "initial commit" Your output should be something like this:

 [master (root-commit) 2103b64] initial commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
type in git log isn’t that nice? press q to exit

### more commits!

- type in nano README.md. This will open up a text editor. Type in some stuff and then press ctrl x to exit. Then y then enter. This will save your changes
- type in cat README.md. This will print your file to the console
- take a look at the git stats again and make sure you understand it
- commit your changes to your repo. Your commit should have the message "second commit"
- make some more changes to your readme and make a "third commit"

### check this out

- type in git log. You should see all your commits there. It should look something like this:
commit a57585d3cf93e64c04e62e58dfe8151d191503cf (HEAD -> master)
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:07:40 2019 +0200

    third commit

commit a48c005c761902395cf9a50f13ddbffeee4f5537
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:07:12 2019 +0200

    second commit

commit 2103b6418ecf4f70effabb639cfad6ac9d57c089
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 14:43:51 2019 +0200

    initial commit
Each commit has a “hash”. That’s the weird alphanumeric string thingy.

- Copy the commit hash for your second commit. You can just select it with your mouse and right click and choose ‘copy’
- press q to exit the log view. You should now be back at the terminal
- type in git checkout and then paste in the commit hash and press enter
- cat README.md It’s like going back in time
- git checkout master
- cat README.md Now we are up to date

You can jump to any commit using git checkout. You can checkout a branch, a commit hash, or a tag. We didn’t explore tags here.

When you checkout a branch, you checkout the latest commit on that branch.

### branching

The real power of git is in branching. Branching is what allows big teams of developers to work on the same code base. Let’s explore branching a little bit.

- git branch This lists all your branches. Git makes a branch named master by default
- Now create a new branch called milkshake-flavours. git is not too restrictive when it comes to naming our branches. It’s generally best to choose a name that has something to do with what the branch is for. Our branch is about milkshakes
- type in git branch. Notice the little *.
- check out your new branch. type in git branch again and look at the *. Can you see what it means? Try switching between the different branches and see how hings change.
- Make sure you are on the milkshake-flavours branch then type in nano milkshakes.md and write fill in a few flavours. Mmmm. save and exit
- what does git status tell you?
- commit your new file with the message "added initial flavours"
- take a look at your git log again. It should make sense
- checkout your master branch. It’ll look a little different. Can you see why?
- from your master branch, create a new branch called history and check it out. If you say git log it should only have three commits
- type in history > history.txt. Can you guess what it does?
- commit your changes with the message "added history". Take a look at the git log
- now checkout your milkshake branch and look at the git log. it should have your three master commits and your one milkshake commit
- make some arbitrary changes to the readme file and make a new commit with the message "random readme changes"
- checkout history again and cat README.md
- now on your history branch do the following:
rm README.md
echo "booya" > README.md
You should know what these lines do.

- commit your changes. Use the commit message "rewrote readme"
- checkout master again

### Just make sure we are still on track

If you have followed along up until this point then your branches should look like this:

Type in:

git checkout master
ls
this outputs:

README.md
Check the log:

git log
this outputs something like:

commit a57585d3cf93e64c04e62e58dfe8151d191503cf (HEAD -> master)
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:07:40 2019 +0200

    third commit

commit a48c005c761902395cf9a50f13ddbffeee4f5537
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:07:12 2019 +0200

    second commit

commit 2103b6418ecf4f70effabb639cfad6ac9d57c089
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 14:43:51 2019 +0200

    initial commit
Now lets look at milkshake-flavours:

git checkout milkshake-flavours
ls
You will see two files:

milkshakes.md  README.md
And git log will look like:

commit d2559d9758f3ec0f7928f6cbef705c6fa9679edf (HEAD -> milkshake-flavours)
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:25:07 2019 +0200

    added initial flavours

commit a57585d3cf93e64c04e62e58dfe8151d191503cf (master)
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:07:40 2019 +0200

    third commit

commit a48c005c761902395cf9a50f13ddbffeee4f5537
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:07:12 2019 +0200

    second commit

commit 2103b6418ecf4f70effabb639cfad6ac9d57c089
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 14:43:51 2019 +0200

    initial commit
Finally history:

git checkout history
ls
there should be two files:

history.txt  README.md
and git log outputs

commit 34025ac2b26accb7c5c18ec048a4982d3bae8909 (HEAD -> history)
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:38:05 2019 +0200

    rewrote readme

commit b9e3c50fb65c7b2df0f09b921a15a7fc146e0bfb
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:36:04 2019 +0200

    added history

commit a57585d3cf93e64c04e62e58dfe8151d191503cf (master)
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:07:40 2019 +0200

    third commit

commit a48c005c761902395cf9a50f13ddbffeee4f5537
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 15:07:12 2019 +0200

    second commit

commit 2103b6418ecf4f70effabb639cfad6ac9d57c089
Author: Sheena O'Connell <sheena.oconnell@gmail.com>
Date:   Tue Apr 23 14:43:51 2019 +0200

    initial commit
    
### merging
Now we want to get the master up to date with all out changes. Let’s start with the milkshake branch

- merge milkshake-flavours into master
git checkout master
git merge milkshake-flavours
- Use ls and git log to see what this did
- merge history into master
- Use ls and git log to see what this did As you can see a whole lot of changes have been made to the master branch
- Now lets take a look at the other branches

git checkout history
git log
...
git checkout milkshake-flavours
git log

These branches were not effected by the merge!

In general if we want to merge branch X into branch Y:

git checkout Y
git merge X
This adds a commit to branch Y and doesn’t change branch X

- merge the master branch into history. Use git log to see whats up.
- checkout master again. git log again. Can you spot any differences?

### GitHub

- Go to Github.com (using your browser of choice) and create a new public repository using the user interface. Name it git-basic-exercises

- You will see a bunch of weird looking things. There is a section entitled “…or push an existing repository from the command line”. We have an existing repository and a command line. So this seems appropriate. Copy the commands from there and paste them into your terminal. this will push your changes to github.

- Refresh your browser. Cool eh?

Now you should see a little dropdown box on github that says “Branch: master”. Click there. your other branches aren’t available.

- Push your other branches to github. We want all branches to be listed

### Pulling and remotes

- You should still be inside the git-basic-exercises directory. Let’s get out of there. cd ../
- Now let’s clone a repo. point your browser here: https://github.com/Umuzi-org/tech-department
- Now there is a friendly green button that says “Clone or download”. Click on it.
- You will see a url come up. Copy it. You will need to paste it into the terminal in a moment
- In your terminal type in git clone $THE_URL_YOU_JUST_COPIED. It should look something like this: git clone https://github.com/Umuzi-org/tech-department
- cd into the tech-department directory that was just created
- explore a little using git branch and git log
- type in git branch -a. This shows the remote branches
- try to checkout the branch called project/git-basic-exercises on your local computer. You can do it, you’ll need to figure out how
- type in git remote -v

### Multiple Repos

- While still in your newly created branch project/git-basic-exercises use git log to see the history.
- From your new branch called project/git-basic-exercisesnavigate back to your git-basic-exercises repo, use git log again to see the difference.
- Let’s go back to our home directory cd and make a new folder mkdir this-will-be-another-repo
- cd into this folder now use git init to initilise a new git repo here, you should get a message in terminal that says ‘Initialized empty Git repository in /home/\$specific-path/this-will-be-another-repo/.git/’
- Type in touch README.md. This creates a new blank file. Stage then commit.
- Go back to your git-basic-exercises repo and use git log to check that you are in the right place and repo.

### gitignore
- Create a new file touch ignore-me.db
- Now use git status to see what is going on in your repo, you will see ignore-me.bd as an unstaged file.
- Now lets create a .gitignore file type nano .gitignore
- In this file type ignore-me.db save and exit your .gitignore file
- Now use git status you will notice that ignore-me.db is no longer an unstaged file and is no longer being tracked by github and .gitignore is being tracked.
- Create a new directory mkdir large-directory-that-should-be-local-only
- cd into this directory and create a readme.md file with some random text in
- Use cd .. to go back to your main directory and git status to see what is going on, you should now see your new folder as an unstaged change.
- Lets add this folder to .gitignore nano .gitignore and add /large-directory-that-should-be-local-only on a new line, save and close .gitignore
- Check git status again, .gitignore is going to be super useful later when you are submitting projects and need to keep your repos small and free from junk and irrelevant files.

### gitignore best practices

You should always gitignore the items in the below list:

- secrets like passwords and keys
- databases
- pycache/
- node_modules/
- temporary files and editor settings files eg .vscode/

### Repo Best Practices

Your repo should be all of the following:

- Files and folders in your repo should be named appropriately.
- Use names that make sense and relate to your projects i.e. simple-calculator
- Each project should be in its own repo
- There should be no junk/unnecessary file in your repos
- Your repos should be small (remember the use of .gitignore)

### Going forward

We just covered the basics here. Please make sure you understand this stuff. It’s super important. Git might seem like a weird theoretical thing to a lot of you. It might seem completely unrelated to the actual job of writing code. But it’s not. Git makes teamwork on dev teams possible. Without it we’d spend more time shouting at each other than writing useful code. So learn it. Be comfortable with it. When we start working in teams later on all will be made clear.

If you are curious now, spend some time googling git branching strategies. We use the feature branching strategy here. We’ll cover it in depth later on in the course.


<<<<<<< HEAD
Typing some stuff for testing...#01
Making some more changes for testing...#02
Making some arbitrary changes for testing...#03
=======
booya
>>>>>>> history
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.

