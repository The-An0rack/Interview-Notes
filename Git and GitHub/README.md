## Git and GitHub for Beginners

Git allows us to track and maintain changes in a codebase known as a repository. This system is known as VCS.

**GitHub** is a cloud based version control system(VCS) that allows us to host our code and allow collaboration and sharing of projects for various users all around the world.

#### Beginning Steps

1.  Install git from the internet
2.  After installation, go to the console and set up name and email
    1.  Set the name: `git config --global user.name “FIRSTNAME LASTNAME”`
    2.  Set the email: `git config --global user.email “EMAIL@CLIENT.COM”`

#### Initialise a new git repository

`git init`

The entire history of a repository is stored in a `.git` folder.

#### View changes in a project

`git status`

Lifecycle of a file: untracked → tracked → modified → staged → committed → pushed

#### Add files to staging area

Only files that are tracked are kept track of. To stage a file

`git add <file_name>`

Or we can use the following command to add all untracked and modified files

`git add .`

We can also remove a file from stage:

`git restore --staged <file_name>`

#### Commit changes

`git commit -m “COMMIT MESSAGE”`

#### See all the changes that are made to the project

`git log`

#### Travel back to a previous commit

When we travel back to a particular commit, all the commits after it are deleted.

`git reset <commit hash code>`

#### Keep current changes aside without committing them: _stashing_

`git stash`

This stashes the changes since the last commit, while keeping changes stored. To get back the changes

`git stash pop`

To remove all stashed changes

`git stash clear`

#### Working with Remote Repositories

Add current repos to remote repos

`git remote add <name_of_url> <url_of_remote_repos>`

By defalut name of url is kept origin.

#### Branches

Always create a separate branch for a new feature.

Committing is rarely done in main branch, only finalsed code must go into main branch

**Create a new branch**

`git branch <branch_name>`

**Go to a particular branch**

`git checkout <branch_name>`

**Merge a branch to main branch**

`git merge <branch_name>`

#### Forking

It is defined as creating a copy of a repository in your account.

#### Cloning

It is defined as bringing a repository from cloud to your local machine

`git clone <repository_url>.git` 

Upstream URL is the URL from where you have forked a given project. To add an upstream:

`git remote add upstream <repository_url>.git`

#### What is a pull request?

It is a request to the original repository to merge your changes to their repository.

#### Fetch data from upstream

`git fetch -- all – prune`

`git reset --hard  upstream/main`

Alternatively, 

`git pull upstream main`

#### Merging several commits to a single commit: squashing

**Trick 1:**

reset to old commit and then commit

**Trick 2:**

`git rebase -i <commit hash>`

It will show all commit after the commit that has given hash, now we can either pick or squash

to pick: **pick**

to squash: **s**