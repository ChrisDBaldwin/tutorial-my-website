# Intro to Git

Hey! Here's everything you need to get started with Git and GitHub. Watch the video first, check out the infographic, then use this as your cheat sheet.

---

## First-Time Setup

You only do this stuff once.

### 1. Install Git

- **Windows:** [git-scm.com/downloads](https://git-scm.com/downloads) (use the defaults in the installer)
- **Mac:** Open Terminal and type `git --version` — it'll prompt you to install it
- **Linux:** `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora)

### 2. Tell Git Who You Are

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Use the same email as your GitHub account.

### 3. Set Up SSH (so you don't type your password every time)

Generate a key:

```bash
ssh-keygen -t ed25519 -C "you@example.com"
```

Just hit Enter through all the prompts.

Copy the key to your clipboard:

- **Windows:** `cat ~/.ssh/id_ed25519.pub | clip`
- **Mac:** `cat ~/.ssh/id_ed25519.pub | pbcopy`
- **Linux:** `cat ~/.ssh/id_ed25519.pub` and copy it manually

Then go to **GitHub > Settings > SSH and GPG Keys > New SSH Key**, paste it in, and save.

### 4. Test the Connection

```bash
ssh -T git@github.com
```

You should see: `Hi username! You've successfully authenticated...`

You're good to go!

---

## The Main Loop

This is what you'll do every day. Get this down and you're 90% of the way there.

```
edit files -> git add -> git commit -> git push
```

---

## Essential Commands

### Starting a Project

| Command | What It Does |
|---|---|
| `git init` | Create a new repo in the current folder |
| `git clone <url>` | Download an existing repo from GitHub |

### Day-to-Day Workflow

| Command | What It Does |
|---|---|
| `git status` | See what's changed |
| `git add <file>` | Stage a specific file for commit |
| `git add .` | Stage everything |
| `git commit -m "message"` | Save your staged changes with a description |
| `git diff` | See your unstaged changes line-by-line |

### Branching

| Command | What It Does |
|---|---|
| `git branch` | List your branches |
| `git branch <name>` | Create a new branch |
| `git checkout <branch>` | Switch to a branch |
| `git checkout -b <name>` | Create and switch in one step |
| `git merge <branch>` | Merge another branch into your current one |

### Working with GitHub (Remotes)

| Command | What It Does |
|---|---|
| `git remote add origin <url>` | Link your local repo to GitHub |
| `git push` | Upload your commits |
| `git pull` | Download and merge the latest changes |
| `git fetch` | Download changes without merging |
| `git remote -v` | See your linked remotes |

### History and Undoing Mistakes

| Command | What It Does |
|---|---|
| `git log` | View commit history |
| `git log --oneline` | Compact commit history |
| `git restore <file>` | Discard uncommitted changes to a file |
| `git reset HEAD <file>` | Unstage a file |
| `git branch -a` | See all branches (local and remote) |

---

## Quick Example: Your First Repo

```bash
# make a folder and go into it
mkdir my-project
cd my-project

# start a repo
git init

# make a file
echo "hello world" > hello.txt

# stage it, commit it, push it
git add hello.txt
git commit -m "first commit"
git remote add origin git@github.com:yourusername/my-project.git
git push -u origin main
```

That's it. You just put code on the internet.

---

## When Things Go Wrong

- **"I committed the wrong thing"** — `git reset HEAD~1` undoes the last commit but keeps your files
- **"I want to start over on this file"** — `git restore <file>` throws away your changes
- **"I'm on the wrong branch"** — `git stash` your work, switch branches, then `git stash pop`
- **"Merge conflict"** — Open the file, look for the `<<<<<<<` markers, pick what you want to keep, then add and commit

---

If you get stuck, `git status` is your best friend. It always tells you what's going on and usually suggests what to do next.
