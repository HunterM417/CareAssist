# Care Assist Contributing Guide #

TODO: A blurb about the project and its goals.

## Getting Started ##

### Tool Versions ###

Particularly for the mobile app, it is important for the development team to use the same tool versions and update in unison.

Development:

- Android 10
- WearOS 2.16
- JDK 14
- Gradle 6.0


We’ll need to get these versions updated to match development versions whenever possible.

This project uses vagrant for box creation and provisioning.

### Get Prerequisites for your platform ###




### Git the code ###
Clone the "CareAssist" repository

    `git clone https://github.com/HunterM417/CareAssist.git`
    
## Committing Code ##

### Workflow ###
We use a rebase workflow so that our repository history is easier to scan and browse (rather than a merge workflow).

The basic overview of the workflow is this:
(assuming you have a freshly cloned copy of the repository on your machine)

1. Switch to the development branch (i.e. staging)

    `git checkout staging`

1. Create a local branch for whatever you're working on

    `git checkout -b my-work`
    
1. Do some work and commit to the local branch
    
    `git commit -m "[CARE-XYZ] doing stuff"`

See the section below on [writing useful commit messages](#useful-commit-messages)

When you have tested and self reviewed your change and determine you are ready to push to the server...

1. Switch to the development branch (i.e. master)

    `git checkout master`
    
1. Pull latest changes from server (should have no conflicts)
    
    `git pull`

1. Switch to your local branch

    `git checkout my-work`
    
1. Rebase onto master (resolving any conflicts)

    `git rebase master`
    
1. Test your changes with the latest server code
    
1. Push to server

    `git push`
    
1. Using GitHub, create a merge request from your branch to the staging branch. Typically, you should assign this merge request to someone other than yourself for review. Unassigned requests will probably be forgotten.

### Tips ###

Try to keep the pull-rebase-merge-commit cycle as small as possible
so that other people won't be able to push in a new commit while you are trying
to push your changes.
If someone does push in a commit after you have done this process it is best to:
1. Reset your releaseBranchName branch to origin/releaseBranchName
2. Start again from step 4

You can bring in server changes at any time by following steps 3-6.
This can help keep any conflicts manageable.

In general, we attempt to divide work pieces into orthogonal/separated, so major conflicts *should be* rare.

You can clean up any history on your local branch work before
pushing it to the server by running an interactive rebase on your local branch
and squashing any commits you don't want.
This can let you make many commits locally, but summarize your changes
for public history on the server.

Make small, single topic commits rather than large, far reaching commits that cover many different features/fixes.

### Useful Commit Messages ###
From https://chris.beams.io/posts/git-commit/
 - Separate subject from body with a blank line
 - Limit the subject line to 50 characters
 - Capitalize the subject line
 - Do not end the subject line with a period
 - Use the imperative mood in the subject line
 - Wrap the body at 72 characters
 - Use the body to explain what and why vs. how
 - Single Issue commit - do one thing in a commit - a single feature, a single bug fix (sometimes closely related bugs in one commit are fine)
 
Above all, keep your messages reasonable. Some of these rules are pedantic and not very important.

#### Additional Resources ####
[Merging vs rebasing] (<https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

[Rebase workflow git](https://randyfay.com/content/rebase-workflow-git)

[Good commit messages](https://chris.beams.io/posts/git-commit/)
