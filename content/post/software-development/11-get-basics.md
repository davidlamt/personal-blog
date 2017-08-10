---
title: "Git Basics: A Short Introduction"
date: 2017-08-10T08:03:22-07:00
publishdate: 2017-06-11
draft: false
slug: "git-basics"
categories: ["Software Development"]
---

In a [previous post](/what-is-version-control), I discussed the differences between centralized and distributed version control systems. I also made a statement that I prefer distributed version control systems.

Git is a distributed version control system. I do not claim that it is the best or that I am a master at it but I have had a wonderful experience using it.

In this post, I hope to give you a basic introduction into Git and its conventions. My goal is just to skim the surface (because that’s all I really know) and let your own thirst for knowledge carry you further.

## Git Lifecycle

There are four main areas in Git that we need to be familiar with:

1. Working directory
2. Staging area
3. Local Git repository
4. Remote Git repository

We start off at the working directory, the location our project files live on our local machine. When we “stage” files from this directory, they are moved into the appropriately named staging area.

We will definitely go over the commands that are required to perform these operations in a bit. Patience is a virtue! 🙂

The staging area contains the changes that are not yet “committed” to your local Git repository. You are still able to back out of these modifications at this point. Actually, you can still revert committed changes through a more involved process.

Your computer stores the local Git repository. This repository contains all of your commits and you are able to view and revert back to any of them. Since this repository exists on your computer, **you can version control without an internet connection**!

The remote Git repository is where you would “push” your local repository changes to. For instance, <a href="https://github.com/" target="_blank" rel="nofollow">GitHub</a>. Although not a necessity, a remote repository **helps you keep a copy of your project in the cloud**. Furthermore, it **promotes and facilitates code collaboration**.

## Installation

Installing Git is quite simple. Just head over to Git’s <a href="https://git-scm.com/downloads" target="_blank" rel="nofollow">download page</a> and install the correct version for your platform.

I recommend **using the command line for learning Git** because it helps you understand exactly what you are doing when you issue commands. I feel like Git GUI applications sometimes abstracts the process.

On the other hand, I do love abstractions. Once you are comfortable with using Git via the command line, feel free to switch to a GUI client! I still use the command line but I have had good experiences with <a href="https://www.sourcetreeapp.com/" target="_blank" rel="nofollow">SourceTree</a>.

## Basic Git Commands

In this section, I will go over some basic Git commands with examples. Please refer to the <a href="https://git-scm.com/docs" target="_blank" rel="nofollow">Git documentation</a> for further details and more commands.

### Status

```default
git status
```

This command will display various information about your repository, such as which changes have not been committed, what is staged, etc.

### Init

```default
git init
```

The `init` command creates a Git repository at your current directory.

### Remote Add

```default
git add remote origin <Remote repository URL>
```

This will add a remote repository connection to your local one to which you can push changes.

### Clone

```default
git clone <Remote repository URL>
```

The `clone` command copies the remote repository to your local directory.

### Pull

```default
git pull <Location to pull from (ex: origin)> <Branch to pull>
```

This command will `fetch` any changes in the remote repository and merge with your local repository.

### Push

```default
git push <Location to push to (ex: origin)> <Branch to push>
```

This will push the changes in your local repository to the remote repository.

### Add

```default
git add <Files you want to stage>
```

This adds files from your working directory to the staging area.

### Commit

```default
git commit <Files you want to commit>
git commit -am "<Your commit message>"
```

The `commit` command commits the files in your staging area to your local Git repository.

The `-am` portion specifies some options for the command. The `a` option commits all your staged files (but not files not tracked by Git yet). The `m` option allows you to add a message to your commit.

### Checkout

```default
git checkout <Branch to switch to>
git checkout -b <Branch to create> <Branch to branch from>
```

This command allows you to switch to another branch.

The `b` option allows you to create a new branch with the current project state according to the branch you wish to branch from. If the second branch is not specified, this command will create a branch from your current branch.

### Merge

```default
git merge <Branch you wish to merge with>
```

This will merge the branch you specify into your current branch.

## My Git Aliases

After using Git for a while, I set up some command line aliases to help facilitate a quicker and more pleasant Git workflow.

I am sure that there are more intuitive and advanced shortcuts out there. I am always on the lookout for ways to improve my day-to-day workflows so feel free to leave a comment with your favorite Git aliases!

Anyhow, here are the aliases I use:

```git
alias gs='git status'
alias gh='git log --all --graph --decorate --oneline'
alias ga='git add'
alias gaa='git add .'
alias gb='git checkout -b'
alias gdb='git branch -d'
alias gco='git checkout'
alias gc='git commit -am'
alias gm='git merge --no-ff'
alias gf='git fetch'
alias gpull='git pull'
alias gpush='git push'
```

I know that we did not cover all the commands and options described here. ~~It is because I am lazy.~~ I hope to just wet your appetite and have you do more research!

## Closing Thoughts

I hope that this short introduction into Git has sparked (or reignited) your interest in Git and version control. If this post also provided useful knowledge for you, that is fantastic! The ultimate goal of this blog is to provide valuable information to others.

There is a <a href="https://betterexplained.com/articles/a-visual-guide-to-version-control/" target="_blank" rel="nofollow">series</a> on BetterExplained that gives a deeper dive into both version control and Git that I highly recommend.

I will discuss the branching structure I follow and my thoughts behind it in a future post so stay tuned! Maybe I will also expand on some of the commands and options mentioned in this post. I am a great teaser, huh?

Do you know of any useful but underrated Git commands or options? What are some of your favorite Git aliases and why?
