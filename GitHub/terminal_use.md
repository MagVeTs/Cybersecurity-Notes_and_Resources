# How to pull from GitHub and push to GitHub using Terminal

## Cloning a GitHub Repo

Run this only once, when you’re setting up your local copy of the repo:

```
Bash

# clone repo
git clone https://github.com/<GITHUB_ACCOUNT_NAME>/<REPO_NAME>.git
```

This creates a local folder/directory with the same name as the cloned repo and which is connected to your remote GitHub repository.

After this, you do not need to clone again.

---

## When Not to Use `git clone` Again

If you've already run git clone and made changes locally, do not clone again — doing so would:

- Create a new folder with a fresh copy of the repo,

- Leave behind your previous changes in the old folder,

- Possibly cause confusion or duplicated work.

---

## What to Do After Initial Clone

- Change directory to the new directory containing the cloned repo

```
Bash

cd <REPO_NAME>
```

- Once you're inside your project folder, all your work happens there.

- To **pull** latest changes from GitHub:

```
Bash

git pull origin main
```

- To **push** your local changes to GitHub:

```
Bash

git add .

git commit -m "Your commit message"

git push origin main
```

- To create and switch to a new branch:

```
Bash

git checkout -b your-feature-name
```

- To switch back to the main branch:

```
Bash

git checkout main
```

