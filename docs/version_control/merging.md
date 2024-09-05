# Merging

Alright, so you've made a feature branch, made some meaningful commits, and now you're ready to merge your changes back into the `dev` branch.

You may want to watch this first to get a better understanding of what will follow below: [Git Merge vs. Rebase](https://www.youtube.com/watch?v=zOnwgxiC0OA&list=PLfU9XN7w4tFwKwh_xPSQ_X1-hROQEpHnM&index=6).

## ⬇️ Always Pull Before Merging

Before you merge your changes, make sure you pull the latest changes from the `dev` branch to ensure that you are up-to-date with the latest changes.

```bash
git checkout dev
git pull
```

If you have issues with pulling, chances are you haven't set upstream. You can set the upstream branch by running the following command:

```bash
git branch --set-upstream-to=origin/dev dev
```

## ➿ Rebase Your Feature Branch from the updated `dev` Branch

After pulling the latest changes from the `dev` branch, switch back to your feature branch and rebase it with the updated `dev` branch.

```bash
git checkout <feature_branch>
git rebase dev
```

### Why do we do this?!

It is entirely possible that changes to `dev` may have occurred while you were working on your feature branch. `main` is used as an example below, but the same concept applies to `dev`.

<div style="display: flex; gap: 0.5rem">
    <img style="width: 50%" src="/assets/images/Rebase_Before.png"></img>
    <img style="width: 50%" src="/assets/images/Rebase_After.png"></img>
</div>


## ⚠️ Resolve Conflicts

Now, this may or may not happen, but if there are any conflicts, Git will prompt you to resolve them. 

Here is a useful resource: [Resolve Git MERGE CONFLICTS: The Definitive Guide](https://www.youtube.com/watch?v=Sqsz1-o7nXk)

As per resource, you will have to stage changes and make a new commit to resolve the conflict. Assuming you're not too lazy, you may want to squash the conflict resolution commit with the commit that caused the conflict to keep things clean.


## ✅ Check that all tests pass

Before merging your feature branch into `dev`, make sure that all tests pass. This is to ensure that your changes do not break any existing functionality.

## 📎 Merge Your Feature Branch into `dev`

Once you have resolved any conflicts, you can now merge your feature branch into the `dev` branch.

```bash
git checkout dev
git merge <feature_branch>
```
No issues should happen because you've already resolved any conflicts in the previous step.

## ✍️ Push Your Changes

You can now update the remote repository's `dev` branch with your changes.

```bash
git checkout dev
git push
```

## 🗑️ Delete Your Feature Branch

After merging your feature branch into `dev`, you can delete your feature branch.

```bash
git branch -d <feature_branch>
```

## 🗑️ Delete Remote Feature Branch

If you want to delete the remote feature branch, you can do so by running the following command:

```bash
git push origin --delete <feature_branch>
```