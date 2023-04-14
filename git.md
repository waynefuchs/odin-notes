# Git Commands

[Think Like (a) Git](https://think-like-a-git.net/sections/about-this-site.html)

## The 80%

A list of the commands that I use the most. None of these files will change anything in the git log nor affect any others working on the project.

| Command                              | Description                                                                     |
| ------------------------------------ | ------------------------------------------------------------------------------- |
| `git clone <repository>`             | pull a remote repository to local disk                                          |
| `git init`                           | Initialize a repository in an existing directory.                               |
| `git add {.\|<file>}`                | Recursively stage all files in the project / specific specified file            |
| `git reset`                          | Reset git to the place it was before adding a file(s)                           |
| `git restore --staged <file>`        | Un-stage a file                                                                 |
| `git status`                         | Show that status of the project files (modified -> staged -> committed)         |
| `git shortlog`                       | Show user + subject line (similar / better than the `--oneline switch`)         |
| `git log`                            | Show a history of commits (add `--oneline` to show only subject)                |
| `git push`                           | push the local disk copy to remote repository (`git push origin main` shortcut) |
| `git commit -m "Add a subject line"` | When a commit only needs the (< 50 char) subject line                           |
| `git commit`                         | open editor to write git commit message.                                        |
| `git rm <file>`                      | remove a file from the repository                                               |

## Git History altering

These commands should be executed with caution, and possibly with communication with other team members. (depending on remote sync status)

| Command                    | Description                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------- |
| 1. `git rebase -i HEAD~2`  | `-i` is interactive (Read the instructions!) (`--root` in place of HEAD~2 for first commit) |
| 2. `git commit --amend`    | Replaces the last commit with a new one.                                                    |
| 3. `git rebase --continue` | Finish the rebase                                                                           |

## Branching

### To Create a new branch

`git checkout -b <new-branch-name>`: Create a branch called new-branch-name and switch to it. Shorthand for:

(1) Create a new branch (2) Switch to the branch

> 1.  `git branch <new-branch-name>`
> 2.  `git checkout <new-branch-name>`

### To merge the changes in the new branch back to main

(1) Switch back to the main branch (2) Merge the branch in

`git checkout main`
`git merge <new-branch-name>`

### To remove the branch when it is no longer needed

Remove a branch when it has been merged.

`git branch -d <branch-name>`

Remove a branch when it has not been merged.

`git branch -D <branch-name>`

## Generate ssh key

`ssh-keygen -t ed25519 -C "github-email-address"`:

    - rename the file in the series of prompts if desired
    - upload the `.pub` to the github ssh credentials page

## Managing remote repositories

`git remote -v`: show remote urls

`git remote set-url origin git@github.com:USERNAME/REPOSITORY.git`: Overwrite remote url for origin. (eg: switch from https to ssh)

Don't do these unless necessary:

    `git remote rm origin`: remove url to remote repository

    `git remote add origin PATH`: add url to remote repository

    `git push --set-upstream origin main`: Tell git to connect main branch to origin. (if origin path has been deleted)

## Change git editor

`git config --global core.editor "vim"`

`git config --global core.editor "code --wait"`

## Mentioned but unknown to me

`git diff`

`git log -p`

`git log --oneline`

`git shortlog`: Group commits by user, showing only the subject line

## Git Commit Guide

1. Limit the subject line to 50 characters
2. Wrap the body at 72 characters
3. Separate subject from body with a blank line
4. Capitalize the subject line
   - Accelerate to 88 mph
   - ~~accelerate to 88 mph~~
5. Do not end the subject line with a period
6. Use the imperative mood in the subject line (Not past tense)
   - Your git subject should always be able to complete this sentence:
     If applied, this commit will **INSERT SUBJECT LINE**
   - This rule is important in the subject, but can be relaxed in the body.
   - Examples (good and bad)
     - Refactor subsystem X for readability
     - Update getting started documentation
     - Remove deprecated methods
     - Release version 1.0.0
     - ~~Fixed bug with Y~~
     - ~~Changing behavior of X~~
     - ~~More fixes for broken stuff~~
7. Use the body to explain what and why vs. how
   - How is for comments

## Writing a README.md

I was perusing the open issues on The Odin Project, an noticed [Github Issue #24019](https://github.com/TheOdinProject/curriculum/issues/24019). I liked what [Arjun Saili](https://github.com/ArjunSaili1) had to say on the matter, and agree that TOP should have a lesson on writing proper `README.md` files. He also has an interesting Github page that showcases his thoughts:

1. Use Media in READMEs (Photos, Videos, Gifs, etc.)
2. Provide information on how to run the project
3. List out the technologies you used
4. (If applicable) Provide information on how to contribute towards the project
5. (if applicable) License information
6. (if applicable) Credit any resources being used (images, starter code, etc.)
7. ~~Explain your development process~~
8. ~~Explain your motivation behind the project~~

I somewhat disagree with #7 and #8 (I moved them to the end of the list), as that is more in line with a blog rather than source code and are especially not as relevant to an assigned project for a coding boot camp.
