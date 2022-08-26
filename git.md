# Git Commands

## The 80%

`git init`: Initialize a repository in an existing directory.

`git add .`: stage all files in the project

`git add <file>`: stage a single file

`git status`: show that status of the project files (modified -> staged -> committed)

`git log`: show a history of commits (add `--oneline` to show only subject)

`git restore --staged <file>`: un-stage a file

`git clone <repository>`: pull a remote repository to local disk

`git push` or `git push origin main`: push the local disk copy to remote repository

`git commit -m "concise descriptive message"`: commit all staged files

`git commit`: open editor to write git commit message.

`git rm <file>`: remove a file from the repository

## Branching

### To Create a new branch

`git checkout -b <new-branch-name>`: Create a branch called new-branch-name and switch to it. Shorthand for:

   (1) Create a new branch (2) Switch to the branch

   > 1. `git branch <new-branch-name>`
   > 2. `git checkout <new-branch-name>`

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
   * Accelerate to 88 mph
   * ~~accelerate to 88 mph~~
5. Do not end the subject line with a period
6. Use the imperative mood in the subject line (Not past tense)
   * Your git subject should always be able to complete this sentence:
     If applied, this commit will **INSERT SUBJECT LINE**
   * This rule is important in the subject, but can be relaxed in the body.
   * Examples (good and bad)
      * Refactor subsystem X for readability
      * Update getting started documentation
      * Remove deprecated methods
      * Release version 1.0.0
      * ~~Fixed bug with Y~~
      * ~~Changing behavior of X~~
      * ~~More fixes for broken stuff~~
7. Use the body to explain what and why vs. how
   * How is for comments
