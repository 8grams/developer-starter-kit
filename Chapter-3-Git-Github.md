 # Git And GitHub

__Git__ is a software to manage source code versioning. In software development world, Git is categorized into _version control system software_. There are many possibilities for VCS, from _centralized_ (such as CVS and Subversion) to _distributed_ (such as Git or Darcs or Mercurial). This chapter discussed Git and how it can be used together with GitHub to help developers in doing their development tasks.

## What Are Git and GitHub?

Git is a __version control system software__. It is used to track changes in files and also provides facilities to coordinate developer work on those files among fellow developers. Git was created by _Linus Torvalds_ back in 2005 to coordinate Linux kernel development work after BitKeeper became a proprietary software. Usually, developers use Git to handle source code eventhough not necessarily source code can be handled by Git. Any digital files are able to be handled.

A directory which is used to store files is called a __repository__. The repository can also be saved into a remote repository. GitHub is such a kind of service to provice remote repository for developers. The repository can be public or private.

## Basic Setup for Git

When Git has been installed, some commands and their manual pages are available. Usually, these comamnds exist:

- /usr/bin/git
- /usr/bin/git-cvsserver
- /usr/bin/git-receive-pack
- /usr/bin/git-shell
- /usr/bin/git-upload-archive
- /usr/bin/git-upload-pack
- /usr/bin/gitk

Although some commands are available, the command that developers usually use the most is git. To start working with Git, one has to setup its initial configuration by using this command:

```
~$ git config --global user.name "Put Your Name"
~$ git config --global user.email your@email.com
```

The result is written in __$HOME/.gitconfig__ file. After this initial setup, developer must have an account in Github. Signup using this URL: https://github.com/join. It is good to have the same name and the same email account as __$HOME/.gitconfig__.

## Basic Commands

### Clone A Repository

A remote repository can be cloned into local computer using git clone:

    git clone URL

Example:

   ~$  git clone https://github.com/ocam1/opam. git

or

    ~$ git clone https://github.com/ocaml/opam

### Create A Git Repository

In local computer, a git repository can be created using (create and enter empty directory first):

    ~$ git init

The result is __.git/__ directory where Git will write any change log. After this step, one can put any files into the directory and then make Git log them plus any changes which happen in any of those files.

Put all the files or create any file inside, and then when everything is finished (at least at that point), use this to record any changes:

```
~$ git add -A
~$ git commit -m "Notes on this commit"
```

One may also use __add__ for specific file(s) such as:

   ~$  git add README.md

### Branching and Merging

If one already commits all changes, it is a good practice to create a branch whenever a need to update repository contents is realized. After doing any updates, if the update is ok, the update will be committed and merged but if they are not ok then one may delete them without afraif of their files in repository dirty.

```
~$ git checkout -b branch-name
...
do any updates
...
~$ git checkout previous-branch
~$ git merge branch-name
~$ git branch -D delete branch-name
```

If the update will be used:

```
~$ git checkout -b branch-name
...
do any update
...
~$ git checkout previous-branch
~$ git branch -D branch-name
```

## Git Workflow for Single Developer

For single developer, Git and Github is not quite difficult:

- Create a repository using this URL: https://github.com/new. Leave it without README.md. A __.gitignore__ file is used to exclude files from being handled by Git and GitHub (usually for something like temporary files, cache, etc). A license maybe selected if needed. Remember, if the repo is not empty, then we may not be able to push anything to the GitHub remote repository from local repository.
- Prepare local repository. This local repository will be pushed to remote repository.
- Let local repository knows about remote GitHub repository: 
    `git remote add origin https://github.com/username/reponame.git`
We put __origin__ to represent the remote repository.
- `git add -A`
- `git commit -m "Notes for push"`
- `git push origin master`
- See https://github.com/username/reponame.git - the files are pushed to that repo.


## Git Workflow for Team

There are many possibilities for a team but basically this section will discuss the generic steps for team. A team usually has a repo. This repo is called upstream repo. Upstream repo has an owner which has a right to permit or deny any request to the repo. Usually this person is called upstream author or maintainer. Any other person in the team is contributor. Git workflow for team can be describe below:

1. A team has a repository. Make sure that every person clone the repo to their local computer:
    `git clone URL`
2. Whenever a contributor need to make changes, make sure that he / she must create that in a branch. Example (inside repository in contributor’s local computer and branch is __master__):
```
~$ git checkout -b branch-name
...
update ...
...
~$ git add -A
~$ git commit -m "Notes (may also put #issue)"
~$ git checkout master
~$ git push origin branch-name
```
3. Contributor go to repo in GitHub, select branch and create __Pull Request__ (PR).
4. The maintainer will review the code from PR tab, and then merge into master branch (or any other default branch) if the code is fine. Otherwise, the code will not be merged.