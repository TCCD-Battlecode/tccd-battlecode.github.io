---
layout: default
title: Battlecode Players GitHub Guide
permalink: /github/
---

# Battlecode Player's GitHub Guide

This page provides a quick guide on what you _have to know_ about GitHub to be able to participate. You can also find links below to more comprehensive guides that will allow you to practice with industry standard workflows while you work on your bot armies.

## Comprehensive Guides

* [Writing Semantic Commits](/github/commits/)
* [Snapshotting](/github/snapshotting/)
* [Branching & Merging](/github/branching/)
* [Syncing with GitHub](/github/syncing/)

## Setting Up Your Codebase

In order to best collaborate with your team, I recommend doing setting up your codebase as follows:

### Create Individual Files for Each Function

In the `examplefuncsplayer/bot.py`, there are 4 different functions that you will be concerned with:

* `run_tower()`
* `run_soldier()`
* `run_mopper()`
* `update_enemy_robots()`

You can divide these into separate files, then import them into your `bot.py` file using this syntax:

```python
import run_tower
import run_soldier
import run_mopper
import update_enemy_robots
```

The remaining code in the bot.py, the `turn()` function, can remain the same and call the other functions directly. This will allow each team member to work on individual code files and push their changes to GitHub, without causing a merge conflict.

### GitHub Primer

#### Branches

While working on your code, it is recommended that you create a new branch for the specific _feature_ you are working on. So, if you are working on adding logic to the soldier bot to search for enemies, you could do something like this:

```git
git checkout -b soldier/search-for-enemies
```

This will create a the branch for you, then switch you to that branch. To switch back to `main` (or any other branch that already exists), you would use the following:

```git
git checkout main # or whatever the branch name is
```

#### Committing Your Code

As you write new features into the code, you'll want to create **snapshots** of your code, called commits, periodically. You start this by **staging** the files that you have changed. In this example, we have changed some code in the `bot.py` file in the `examplefuncsplayer` folder.

```git
git add examplefuncsplayer/bot.py

git commit -m "Short message about what you changed"
```

#### Pushing Your Branch

As you are making commits, you can push your code to the GitHub repository to make sure it is backed up, and for your teammates to view it. The first time you push from your branch, you'll need to use special flags to let Git know where to sync:

```git
git push -u origin soldier/search-for-enemies
```

After that, you can push without the flags:

```git
git push
```

When you are ready to have your code merged into the main branch, where the rest of your team can view or work on it, you would use the following commands:

```git
git checkout main

# Ensure your local main is up to date with the remote main
git pull origin main

git merge soldier/search-for-enemies
```

This will merge the changes you made in the `soldier/search-for-enemies` branch into the `main` branch. If you are done with the branch you were previously working on, you can delete it using:

```git
git branch -d soldier/search-for-enemies
```

It is recommended to only use branches for the purpose they were created for. If you need to work on a different feature for the soldier bots, you would want to make a new branch.

#### Syncing With GitHub

Once you have the branch merged, you'll need to add the files, write a commit message, and push them again, this time from the `main` branch:

```git
git push
```

Your teammates can then use `git pull` to download the updates to `main`!
