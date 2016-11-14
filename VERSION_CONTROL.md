# Version control with Git

Version control is important for maintaining the integrity of a software project. Tools like `git`, which is now the de facto standard for version control in most places, provide an interactive workflow environment for version control. 

A version control system like git allows
- Track versions of files
- Connect and share code between computers using repositories (this is where github comes into the equation)
- Easy mirroring and branching of code bases

On the user side, it provides a context manager, easily allowing you to switch between different versions of code, known as branches. It also provides a workflow for extending and modifying existing code:
There are 4 steps to modifying code:

1. branch the code, starting from the current state of the project
2. add changes to it, enabling new features, or modifying existing ones
3. commit, formally declare what changes you want to keep
4. merge, putting your changes back into the original code base.

# Online repositories:

To make collaborating on codebases with other developers easier, it is important to use a central repository service, such as Github, or Bitbucket. These websites provide a location to host your repository, and an interface to discuss and merge code collaboratively. 

Github provides some easy guides on how to get set up with git and github for the management of your codebases. 

https://guides.github.com/introduction/getting-your-project-on-github/

In a collaborative project, before merging, it is important to discuss with other colleagues whether the changes are appropriate. On github, this is done by means of a [pull request](https://help.github.com/articles/about-pull-requests/). 

Below is a basic description of a workflow that uses github.

https://guides.github.com/introduction/flow/index.html

# Recommendations

## For new projects

If you are currently not using any version control for your software project, we recommend using `git`. Many repository hosts support git, and it is the easiest way of working with Github. 

## For existing projects

You may already have a codebases that uses a different version control system. A very popular version control software is Subversion (`svn`). It may be worth investing the effort to switch to `git`. While `git` has a slightly steeper learning curve, you may find the features it offers worth it. There are also ways to use `git` with an `svn` repository.

https://git-scm.com/book/en/v1/Git-and-Other-Systems-Git-and-Subversion

There are also guides available to help you migrate to `git` entirely:

https://git-scm.com/book/en/v2/Git-and-Other-Systems-Migrating-to-Git

## Mercurial 
If you are using a tool like Mercurial (`hg`), you probably don't need to switch to `git`. There are [plugins](http://hg-git.github.io/) available that make it easy to interact with `git` repositories (such as the ones hosted on Github).  Although `git` is slightly more powerful out of the box, most of what you'll need will also be offered by Mercurial. People also often consider Mercurial to be easier to learn.

# More useful links

The documentation for git:

https://git-scm.com/

A good guide on using git:

https://www.atlassian.com/git/


Some example projects on Github that are actively developed:

https://github.com/pandegroup/openmm

https://github.com/numpy/numpy


