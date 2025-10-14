
# **Clean Sync Cheatsheet – Step by Step**

This is what you will **actually do daily** to keep your branches clean and PR-ready.

---

## **Step 1: Update `develop` and `main` locally**

```bash
git fetch origin
git checkout develop
git pull --ff-only
git checkout main
git pull --ff-only
```

**Explanation / Why:**

1. `git fetch origin` → Downloads the latest commits from remote without merging. Keeps you updated.
2. `git checkout develop` → Switch to your local `develop` branch.
3. `git pull --ff-only` → Update `develop` fast-forward only. No extra merge commits.
4. Same for `main`.

**Deliverable Task:**

* Your local `develop` and `main` must exactly match the remote.
* Take a screenshot of `git log --oneline --graph` showing `develop` aligned with remote.

---

## **Step 2: Rebase your feature branch on up-to-date `develop`**

```bash
git checkout feature/321-recherche-filtrage
git rebase origin/develop
git push --force-with-lease
```

**Explanation / Why:**

1. `git checkout feature/...` → Switch to your feature branch.
2. `git rebase origin/develop` → Move your commits on top of the latest `develop`. Linear history, fewer conflicts.
3. Resolve conflicts if Git stops:

```bash
git status               # see conflicted files
# edit files to fix conflicts
git add path/to/file
git rebase --continue
```

4. `git push --force-with-lease` → Update the remote branch safely after rebase.

**Deliverable Task:**

* Your feature branch is fully rebased.
* Take a screenshot showing your branch **ahead of develop** by your feature commits and ready to push.

---

## **Step 3: Fix a Rebase If Things Go Wrong**

```bash
git rebase --abort
```

**Explanation:**

* Cancels the rebase if it gets too messy.
* Your branch goes back to the state before rebase.

**Deliverable Task:**

* Demonstrate understanding by explaining in a note or screenshot **how you would abort a bad rebase**.

---

## **Step 4: Back-Merge After Release/Hotfix**

```bash
git checkout develop
git merge --no-ff main
git push
```

**Explanation / Why:**

* When you tag a release or hotfix on `main`, you merge it back into `develop`.
* `--no-ff` ensures a **merge commit is created** → explicit history of the release.

**Deliverable Task:**

* Simulate or explain a **back-merge workflow**.
* Screenshot of merge commit showing main → develop.

---


## **Step 6: Pull Request Preparation**

1. Rebase your branch on latest `develop`.
2. Ensure CI is green (tests pass + lint).
3. Open PR to `develop`.
4. Use **Squash & Merge**.

