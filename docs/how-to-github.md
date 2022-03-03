# How To GitHub

This small introductory guide aims to introduce GitHub, Git, and ways to get started using these platforms for development.

<!-- ## Contents -->
<!--
-   [Git](#git)
    -   [General Idea](#general-idea)
    -   [How to use Git](#how-to-use-git)
    -   [Workflow](#workflow)
-   [GitHub](#github)
    -   [Issue Tracking](#issue-tracking)
    -   [Pull Requests](#pull-requests)
    -   [Projects](#projects) -->

## [Git](https://git-scm.com/)

<p align="center">
  <img src="/assets/git.svg" height="100" />
</p>

Git is the current industry standard in version control and evidently is used by the majority of development teams around the world. If you are interested in what the differences are between Git and Perforce Helix Core, here is [a little article] from Perforce themselves.

[a little article]: https://www.perforce.com/blog/vcs/git-vs-perforce-how-choose-and-when-use-both

### General Idea

Git version control is based on a tree/graph like structure where their is a concept of a main/master branch, and other branches forming off of it at different points. Each branch, including the main branch, tracks its own history so different developers can work simultainiously on different parts of a project without affecting anothers work in any way. In theory, these branches are eventually merged back into the main branch through a merge or merge request once that part of the software is complete.

<p align="center">
<img src="https://miro.medium.com/max/700/1*9Mj5Ap8HSlor8P0DGlWrzg.png" height="200" alt="Git Tree Diagram" />
</p>

Alternativly, users are able to make copies of the entire repository through what is called a fork, work on their own version, and then merge the changes they made to their own version back into the original repository. This is quite a bit more effort and probably a bit uneccessary for regular development.

The simplest method is to simply work on the main branch itself. This is usually done at the beggining of a project when the codebase is small or nonexistant and chance of collision is small. I often do this when setting up the skeleton of an application or service as to have a substantial base to work from, adding readme information, or if im doing small quick projects that only 1 person is ever going to see. Once their is chance of 2 developers working on the same area of code, this method becomes very messy and can lead to tons of time spent sorting out merge conflicts and overlap.

### How to use Git

Although the default way to use Git is through the command line, there are many great Git GUI's that provide a more intuitive overview of all the commands afforded to the user. Additionally, a code editor makes for a much more ideal interface for the handling of merge conflicts and other more complex versioning actions. For instance, VSCode comes included with its own Git GUI, which can be supplemented with extensions such as GitLens to create a comprehensive tool for managing version control.

### Workflow

The general workflow for a Git controlled project goes something like the following:

1. Use `git clone [url]` to copy an existing Git repository to your machine, or `git init` to initialize a new Git repository. Although there are variations on this these are the most common scenarios in my experience.
2. Use `git branch [branch name]` to create your own branch and `git checkout [branch name]` to access branches.
3. Once you have made changes to a file, first `git add [file]` to add the file and its changes to the commit. Then `git commit -m [commit message]` to commit the added files with a thoughtful message about what those changes are.
4. Once you have 1 or more commits you want to push online, use `git push` to push those changes to the remote repository. Often this is preceded or followed by a `git pull` to pull all the most recent changes if you do not yet have them. If there are any merge conflicts Git will inform you of them and walk you through the process to resolve them.
5. Once you are ready to merge your work into the main branch, `git checkout [main branch]` and then `git merge [your branch]` to merge your branch into the main branch.

There are inifinite variations on this flow however so here is a link to the [GitHub Git cheatsheet](https://training.github.com/downloads/github-git-cheat-sheet.pdf) which lists the commands and a brief description on what they do. But if in doubt, StackOverflow is your best friend.

## [GitHub](https://github.com/)

<p align="center">
<img src="/assets/github.svg" height="200" alt="GitHub Log" />
</p>

GitHub, and similar products such as [GitLab](https://about.gitlab.com/) and [BitBucket](https://bitbucket.org/), are all primarily online hosting platforms for [Git](https://git-scm.com/). However, over the past few years they have expanded to include tools for project management, CI/CD pipelines, documentation hosting, and a plethora of other features which we will touch on.

First and foremost GitHub is used to remotely store your repositories. If you are reading this, you are in such a repository. By default, if a repository or a directory in a repository has a README.md (or readme.md or similar) this will be automagically displayed when you browse to the repository or subdirectory. These README files usually provide information on the repository for anyone who is passing by. These files are written and styled using [Markdown](https://www.markdownguide.org/), here is a GitHub oriented [cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) that I find useful.

GitHub allows you to manage who has access to each repository, see all the commits made on a repository, see all the branches of a repsository, and many other Git based features in a graphical interface.

GitHub also incorperates features to build on the project management workflow, such as issue tracking, project boards, wiki pages, repository security and insights, project artifact and releases, and CI/CD pipeline actions.

### Issue Tracking

GitHub, and most Git platforms, allow for some level of tracking of issues and other work to be done on a project. In GitHub this is kept under the Issues tab. Here you can view, sort, and filter all the issues related to the repository. You can also create new issues here.

Issues can be referenced in other issues, in commits through commit messages, or by commenting on commits in GitHub. This can be done by referencing the issue number in the message or comment `#{issue number}`.

### Pull Requests

Part of the Git flow is to eventually merge work from other branches into the main branch. Pull requests offer an avenue to review and approve a merge for quality purposes or allow those who do not normally have merge privilages to merge their work. This is ideal for sharing knowledge when collaborating on different parts of a project and checking understanding of new contributers. Pull requests have their own thread of comments attached and also allow for adding comments to code snippets so that code can be properly reviewed and discussed.

### Projects

Projects are a Trello/Planner style interface for making Kanban type project tracking boards. These project boards are able to integrate with the tracked issues such that issues act as cards on the board. This process can be automated too in that changes made to the status of the issue can automatically move a card on the project board. This automation comes preset on a few of GitHubs own templates but can also be configured on the Projects page.

This tool is generally more helpful for larger more long term projects where the ability to track work over time is more worthwhile.
