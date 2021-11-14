---
title: Setup
---
To prepare for this lesson you will need the following tools installed:

- A GitHub Account
  - You can [sign up for free](https://github.com/join)
- A terminal
  - [Linux](https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners)
  - [Mac](https://www.businessinsider.com/how-to-open-terminal-on-mac?r=US&IR=T)
  - Windows: [Linux Bash](https://www.laptopmag.com/uk/articles/use-bash-shell-windows-10) (preferred), [Command Prompt](https://www.howtogeek.com/235101/10-ways-to-open-the-command-prompt-in-windows-10/)
    - If using the command prompt, some of the commands I use below will be different and you may wish to consult this [cheatsheet](http://www.cs.columbia.edu/~sedwards/classes/2015/1102-fall/Command%20Prompt%20Cheatsheet.pdf)
- `git` version control
  - [Installation guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for all three Operating Systems
  - Follow [this guide](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) for one-time `git` setup the first time you use it
- `hugo`
  - [Installation guide](https://gohugo.io/getting-started/installing/) for all three Operating Systems
  - If you are installing on Linux, see the below section on [installing the most recent version](#installing-the-most-recent-version-of-hugo-on-linux).
- A text editor of your choice! Examples:
  - VSCode
  - nano
  - gedit
  - Notepad++
  - emacs
  - vim

## Installing the most recent version of Hugo on Linux

When running `sudo spt-get install hugo` this does not always install the most recent version of hugo.
If you find this is the case, you can try the following steps.

1. Go to <https://github.com/gohugoio/hugo/releases> and find the latest release
2. Download the `.deb` file for Linux according to your architecture.
   This is most likely the file that ends `_Linux-64bit.deb`.
3. Once downloaded, run the following commands to install this version.

   ~~~
   sudo updates && sudo update hugo
   ~~~
   {: .language-bash}

{% include links.md %}
