# Git flow

In the Git flow workflow, there are five different branch types:

- Main
- Develop
- Feature
- Release
- Hotfix

## Git Flow: Main Branch

Please note: the main branch is commonly referred to as “master”; we have made an intentional decision to avoid that
outdated term and have chosen to use “main” instead.

The purpose of the main branch in the Git flow workflow is to contain production-ready code that can be released.

In Git flow, the main branch is created at the start of a project and is maintained throughout the development process.
The branch can be tagged at various commits in order to signify different versions or releases of the code, and other
branches will be merged into the main branch after they have been sufficiently vetted and tested.

## Git Flow: Develop Branch

The develop branch is created at the start of a project and is maintained throughout the development process, and
contains pre-production code with newly developed features that are in the process of being tested.

Newly-created features should be based off the develop branch, and then merged back in when ready for testing.

## Git Flow: Supporting Branches

When developing with Git flow, there are three types of supporting branches with different intended purposes: feature,
release, and hotfix.

## Git Flow: Feature Branch

The feature branch is the most common type of branch in the Git flow workflow. It is used when adding new features to
your code.

When working on a new feature, you will start a feature branch off the develop branch, and then merge your changes back
into the develop branch when the feature is completed and properly reviewed.

## Git Flow: Release Branch

The release branch should be used when preparing new production releases. Typically, the work being performed on release
branches concerns finishing touches and minor bugs specific to releasing new code, with code that should be addressed
separately from the main develop branch.

## Git Flow: Hotfix Branch

In Git flow, the hotfix branch is used to quickly address necessary changes in your main branch.

The base of the hotfix branch should be your main branch and should be merged back into both the main and develop
branches. Merging the changes from your hotfix branch back into the develop branch is critical to ensure the fix
persists the next time the main branch is released.

# git merge vs rebase

Git Merge and Git Rebase are both used to combine the changes of branches but in a distinct way.

## Git Merge

For developers using version control systems, merging is a prevalent method. Merging takes the contents of a source
branch and combines them with a target branch, to be more precise. Only the target branch is updated in this process.
The history of the source branch remains similar.

## Git Rebase

Another way to integrate modifications from one branch to another is by Rebase. Rebase compresses all the modifications
into a single patch. The patch is then inserted into the target branch.

## When to use Git Rebase or Git Merge

### Choose Merge

- whenever we want to add changes of a feature branch back into the base branch.
- if you want to keep the same history rather than rewrite it.
- if you want to revert the changes quickly

### Choose Rebase

- whenever we want to add changes of a base branch back to a feature branch.
- squash multiple commits
- reiterate each commit and update the changes
- reverting rebase would be very difficult

## conflicts

Merge conflicts can be an intimidating experience. Luckily, Git offers powerful tools to help navigate and resolve
conflicts. Git can handle most merges on its own with automatic merging features. A conflict arises when two separate
branches have made edits to the same line in a file, or when a file has been deleted in one branch but edited in the
other. Conflicts will most likely happen when working in a team environment.

There are many tools to help resolve merge conflicts. Git has plenty of command line tools. For more detailed
information on these tools visit stand-alone pages for git log, git reset, git status, git checkout, and git reset. In
addition to the Git, many third-party tools offer streamlined merge conflict support features.

## HEAD in Git

A head is simply a reference to a commit object. Each head has a name (branch name or tag name, etc). By default, there
is a head in every repository called master. A repository can contain any number of heads. At any given time, one head
is selected as the “current head.” This head is aliased to HEAD, always in capitals".

Note this difference: a “head” (lowercase) refers to any one of the named heads in the repository; “HEAD” (uppercase)
refers exclusively to the currently active head. This distinction is used frequently in Git documentation.
