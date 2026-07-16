# DevOps

## How team working on git?
1. You have remote server to store your code (e.g. github)
2. Make sure 'git pull origin main', get the latest official version
3. Create your personal branch/workspace
4. Save snapshots locally by 'git commit'
5. Push your changes to github by 'git push origin my-branch'. (push doesn't mean to merge, it'e like upload my draft to supervisor to review)
6. Github will mark the overlap part, wait for teammate or supervisor to review and approve
7. Now you can use click 'Merge' on github, your branch become part of the main branch
8. Like Step 1, use git pull again, update the latest official version

PS: 
- Github doesn't run your code, doesn't compile your code, doesn't test anything. Even there's no overlap warning, whole repository might fail after merge. 

- Branch is independent pointer, it does NOT know where you merge, and it's still there. 

- Last commit of log  ≠  last commit of main. As long as those commits are NOT merge to main, it's not the latest product. 

## How pull request works?
Think Pull Request is a living conversation between `main` and `your-branch`, it might have error after first apply for pull request, you can keep push your new debug commit on it. Until it's being approved to merge to `main`. 

e.g. <-------see md source file

`
main:    A---B---C---D---E---F---G   ← teammates kept merging here
              \
your branch:   X---Y---Z              ← you've been working here
`

once you submit the pull request, github find out there's no conflict, then it can merge
`
main:    A---B---C---D---E---F---G---M   ← merge commit M combines everything
              \                    /
your branch:   X---Y---Z----------/
`

see md source file----------->


If you want to see the visual commit log of main branch, use this:

`git log --graph --oneline --decorate --all`

## How to deal with branches once problem solved?
Every branches live in 3 place once you create:
1. local branch
2. remote branch
3. local cache / snapshot of the remote

- e.g. (example of code snippet once problem solved)

`git branch -a` // show all local & remote branch

`git branch -d chore/fix-ci-workflow` // delete local

`git push origin --delete chore/fix-ci-workflow` // delete remote

`git fetch --prune` // clean deleting cache

- e.b. (example of creating a new branch with new problem)

`git checkout -b fix/next-description` // create locally

`git push -u origin fix/next-description` // create on remote as backup


## What kind of problem of CI/CD solving?
The software might work on your local, but not work on other environment (OS, JDK version, Gradle version, ...etc)

CI/CD is a assembly line
1. Make sure code build from clean slate / clean environment
2. Run through all the tests

However, during the CI/CD or assembling, all the tests pass does NOT mean the App runs or works correctly. 

## How Github Action works?
GitHub is like a robot monitoring your repository, whether it runs or not, only depends on 'triggers'. And the file path of `.yml` is offical, mandatory path hardcoded by GitHub `.github/workflow/`

The trigger is controlled by `on:` keyword, `on: [push]` which's it runs on each push no matter any branches. 

You can set rule to trigger when it's pull request to main. 