# Notes for talk on git --- hub

git with Unix executable image != GitHub octocat

## Start a Repo

* For Any Folder

Now we just `git init` Boom done!

* For an Xcode Project

Just check the box when starting, or "Create Working Copy"

## Use an existing repo

Fork or clone from GitHub
Needs to already be a git repository
just click the clone or fork button on GitHub.

### Clone

A full copy of the source code and history.
You might make a clone of
* an example project
* a Library you want to use
* A friends code to help debug an issue

Since this is a git folder you can just continue working adding more commits and work

### Fork (GitHub)
This is a GitHub specific feature, takes an existing repo on GitHub and make a repo
under your account for it.
Think of this as a GitHub -> GitHub clone.

## Everyday (More like every hour)

Write new code or fix bugs. Then you will want to "make a snapshot"
git calls this a commit.
These commits are the main pieces that git works with.

### A commit object has

* An author - Git will ask you to set these up if they are not yet configured.
* A complete project - The full source is here (No computed diffs)
* A unique hash
* A message

You will probably want a tool for looking at these commits.
* Git Kraken **Image Here**
* gitk **Image Here**
* SourceTree **Image Here**

You could look at these through the command line with the `git log` command
There is a ton of commands to modify how this looks.

### How to make one

`git commit` but it is actually a bit more complex than that. And this is probably where most people want to quit.

You have to decide, by hand manually, By dragging files or clicking buttons or typing commands

What do you really want to be part of your changes? I often put red boxes everywhere when debugging layouts, I don't want
those saved in my projects history.

#### Git Status

Did you add a new file, or change existing ones or both?
Do you remember what you did? I almost never do.

`git status` is your friend. These visual tools will usually show your status by default.
**Image Here**
There you can decide what you want to do.

#### Git diff
`git diff` to show the actual lines you changed.

Focus * We still are trying to save our changes, Now we can see what we changed. We need to add it to the staging are just like
git status told us to.

#### Git Add
`git add` to stage new changes, and `git checkout` to put files back that we do not want to save.

You can mix and match these too. (if you have debugging code in the project definition) just commit the files that fix your bug.

Once it is staged we can commit it and make a new snapshot.

### Eject button `git reset --hard`

Sometimes it is nice to think of `git` as a bit of a safety net. You can try things out
knowing that you can always get back.

`git reset --hard` is you eject button. Something went horribly wrong, I just
want to go back to my last snapshot.

### Branching

Everything is a branch. Most of your initial project work will be commits added to a branch called master.
Branches basically point to one commit and all of their parent commits. Just like branches of a tree.

You will use these often.

`git branch Some_awesome_branch_name` to make a new one.

`git checkout Some_awesome_branch_name` to switch to that branch.

Continue fixing bugs, adding features. Depending on your team, You will probably do one fix or one feature per branch.

### Merge

Bring two branches together.

Move to the destination branch. Then just `git merge branch_with_changes_you_want`

You will not use this that often if using a GitHub workflow with pull requests, because there is a merge button on the web interface.
But if there are issues the web interface will tell you to do it this way.

#### Fast-Forward Merge vs. No Fast-Forward (What?) **Intermediate**

All about source management and specifically what do you want your history to look like.
Probably more of a senior level decision make sure you have your local system set up to do what your team
expects.

Talk through the pictures. **Images**

### ReBaseing - How to FF merge when others have made changes?

Talk through the pictures, You really just change the base. It is not that hard.

## GitHub - ^^^^ Look how much work you can do without GitHub.

GitHub is just a website where we can put code and browse others code and so much more.

## Remotes - How to connect you `git init` to the web.

`git remote -v show` show all remotes and their URLs.

**Image**

### Add a new Remote

`git remote add <name> <some_url>`

Now you can put your code on GitHub, for sharing with friends, or a portfolio or whatever.

### Putting new code up there.

This is called a Push.

The command is `git push` There are some subtleties.

You push a branch name and git looks back to see what it does not have yet for that branch.

But you may need the `-u` flag to make a new branch on GitHub.

U is for creating a new `upstream` branch.

You may need this when working on new branches.

### Get stuff

`git fetch --all` get all updates from origin

This way you can see what bugs are fixed on master, what your team is working on etc.

This does not automatically integrate. With your work, it just updates your pointers.

### Pull is Fetch Plus merge

`git pull` will grab the changes from upstream and merge them with the current branch.
You'll probably use this for master to just pull down your teams changes.
Then maybe Rebase your own work on top.

## Being Friends

We talked about interacting with a "remote" on Github. If you and your friends are in one organization
on github you can all push and fetch from one repo so this is pretty great.
This is how the Apple/Swift repo works right now. All Apple employees and some select
outsiders can push custom branches and push to master. But not everyone can.

How do I help? I want to make the docs clearer. I noticed a but. Can I fix it?

### How to pull Request!
* Fork
* Clone Your new Fork
* Branch
* Fixes and Commits
* Push
* Propose

-------------------------------------------------------------------------------

### Putting work aside with `git stash`

### Interactive Re-Base

Gotta talk about Re-Base.
     - Part of the problem with interactive rebase might be just learning vi!!!
Reorder and remove commits.

### Grab Bag
Find and fix bugs with `git bisect`
grab one commit with `git cherry-pick`
Search Your repo with `git grep`

# Resources:
Here is the getting started guide for git on GitHub https://guides.GitHub.com/activities/hello-world/

http://guides.github.com/
http://www.learnenough.com/git-tutorial
http://gitready.com/
http://git-scm.com/

Why do you need to know this. Because you love Swift or open source, You want
the world to be a better place.
Let's just Rebase this and get it merged -
https://GitHub.com/apple/swift/pull/330/files
