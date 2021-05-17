---
title: "Create and Setup your blog repository on GitHub"
teaching: 1
exercises: 10
questions:
- "How do we set up a GitHub repository for blogging?"
objectives:
- "Create a repository on GitHub ready for hosting a blog site"
keypoints:
- "Blog sites hosted on GitHub usually have the repo name `USERNAME.github.io`"
---

In this first episode, we will create the repository that will host our website on GitHub.
We will do this entirely in the browser and we will also assume that your GitHub account is called `HelmUpgradeBot`.

1. Go to <https://github.com> and sign in to your account
2. In the top, right-hand corner of the browser, click the plus `+` symbol and select "New repository" from the dropdown menu.
3. Give your repository the name `HelmUpgradeBot.github.io`.
   This is a special GitHub repository that will act as your website.
   Make sure that it is **public**!
   (You can have private GitHub Pages sites, but they cost money!)
    - Also add a README file to your repository and a license (the MIT license has been used in the example below but you might prefer [Creative Commons](https://github.com/idleberg/Creative-Commons-Markdown)).
    - Once you're happy, click "Create repository"

| ![new_repo_page](../fig/create_new_repo.png) |
| :---: |
| Example of how to fill in GitHub's create repository form |

4. Once your GitHub repo has been created, click the large, green "code" button in the top-right, make sure "HTTPS" is selected, and click the clipboard icon to copy the contents of the text box.

| ![github_repo](../fig/copy_repo_url.png) |
| :---: |
| Where to find the address of your GitHub repo |

Next we will make a local copy of this repository and set it up to create a blog site with Hugo.

{% include links.md %}
