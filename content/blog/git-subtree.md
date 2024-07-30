+++
title = "Git Subtree Usage"
date = "2024-07-24"
tags = ["Git"]
type = "post"
+++

# Git Subtree

Git subtree is an alternative to git submodules. Its a way for having a git repo on another git repo.

It works by copying git commits from the child repo to mother repo. Usually we squash these commits to one root commit, but you may omit that to preserve history of child repo on the mother repo.

Since it copies the commits rather than having pointers. After the copying, the child repo can be destroyed and the mother repo will still have the files and will be fully functional.

Git subtree does not require anything on the user side. Only the person who modifies the subtrees needs to know and execute commands.


# Adding subtree to a repo

```
git stash --include-untracked
git subtree add --prefix themes/gokarna https://github.com/526avijitgupta/gokarna.git main --squash
git push
```

This will create a root commit that has all the changes of child repo fully squashed, and a merge commit that merges this root commit to the mother repo.


# Updating subtree to a certain branch/commit

```
git stash --include-untracked
git subtree pull --prefix themes/gokarna https://github.com/526avijitgupta/gokarna.git main --squash
git push
```

This will create a squash commit on the subtree root that has the changes from last known commit to specified commit. And a merge commit that merges the squash commit to the mother repo.

note: If you changed some child files on the mother repo, you may get a merge conflict while running this command. If you don’t care about the changes there, It might be easier to just remove the subtree and add it again.


# Remove Subtree

```
rm themes/gokarna -r -Force
git add .
git commit -m "remove subtree gokarna"
git push
```

Subtrees do not have any hidden files inside the repo. They are just root commits and files. Just delete the files and commit.


# Push Subtree changes to child repo (don’t do it :)

```
git add themes/gokarna
git commit -m "subtree commit"
git push
git subtree push --prefix=themes/gokarna https://github.com/526avijitgupta/gokarna.git main
```

Note: On some cases this may push all the history of the mother repo to child repo. I still don't understand how that might be possible. It might be a typo on my side. Online sources generally suggest not pushing subtree changes directly from mother repo to child repo. But anywho this is how to do it if you like.


# Working on mother repo on child files

So you wanna do some changes on child, and you are on mother repo, what to do?

```
Create a branch to do your changes in on mother repo.
Do your work, Do the changes on child files on mother repo, Create commits.
Test your solution, make sure everything works.
Make another clone of the child repo on your PC.
Copy the changes of child repo from mother repo manually.
Commit changes on child repo in a feature branch
Merge child feature branch to main
Update child subtree on mother to main
Merge feature branch on mother to main
```

