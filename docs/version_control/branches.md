# Branches

## 📋 Branching Strategy

This repository uses a variation of the convention known as [GitFlow](). There are three main kinds of branches:

- `main`
- `dev`
- Feature branches


![GitFlow](../assets/images/GitFlow.svg)

### `main` Branch
- The `main` branch is the primary branch of the repository.
- It should only contain stable code. **Ideally, the repository owner should merge code into this branch at the end of the project to prepare the next year's team.**


### `dev` Branch
- The `dev` branch is for integrating feature branches into. 
- When a feature is complete, it is merged into the `dev` branch.

### Feature Branches
- Each new feature or bug fix should be developed in its own branch, created off the `dev` branch.
- Feature, bugfixes, etc. branches should be named according to the following convention: 
	- `feat/<name>`
	- `fix/<name>`.

Where `<name>` is a short, descriptive name of the feature or bug fix. If it is based off an issue, the name should start wth `#<issue_number>`. For example, `feature/#1-add-login-page`.

## 🚨 Ground Rules 

- **Never** commit directly to the `main` branch.

- **Never** commit directly to the `dev` branch.

- **Always** create a new branch for each new feature or bug fix.

- **One person per branch**. Each team member should work on their own branch. This ensures that there is safety in force pushing to the remote feature branch when necessary.

	- The exception to this is any interactive live-collaboration in which two or more team members are communicating in real time to avoid commit/merge/rebase conflicts.


## ℹ️ Basic Branching Commands

### Create a New Branch
```bash
git checkout -b <branch_name>
```

### Switch to a Branch
```bash
git checkout <branch_name>
```

### List Branches
```bash
git branch
```

### Delete a Branch
```bash
git branch -d <branch_name>
```

