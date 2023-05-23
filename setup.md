---
layout: page
title: Setup
permalink: /setup/
---

## Files

There are no files required for this lesson. You will create all the files needed.

## Software

git is free and open-source software, available for all major operating systems.

### Installation

If you are working on a Linux or MacOS machine,
[please see here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for git installation instructions.

For Windows machines, we **highly recommend** that you install the Windows Subsystem for Linux (WSL).
WSL installation instructions are [available here](https://neurodatasci-course-2020.netlify.app/setup/). Alternatively, this course can be followed using [Git Bash](https://www.atlassian.com/git/tutorials/git-bash).

GitHub does not require you to download any additional software;
however, you will need to make a GitHub account.
[Please see here](https://github.com/join) to create your account.

Although we will not cover them in this lesson, there are
GitHub desktop clients that you can download to provide a
graphical user interface (GUI) for interacting with git and GitHub.

If you would like to use a desktop client, we recommend:

- [GitHub Desktop](https://desktop.github.com/)
- [GitKraken](https://www.gitkraken.com/)

### Authentication

GitHub strongly recommends using more secure authentication methods. One such method is _SSH key authentication_, which provides a secure and convenient way to access your GitHub repositories. SSH keys use cryptographic key pairs to establish a connection between your local machine and GitHub servers, providing enhanced security.

**To configure GitHub SSH key authentication, follow these steps:**

1. If you don't already have one, generate a new SSH key pair on your local machine by running `ssh-keygen -t ed25519 -C "your@mail.com"`
2. Log in to your GitHub account, navigate to "Settings," and go to "SSH and GPG keys".
3. Click on "New SSH key." Give the new key a title, and paste the content of your public key (`less ~/.ssh/id_ed25519.pub`) to the Key field.
4. Click on "Add SSH key" to save the changes.

(Optional) To make your SSH key easily accessible, you can **configure an SSH agent** on your local machine, which will manage your private keys and enable passwordless authentication when interacting with GitHub. Run `eval "$(ssh-agent -s)"` to start the SSH agent and set up the necessary environment variables, and then run `ssh-add ~/.ssh/id_ed25519` to add your private key to the SSH agent.
