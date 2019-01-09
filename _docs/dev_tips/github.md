---
title: Github Intro
permalink: /docs/github/
---

###### Written by Josh Beto

## Git intro

Until now, you have most likely been using Cloud9 and zyBooks to save your code for you, but what do you do
when you've realized you have broken a part of your code mid-assignment? For a majority of you, that means
hitting `ctrl+z` until you hopefully come back to the version that isn't broken. Today, you will learn version control,
which is a way of managing different code versions and iterations as you create your programs/applications.

Git is a version-control system for tracking changes in your repository, your project.

## Your first repo

**Step 1:** Create an account on https://github.com/
**Step 2:** Download Git Bash: https://git-scm.com/downloads
**Step 3:** In your account, create a new repository with the 'New repository' button
**Step 4:** Follow the instructions and make sure to initialize the repository with a README.md
 * This creates a repository stored under your account in github's servers.
 * To modify this repository, you need a local copy on your computer
**Step 5:** Go to your terminal, and navigate to a folder that you want to save your repository in
**Step 6:** Do `git clone https://github.com/<Username>/<RepoName>`
 * This will create a local copy on your computer; when you modify this copy, you can *push* the changes to the remote copy on github's servers

 Congratulations, you now have created your first repo!

**NOTE:** The following commands MUST be run inside your git repository. Make sure to navigate to your local copy of the repository!

 ## Your first commit

 In git, you must add your changes using `git add -A` in your command line. The flag `-A` specifies to add ALL changes, you can also specify specific files to add 
 by doing `git add <filename>`. This process of adding files is known as *staging* your changes. Although these changes have been *staged*, they have not been *committed*.
 *Committing* changes saves these changes to your **local** repository state. 

 To commit changes, simply do `git commit -m <message>` where message is a string that you want to specify, such as `git commit -m "My first commit!"`. Once you have made your
 commit, these changes are now saved in your **local repository**. To *push* these changes to the remote repository saved at github's servers, you have to do `git push`.

 Now, these changes have been successfully saved on your local repository, and have been reflected on your remote repository saved at GitHub! You can see your changes
 in your account at github.com.

 ## Pulling changes

 We have now gone over how to push changes to the remote repository, but we haven't covered *pulling* changes from the remote repository to your local repository. 
 Situations where that may happen is when you collaborate with a partner and your partner pushes some changes to your project. To *pull*, or get these changes on
 your local computer, simply do `git pull`.

 ## Branches

 Until now, you have been working on your *master* branch, otherwise known as the main or stable branch. Branches are essentially different versions of your
 repository that represent a specific state, such as *development*, *bugfixes*, etc. When you work on future projects, you want to create your changes in
 a different branch so your clients don't download broken code from *master* as you work and push changes. To make a branch, simply do `git checkout -b <branchName>`, and
 to move from different branches, simply do `git branch <branchName>`.

 This is a lot of information for today's session, so we will continue learning git throughout the week!