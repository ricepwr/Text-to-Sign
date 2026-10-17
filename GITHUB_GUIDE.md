# GitHub Beginner Guide for a Two-Person Project

This guide uses **GitHub Desktop**, a free app with buttons instead of commands. It covers setup once, then the routine for every work session.

## Key words

| Word | Meaning |
| --- | --- |
| Repository (repo) | The project folder, stored on GitHub and copied to each computer |
| Clone | Download a copy of the repo to a computer |
| Commit | A saved snapshot of changes, with a short message describing them |
| Branch | A separate line of work, so changes do not disturb the main version until ready |
| Push | Send local commits up to GitHub |
| Pull | Bring the latest GitHub changes down to the computer |
| Pull request (PR) | A request to merge a branch into `main`, where the other person can look first |
| Merge | Combine a branch's changes into `main` |
| Main | The official, working version of the project |

## Part 1: One-time setup

### Both people
1. Create a free account at https://github.com (use any email; note the username).
2. Install **GitHub Desktop** from https://desktop.github.com and sign in with the new account.
3. Install **Python 3.10 or 3.11** and a code editor such as **VS Code** (https://code.visualstudio.com).

### Person 1: create the repository
1. On github.com, click the **+** at the top right, then **New repository**.
2. Name it `asl-to-text`. Choose **Private**. Tick **Add a README file**. Click **Create repository**.
3. On the repo page, click **Add file**, then **Upload files**. Drag in `README.md`, `.gitignore`, `requirements.txt`, and `RESULTS.md` from the starter folder. When asked about replacing the existing README, accept. Click **Commit changes**.
   - If `.gitignore` is hidden on the computer (names starting with a dot are often hidden), turn on "show hidden files" in the file manager, or create it on GitHub: **Add file**, **Create new file**, name it `.gitignore`, paste the contents.
4. Invite the partner: on the repo page go to **Settings**, then **Collaborators**, then **Add people**, and enter the partner's GitHub username.

### Person 2: accept
1. Open the invitation email (or the notification on github.com) and click **Accept invitation**.

### Both people: clone the repo
1. In GitHub Desktop: **File**, **Clone repository**, pick `asl-to-text` from the list.
2. Choose a folder on the computer (keep it outside Dropbox, OneDrive, or Google Drive folders, since syncing tools and Git can conflict), then click **Clone**.
3. Open the folder in VS Code and follow the **Setup** section of `README.md` to create the virtual environment and install packages.

## Part 2: The routine for every work session

1. **Pull first.** In GitHub Desktop click **Fetch origin**. If it says **Pull origin**, click that. This brings in the partner's latest work.
2. **Make a branch** (once per task). Click **Current branch**, then **New branch**, and name it after the task (for example `landmark-extraction`). Click **Create branch**.
3. **Do the work** in VS Code. Save files as usual.
4. **Commit.** Back in GitHub Desktop, the changed files appear on the left. Type a short summary in the box at the bottom left (for example "Add landmark extraction script"), then click **Commit to landmark-extraction**. Commit after each small piece of working progress.
5. **Push.** Click **Publish branch** the first time, or **Push origin** afterward. This uploads the work to GitHub.
6. **Open a pull request** when the task is done: click **Create Pull Request** (GitHub Desktop opens the page on github.com), then click **Create pull request** there.
7. **Merge.** The partner looks over the changes and clicks **Merge pull request**. While learning, merging one's own pull request is fine.
8. **Switch back to main and pull.** Click **Current branch**, choose `main`, then click **Pull origin** so the merged work is on the computer.

## Part 3: Habits that prevent most problems

- Pull before starting, every time.
- Agree on who edits which file. Two people changing the same lines of the same file at the same time causes a merge conflict.
- Commit small and often, with a plain message.
- Keep datasets, videos, and trained models out of Git. The `.gitignore` handles this as long as they live in `data/` or `models/`.
- Never commit passwords or API keys.
- Keep notebooks to one owner each. Notebook files merge badly. Move finished logic into `.py` files under `src/`.

## If something goes wrong

- **"Merge conflict" message:** GitHub Desktop lists the conflicted files and offers **Open in Visual Studio Code**. VS Code highlights both versions and offers **Accept Current**, **Accept Incoming**, or **Accept Both**. After choosing, save, return to GitHub Desktop, and commit.
- **A file was committed by accident (for example a large video):** stop and ask for help before pushing, since removing it afterward takes extra steps.
- **Changes were made on `main` by mistake:** in GitHub Desktop, **Branch** menu, **New branch**; GitHub Desktop offers to move the uncommitted changes to the new branch.

## Optional: command-line version of the routine

```bash
git pull                              # get the latest work
git checkout -b landmark-extraction   # make a branch
# ...edit files...
git add .                             # stage the changes
git commit -m "Add landmark extraction script"
git push -u origin landmark-extraction
# then open the pull request on github.com
git checkout main && git pull         # after merging
```
