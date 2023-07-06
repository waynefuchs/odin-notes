# Git <!-- omit in toc -->

- [The 80 percent](#the-80-percent)
- [Branching](#branching)
  - [Create Branch Shorthand](#create-branch-shorthand)
  - [Create Branch Longhand](#create-branch-longhand)
  - [Merging](#merging)
  - [Remove a branch](#remove-a-branch)
  - [Previous Commit "Time Travel"](#previous-commit-time-travel)
- [Generate SSH Key for Git](#generate-ssh-key-for-git)
- [Managing remote repositories](#managing-remote-repositories)
  - [Common Remote Commands](#common-remote-commands)
  - [Multiple Remote Repositories](#multiple-remote-repositories)
- [Git History altering](#git-history-altering)
- [Quick Guide (new repo)](#quick-guide-new-repo)
  - [Creating a new repository on the command line](#creating-a-new-repository-on-the-command-line)
  - [Pushing an existing repository from the command line](#pushing-an-existing-repository-from-the-command-line)
- [Change git editor](#change-git-editor)
- [Git Commit Guidelines](#git-commit-guidelines)
- [Writing a README.md](#writing-a-readmemd)
- [Reference Links](#reference-links)
- [Footnotes](#footnotes)

Git is a distributed version control system. It was developed by Linus Torvalds to provide versioning for the linux kernel. It is (basically) time travel and backup for your files.

# The 80 percent

A list of the commands that cover 80% of "normal" daily git usage. The commands listed here are "safe" and will not result in data loss, even through misuse. I say that, knowing there are people on this planet that would take that as a personal challenge. With that said, the largest danger with these commands would be unintentionally committing and pushing something sensitive to a remote repo. (eg: API keys.)

| Command                              | Description                                                                           |
| ------------------------------------ | ------------------------------------------------------------------------------------- |
| `git clone <url>`                    | Clone a remote repository to local disk                                               |
| `git init`                           | Initialize a repository in an existing directory.                                     |
| `git add --patch`                    | Review changes and commit                                                             |
| `git add <path>`                     | Stage the specified `file` or `directory` (recurisvely)                               |
| `git status`                         | Show that status of the project files (modified -> staged -> committed)               |
| `git diff --staged`                  | Show changes between last commit and staged (remove `--staged` for working tree diff) |
| `git reset`                          | Reset git staging (removing everything from "staged" state)                           |
| `git restore --staged <file>`        | Un-stage a file                                                                       |
| `git log --oneline`                  | Quickly view git commits _**with hash**_ (Similar to `git shortlog`)                  |
| `git show <hash>`                    | Look at the `diff` of a particular commit                                             |
| `git push`                           | push the local disk copy to remote repository (`git push origin main` shortcut)       |
| `git commit -m "Add a subject line"` | When a commit only needs the (< 50 char) subject line                                 |
| `git commit`                         | open editor to write git commit message.                                              |
| `git rm <file>`                      | remove a file from the repository                                                     |

> ⓘ Bonus edge-case log command:
>
> `git log --pretty=format:"%h%x09%an%x09%as%x09%s"`
>
> The above line shows a brief log containing `short-hash`, `user`, `date`, and `commit message`. This could be useful if working on a team and you want to see the user along with the hash, and the format string makes this incredibly customizable. This would be best as a bash alias in your `.bashrc` (`alias gitteamlog='git log --pretty=format:"%h%x09%an%x09%as%x09%s"'`)
>
> See the [git-log](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-log.html) manpage (`man git log`) for format string options.

# Branching

## Create Branch Shorthand

```bash
git checkout -b <new-branch-name>   # Create a new branch and switch to it
```

## Create Branch Longhand

```bash
git branch <new-branch-name>        # Create a new branch
git checkout <new-branch-name>      # Switch to it
```

## Merging

In order to merge branches, there are three steps.

```bash
# 1. Switch to the surviving branch (likely `main`)
git checkout <branch>
# 2. Merge the new `feature-branch` into the branch that was just checked out in step 1
git merge <feature-branch-name>
# 3. Delete the feature branch to clean up (optional, but recommended)
git branch -d <feature-branch-name>
```

## Remove a branch

```bash
# This will only work if the branch has been merged with its upstream branch
git branch -d <branch-name>

# This will force a delete, even if the branch has not been merged (**use with caution!**)
git branch -D <branch-name>
```

## Previous Commit "Time Travel"

```bash
# "Time Travel" to a previous commit
git checkout <commit-hash>

# "Come back to the present"
git checkout main
```

# Generate SSH Key for Git

`ssh-keygen -t ed25519 -C "github-email-address"`:

    - rename the file in the series of prompts if desired
    - upload the `.pub` to the github ssh credentials page

# Managing remote repositories

```bash
# Push the current branch to the upstream repo(s)
# This is lazy and deprecated syntax
git push

# Specify a repository to upload to, and the branch that should be synced
# This is the version we should all be using
git push <repository> <branch>
```

Typical use-case would be:

```
git push origin main
```

## Common Remote Commands

| command                           | description                                                       |
| --------------------------------- | ----------------------------------------------------------------- |
| `git remote set-url <name> <url>` | Overwrite URL for the named remote (eg: switch from https to ssh) |
| `git remote rm <name>`            | Remove url/link to default upstream repo                          |
| `git remote add <name> <url>`     | Add `<url>` with remote `<name>`                                  |
| `git remote -v`                   | Show remote named repos with urls                                 |
| `git push -u <name> <branch>`     | Tell git to set the default remote `<name>` and `<branch>`        |

> ⓘ `origin` is the name/alias for "the remote repository that a project was originally cloned from."

> ⓘ The `git push -u` flag is the same as `git push --set-upstream`

## Multiple Remote Repositories

You can have as many remote repositories as you like. Why would you need more than one remote?

1. Website deployment using git remote repositories (`prod`, `dev`, etc)
2. It can be desirable to use more than one git server.
   1. Collaboration
   2. Backup
   3. Flexibility [^1]

[^1]: Here are my reasons for self-hosting a local git server

    - I run a home git server for faster git remote access
    - No storage limitations.
    - As many private repos as I want
    - Code I don't push to github doesn't get assimilated into github's copilot
    - I can mirror select repos to github to maintain those sweet green squares

# Git History altering

⚠️ Don't do this unless you have a good reason _and_ you know what you're doing. These commands should be executed with extreme caution and in communication with other team members. (depending on remote push status)

🚧 TODO: Consider removing this section entirely and linking to official git or github documentation.

| #   | Command                 | Description                                                                                 |
| --- | ----------------------- | ------------------------------------------------------------------------------------------- |
| 1.  | `git rebase -i HEAD~2`  | `-i` is interactive (Read the instructions!) (`--root` in place of HEAD~2 for first commit) |
| 2.  | `git commit --amend`    | Replaces the last commit with a new one.                                                    |
| 3.  | `git rebase --continue` | Finish the rebase                                                                           |

# Quick Guide (new repo)

## Creating a new repository on the command line

```bash
touch README.md
git init
git checkout -b main
git add README.md
git commit -m "first commit"
git remote add origin git@gitea.xeno.org:grok/writing.git
git push -u origin main
```

## Pushing an existing repository from the command line

```bash
git remote add origin git@gitea.xeno.org:grok/writing.git
git push -u origin main
```

# Change git editor

```bash
git config --global core.editor "vim"           # vim (my preference)
git config --global core.editor "pico"          # default
git config --global core.editor "code --wait"   # vscode
```

# Git Commit Guidelines

1. Limit the subject line to 50 characters
2. Wrap the body at 72 characters
3. Separate subject from body with a blank line
4. Capitalize the subject line  
   Accelerate to 88 mph  
   ~~accelerate to 88 mph~~
5. Do not end the subject line with a period
6. Use the imperative mood in the subject line (Avoid past imperative)  
   A git subject should always be able to complete this sentence:  
   **If applied, this commit will `<subject line>`**
7. Use the body to explain what and why (**NOT** how; how is task/ticket/project management trackers)
   - Mention which component changed
   - Declare intent/purpose, not implementation

# Writing a README.md

I have created a [Markdown](./Markdown.md) guide to fill this need.

# Reference Links

| Link                                                                             | Author              | Description                                   |
| -------------------------------------------------------------------------------- | ------------------- | --------------------------------------------- |
| [Git](https://en.wikipedia.org/wiki/Git)                                         | Wikipedia           | An overview of the history and design of git. |
| [Think Like (a) Git](https://think-like-a-git.net/sections/about-this-site.html) | Sam Livingston-Gray | An attempt to thoroughly teach Git            |

# Footnotes
