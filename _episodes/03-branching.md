---
title: "Branching"
teaching: 10
exercises: 10
questions:
- "What is a branch?"
- "How can I merge changes from another branch?"
objectives:
- "Know what branches are and why you would use them"
- "Understand how to merge branches"
- "Understand how to resolve conflicts during a merge"
keypoints:
- "`git branch` creates a new branch"
- "Use feature branches for new ideas and fixes, before merging into `master`"
- "Merging does not delete any branches"
---

## What is a branch?

You might have noticed the term *branch* in status messages:

~~~
$ git status
~~~
{: .language-bash}
~~~
On branch master
nothing to commit (working directory clean)
~~~
{: .output}

and when we wanted to get back to our most recent version of the repository, we
used `git checkout master`.

Not only can our repository store the changes made to files and directories, it
can also store multiple sets of these changed, which we can use and edit and update in parallel. Each of these sets, or parallel instances, is termed a `branch` and `master` is Git's default branch.

A new branch can be created from any commit. Branches can also be *merged*
together.

## Why branching is useful?

Suppose we've developed some software, and now we want to try out some new ideas; however, we're not sure yet whether we'll keep them or not. We
want to create some sort of *experimental state* here to keep our main branch (`master`) clean. This is where *branching* plays a vital role.

We can create a branch, e.g. `feature1`, to keep track of the development of the feature. This will keep all the work-in-progress separate from the `master` branch that contains codes that have already been tested. When we finish developing the feature, and we are sure that we want to include the new feature in our software, we can merge `feature1` with the `master` branch.

After merging `feature1` branch with `master`, git creates a new commit which contains merged files from `master` and `feature1`. **The merged branch is not deleted.** After the merge, we can continue developing (i.e. making commits) along `feature1`.


> ## Exercise: How can John contribute?
> 
> One of our colleagues, John, wants to contribute to the paper, but is not quite sure if it will actually make a publication. So it will be safer to create a branch and carry on working on this "experimental" version of the paper in a branch rather than in the master. So let's get John onboard.
> 
> ~~~
> $ git checkout -b paperWJohn
> ~~~
> {: .language-bash}
> ~~~
> Switched to a new branch 'paperWJohn'
> ~~~
> {: .output}
> 
> We're going to change the title of the paper and update the author list (adding John Smith).
> However, before we get started it's a good practice to check that we're working on the right branch.
> 
> ~~~
> $ git branch			# Double check which branch we are working on
> ~~~
> {: .language-bash}
> ~~~
>   master
> * paperWJohn
> ~~~
> {: .output}
> 
> The * indicates which branch we're currently in. Now let's make the changes to the paper.
> 
> ~~~
> $ nano journal.md		# Change title and add co-author
> $ git add journal.md
> $ git commit			# "Modify title and add John as co-author"
> ~~~
> {: .language-bash}
> 
> If we now want to work in our `master` branch. We can switch back by using:
> 
> ~~~
> $ git checkout master
> ~~~
> {: .language-bash}
> ~~~
> Switched to branch 'master'
> ~~~
> {: .output}
> 
> Notice that the changes that are in the `paperWJohn` branch are not present here. They exist only in that branch! When switching between branches, git literally goes to look for that branch inside of the `.git` directory, and like checking out a book from the library, it checks that state of the filesystem out of the repository to replace the current state.
> 
> 
> To merge the changes that are in this other branch together with your previous work, run
> 
> ~~~
> $ git merge paperWJohn
> ~~~
> {: .language-bash}
> This adds into your current branch the work that was, until now, only on that other branch. And you can keep going from here.
{: .challenge}
