---
title: Closing Remarks
teaching: 3
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Consolidate and reflect on what we've learned

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What have we learned?
- What are the next steps?

::::::::::::::::::::::::::::::::::::::::::::::::::

So here's what we've achieved over the course of this lesson.

- We've setup a repository on GitHub with a Hugo site template and a theme via a git submodule
- We've added a Continuous Deployment pipeline that automatically builds our website and publishes it to GitHub Pages whenever we merge a change, using GitHub Actions as a vendor
- We've created a new post with Hugo and added content, including updating our profile picture and embedding content from external sources using shortcodes

From here, you can:

- Continue to use the site as it is and begin publishing your blogs
- Further customise your site by editing the `config.toml` file (see the [anatole documentation](https://github.com/lxndrblz/anatole/) and [this config file](https://github.com/sgibson91/sgibson91.github.io/blob/main/config.toml) for examples)
- Or try implementing a new theme from <https://themes.gohugo.io/>!
  You can do this by running the `git submodule add` command again with your new theme and then updating the `config.toml` file.

::::::::::::::::::::::::::::::::::::::  callout

## Using a new theme

Be warned, some settings we've used during this lesson may break when changing themes!
Always check the theme's example documentation!


::::::::::::::::::::::::::::::::::::::::::::::::::

We hope you've enjoyed learning how to get setup with Hugo and GitHub Pages.
Happy blogging!



:::::::::::::::::::::::::::::::::::::::: keypoints

- We've setup a repository on GitHub with a Hugo site template and a theme via a git submodule
- We've added a Continuous Deployment pipeline that automatically builds our website and publishes it to GitHub Pages whenever we merge a change, using GitHub Actions as a vendor
- We've created a new post with Hugo and added content, including updating our profile picture and embedding content from external sources using shortcodes
- The theme can be changed by running a new `git submodule add` command, but the configuration file will need updating

::::::::::::::::::::::::::::::::::::::::::::::::::


