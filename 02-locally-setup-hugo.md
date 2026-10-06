---
title: Locally setting up our blog site with Hugo
teaching: 1
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Get a local copy of our repository onto our machines
- Initialise a blog site with Hugo
- Apply a theme to our blog site and set some basic configuration options

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How do we get a local copy of a GitHub repo?
- How do we initialise a blog site using Hugo?
- How do we add and configure a theme for our site?

::::::::::::::::::::::::::::::::::::::::::::::::::

Now we will "clone" our GitHub repository - meaning we will add a copy of it to our local machines.
This is where we will make changes to our repository and initialise a new site using Hugo.

1. Open up your terminal app on your machine

2. Change to a "sensible" directory somewhere on your filesystem
  
  This could be `Desktop`, or maybe you have a folder called `projects` - wherever makes sense to you is the right place to go!
  In this example, we will use `source/github`.
  
  ```bash
  cd source/github
  ```

3. Now clone the repository using the `git clone` command and pasting the address we copied in [step 4 of section 1](01-create-github-repo.md).
  Here we are assuming your GitHub account is called `HelmUpgradeBot` and your repository is called `HelmUpgradeBot.github.io`.
  
  ```bash
  git clone https://github.com/HelmUpgradeBot/HelmUpgradeBot.github.io.git
  ```
  
  ```output
  Cloning into 'HelmUpgradeBot.github.io'...
  remote: Enumerating objects: 4, done.
  remote: Counting objects: 100% (4/4), done.
  remote: Compressing objects: 100% (4/4), done.
  remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
  Receiving objects: 100% (4/4), done.
  ```

4. `git clone` will have created a new directory named after your repo, containing all the files currently in your repo (only the README and LICENSE files so far!).
  You can use the command `ls` to check this.
  Now change into that directory.
  
  ```bash
  cd HelmUpgradeBot.github.io
  ```

5. The first action to take in good [gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) is to create a new branch to work on, so we are not saving our work to the `main` branch until we are ready.
  Let's call our new branch `setup-hugo`.
  
  ```bash
  git checkout -b setup-hugo
  ```
  
  ```output
  Switched to a new branch 'setup-hugo'
  ```

6. And now we use hugo to create our website!
  The below command will auto-generate all of the structure we need to generate html files using hugo's site template.
  The most important file this command will create is `config.toml` which will allow us to control the look and feel of our site.
  (For a tangent into the TOML file format, read this ["Learn X in Y minutes" explainer](https://learnxinyminutes.com/docs/toml/)!)
  
  ```bash
  hugo new site --force .
  ```
  
  ```output
  Congratulations! Your new Hugo site is created in ~/source/github/HelmUpgradeBot/HelmUpgradeBot.github.io.
  
  Just a few more steps and you're ready to go:
  
  1. Download a theme into the same-named folder.
  Choose a theme from https://themes.gohugo.io/ or
  create your own with the "hugo new theme <THEMENAME>" command.
  2. Perhaps you want to add some content. You can add single files
  with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
  3. Start the built-in live server via "hugo server".
  
  Visit https://gohugo.io/ for quickstart guide and full documentation.
  ```
  
  **Note: ** some things to note about the above command:
  
  - The `.` means "Create the site right here please", not in another directory.
  - We needed to use the `--force` flag as hugo would have complained that our directory wasn't empty - remember the README and LICENSE?
    Using `--force` means that hugo will ignore those files when it generates the site.
    

7. Next we will add a theme.
  You can choose any of the free themes available at <https://themes.gohugo.io/> but, for this lesson, we will use [Anatole](https://themes.gohugo.io/anatole/).
  Add the theme to your repository using the `git submodule` command.
  
  ```bash
  git submodule add https://github.com/lxndrblz/anatole.git themes/anatole
  ```
  
  ```output
  Cloning into '~/source/github/HelmUpgradeBot/HelmUpgradeBot.github.io/themes/anatole'...
  remote: Enumerating objects: 1611, done.
  remote: Counting objects: 100% (255/255), done.
  remote: Compressing objects: 100% (177/177), done.
  remote: Total 1611 (delta 120), reused 188 (delta 77), pack-reused 1356
  Receiving objects: 100% (1611/1611), 4.79 MiB | 7.27 MiB/s, done.
  Resolving deltas: 100% (844/844), done.
  ```
  
  **Note: ** now under the `themes/anatole` directory, we will have checked out a single reference of the anatole repository to build the content from.
  
8. Now we need to update `config.toml` to use the theme.
  Open up the file in your favourite text editor.
  This is how you would open it in `nano`.
  
  ```bash
  nano config.toml
  ```
  
  Now add the following line to the bottom of the file.
  
  ```toml
  theme = "anatole"
  ```
  
  While you have the config file open, let's make a few more edits to personalise our site.
  The templates provide a guide on common configuration options - for example, [see Anatole's guide](https://themes.gohugo.io/anatole/#modifying-the-configtoml).
  
  Firstly, I strongly recommend updating the `baseURL` field to be that of our GitHub repository, like so:
  
  ```toml
  baseURL = "https://HelmUpgradeBot.github.io/"
  ```
  
  Another *super useful* field to add here is the one that will enable the rendering of emojis in your posts :wink:
  
  ```toml
  enableEmoji = true
  ```
  
  We are now going to create a new section in our config file called `[params]` and list some more metadata about our site there.
  
  Give your website a cool name in the `title` field, describe what your site is about in the `description` field, and add your name under the `author` field:
  
  ```toml
  [params]
  title = "A Bot with a Blog"
  author = "HelmUpgradeBot"
  description = "Automatic blogging from a GitHub bot"
  ```
  
  All together, your config file should now look like this:
  
  ```toml
  baseURL = "https://HelmUpgradeBot.github.io/"
  languageCode = "en-us"  # Update to "en-gb" if you prefer, or another language!
  theme = "anatole"
  enableEmoji = true
  
  [params]
  title = "A Bot with a Blog"
  author = "HelmUpgradeBot"
  description = "Automatic blogging from a GitHub bot"
  ```
  
  **Make sure to save the file!**
  
  **Note: ** Some of the information you've been asked you to add to your `config.toml` file is theme-specific configuration - i.e. it will be specific to the "anatole" theme and will not work if you swap themes. 
  You should always check the documentation and example site of the theme you wish to use as they will outline what fields can be used and what their expected values will be.
  

9. Now check your site builds by running the below command in your terminal, and then visiting [http://localhost:1313](https://localhost:1313) in your browser.
  
  ```bash
  hugo server
  ```
  
  ```output
Start building sites …
WARN 2021/05/16 21:17:56 found no layout file for "HTML" for kind "home": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2021/05/16 21:17:56 found no layout file for "HTML" for kind "taxonomy": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2021/05/16 21:17:56 found no layout file for "HTML" for kind "taxonomy": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.

                | EN
-------------------+-----
  Pages            |  3
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

 Built in 4 ms
 Watching for changes in ~/source/github/HelmUpgradeBot/HelmUpgradeBot.github.io/{archetypes,content,data,layouts,static}
 Watching for config changes in ~/source/github/HelmUpgradeBot/HelmUpgradeBot.github.io/config.toml
 Environment: "development"
 Serving pages from memory
 Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
 Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
 Press Ctrl+C to stop
  ```

Our blog doesn't look very exciting yet, but it's good to know that it works! Let's save what we have and we will deploy it online in the next episode.

**Close your browser window displaying your website and run <kbd>Ctrl</kbd>\+<kbd>C</kbd> in your terminal to stop the hugo server command.**



:::::::::::::::::::::::::::::::::::::::: keypoints

- Get a local copy of a GitHub repository using the `git clone` command
- Initialise a blog site with hugo using the `hugo new site` command
- Add a blog theme as a submodule using the `git submodule add` command and configure the theme by editing the `config.toml` file

::::::::::::::::::::::::::::::::::::::::::::::::::


