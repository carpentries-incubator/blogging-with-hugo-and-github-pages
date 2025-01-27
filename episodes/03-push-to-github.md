---
title: Push our Hugo site to GitHub
teaching: 1
exercises: 5
---

::::::::::::::::::::::::::::::::::::::: objectives

- Push the Hugo site to GitHub and use a Pull Request to bring it into the `main` branch

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How do we save and track our local changes in `git`?
- How do we send our changes to our GitHub repository?
- How do we open and merge a Pull Request?

::::::::::::::::::::::::::::::::::::::::::::::::::

In this episode, we will push the changes we made in our local repository back to the remote repository on GitHub.

For more detail on the workflows used in this episode, see the [Version Control with Git](https://swcarpentry.github.io/git-novice/) Software Carpentry lesson.

1. First of all, we need to tell `git` to track all of the changes we have created.
  We do this by **adding** them to git's staging area.
  
  ```bash
  git add .
  ```
  
  As we saw before, here the `.` means "please add everything in this current location."

  If you now run `git status` you should see a similar output as below.
  
  ```bash
  git status
  ```
  
  ```output
  On branch setup-hugo
  Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
      new file:   .gitmodules
      new file:   archetypes/default.md
      new file:   config.toml
      new file:   themes/anatole
  ```

2. To tell git to make a snapshot (or "commit") of the current state of our files, we use the `git commit` command, passing the `-m` flag in order to leave a message about what we've changed.
  
  ```bash
  git commit -m "Initial setup of blog site"
  ```
  
  The output should look similar to below.
  
  ```output
  [setup-hugo 62d794e] Initial setup of blog site
   4 files changed, 19 insertions(+)
   create mode 100644 .gitmodules
   create mode 100644 archetypes/default.md
   create mode 100644 config.toml
   create mode 160000 themes/anatole
  ```
  
  Now if we run `git status` again, we should see the message `nothing to commit, working tree clean`

3. Now we push this commit from our local commit up to the GitHub server using the `git push` command.
  In the below command, `origin` is a reference to the original repo we setup on GitHub, and `setup-hugo` represents an instruction to create a new branch on the GitHub-hosted repo with the same name as our locally-created branch.
  
  ```bash
  git push origin setup-hugo
  ```
  
  ```output
  Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
  remote:
  remote: Create a pull request for 'setup-hugo' on GitHub by visiting:
  remote:      https://github.com/HelmUpgradeBot/HelmUpgradeBot.github.io/pull/new/setup-hugo
  remote:
  To https://github.com/HelmUpgradeBot/HelmUpgradeBot.github.io.git
  * [new branch]      setup-hugo -> setup-hugo
  ```

4. If we head back onto GitHub to our repo's page, we should now see a banner informing us that a branch has been updated and providing us with an option to "Compare \& pull request".
  Click that big, green button!

![GitHub repo page with a banner and "Compare \& pull request" button](fig/repo_with_pr_banner.png){alt='GitHub repo page with a banner and "Compare \& pull request" button'}

You will be redirected to GitHub's interface for opening a Pull Request (PR).
Give your PR an informative title and a descriptive summary in the relevant boxes, then click "Create pull request".

If we had any tests for our website, this is where they'd run before we merged the PR.
However, we'll set up our tests next, so go ahead and click "Merge pull request", followed by "Confirm merge".

If you head back over to the repo's landing page, you'll see our changes have now been added to the `main` branch - but that doesn't mean our blog is live and deployed yet!

![The GitHub repo's `main` branch with the hugo files now added to it](fig/updated_repo.png){alt="The GitHub repo's `main` branch with the hugo files now added to it"}

First, let's update our local copy of the repo and then we can add a GitHub Action workflow to automatically deploy our website for us.

In your terminal, run the following `git checkout` and `git pull` commands.

```bash
git checkout main
```

```output
warning: unable to rmdir 'themes/anatole': Directory not empty
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```

Note that, this time, we did not use the `-b` flag in the `git checkout` command because we are **switching to a branch that already exists**, not creating a new one.

```bash
git pull
```

```output
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), 636 bytes | 636.00 KiB/s, done.
From https://github.com/HelmUpgradeBot/HelmUpgradeBot.github.io
   594286e..cd19a8f  main       -> origin/main
Updating 594286e..cd19a8f
Fast-forward
 .gitmodules           | 3 +++
 archetypes/default.md | 6 ++++++
 config.toml           | 3 +++
 themes/anatole        | 1 +
 4 files changed, 13 insertions(+)
 create mode 100644 .gitmodules
 create mode 100644 archetypes/default.md
 create mode 100644 config.toml
 create mode 160000 themes/anatole
```



:::::::::::::::::::::::::::::::::::::::: keypoints

- Local changes are saved and tracked using the `git add` and `git commit` commands
- The remote repository on GitHub is synced with a local repository using `git push`. The reverse sync is achieved with `git pull`.
- A Pull Request can be opened and merged in the GitHub browser interface

::::::::::::::::::::::::::::::::::::::::::::::::::


