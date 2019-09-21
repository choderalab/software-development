# Version control with Git

Version control is important for maintaining the integrity of a software project. Tools like `git`, which is now the 
de facto standard for version control in most places, provide an interactive workflow environment for version control. 

A version control system like git allows
- Tracking versions of files
- Connecting and sharing code between computers using repositories (this is where github comes into the equation)
- Easy mirroring and branching of code bases

On the user side, it provides a context manager, easily allowing you to switch between different versions of code, 
known as branches. It also provides a workflow for extending and modifying existing code:
There are 4 steps to modifying code:

1. branch the code, starting from the current state of the project
2. add changes to it, enabling new features, or modifying existing ones
3. commit, formally declare what changes you want to keep
4. merge, putting your changes back into the original code base.

# Online repositories:

To make collaborating on codebases with other developers easier, it is important to use a central repository service, 
such as Github, or Bitbucket. These websites provide a location to host your repository, and an interface to discuss 
and merge code collaboratively. 

Github provides some easy guides on how to get set up with git and github for the management of your codebases. 

https://guides.github.com/introduction/getting-your-project-on-github/

In a collaborative project, before merging, it is important to discuss with other colleagues whether the changes are 
appropriate. On github, this is done by means of a 
[pull request (PR)](https://help.github.com/articles/about-pull-requests/). 

Below is a basic description of a workflow that uses github.

https://guides.github.com/introduction/flow/index.html

# Recommendations

## What tool should I use?

### For new projects

If you are currently not using any version control for your software project, we recommend using `git`. Many 
repository hosts support git, and it is the easiest way of working with Github.

### For existing projects

You may already have a codebases that uses a different version control system. A very popular version control 
software is Subversion (`svn`). It may be worth investing the effort to switch to `git`. While `git` has a slightly 
steeper learning curve, you may find the features it offers worth it. There are also ways to use `git` with an `svn` 
repository.

https://git-scm.com/book/en/v1/Git-and-Other-Systems-Git-and-Subversion

There are also guides available to help you migrate to `git` entirely:

https://git-scm.com/book/en/v2/Git-and-Other-Systems-Migrating-to-Git

### Mercurial 

If you are using a tool like Mercurial (`hg`), you probably don't need to switch to `git`. There are 
[plugins](http://hg-git.github.io/) available that make it easy to interact with `git` repositories (such as the 
ones hosted on Github).  Although `git` is slightly more powerful out of the box, most of what you'll need will also 
be offered by Mercurial. People also often consider Mercurial to be easier to learn.

## What host should I use?

We strongly recommend using Github.  Github makes collaboration on code very easy, and for small groups it offers 
unlimited private repositories. At the same time, it allows you to publish and share your completed projects with 
the open source community, to increase the impact of your code, and allow for contributions from the community. 
There are many integrations for Github that allow you to automatically test your code, assess the code quality, and 
host documentation, which makes the development even easier.

## What workflow should I adopt?

For small projects with few developers, a simple workflow that uses branches is a great way to keep development 
organized. Take a look at the [Github flow](https://guides.github.com/introduction/flow/index.html) model. In a 
nutshell, new code gets developed on a branch of the repository, and when the code is ready a pull-request is 
opened to discuss the merge with the main branch of the repository. This is a great way to do incremental development 
of the code for projects that have few developers, and a small codebase.

Alternatively, on Github, opening a pull-request from a fork is just as easy, and it is the preferred way of having 
outside collaborators contribute to the codebase. This helps keeping the main code separate, while allowing other 
developers to experiment. Even within the same company or group, you may find that using forks lowers the barrier 
for development. It is a workflow worth considering.

If you're starting a major project with many developers, you should consider the 
[git-flow](http://nvie.com/posts/a-successful-git-branching-model/) model. It is probably too much effort 
for a small project with one or two developers, but it can help to keep a very active large software project 
organized. It provides strategies for maintaining the code and releasing new versions and bugfixes. 

### Example Workflow: GitHub Flow "Branch and Pull Request" OR "Fork and Pull Request"

This is an example work flow which will often be encountered on GitHub. There are two approaches here: 
"Branch and Pull Request" 
and "Fork and Pull Request." Both methods are very similar and differ mainly in level of repository access. 
This example follows 
from the [GitHub Flow introduction](https://guides.github.com/introduction/flow/) which has interactive images. 
These two methods are not exclusive from one another and can work simultaneously with each other.

We'll assume there exists your software project `exampleproject` with the primary `master` branch on which releases 
are built against. 

#### Branch and Pull Request Model
This is a model which is good for a small number of developers which all have write access to the repository. This 
is also the recommended model for your own projects to mitigate possible damage to the `master` branch, which can 
be very hard to fix. 

1. Create a new branch on your local copy, lets call it `awesome_new_feature`
2. Make your changes to the code
    * *Pitfall Warning:* You can make changes before switching branches, but this often leads you to committing directly 
      to master, which is difficult to fix
3. Commit your changes
4. Test locally, repeat previous two steps as needed
5. Push new branch to the repository
6. Create a pull request proposing `awesome_new_feature` be merged into `master`, or whatever branch you want
7. Allow continuous integration tests to run, discuss
8. Repeat step 2 through 7 as needed, skip step 6
    * You don't have to make a new pull request for every push, the pull request will be automatically updated
9. Merge

#### Fork and Pull Request Model

This example is slightly different than the previous model and is better for repositories with many possible 
contributors without write access to the repository, such as users who want to propose bug fixes or features. The 
limited write access, but accepted pull requests from forks encourages user contribution while still retaining 
tight control of the code base.

1. [Fork a repository][github_fork] into your personal account
    * If the repository is `researchgroup/exampleproject`, the fork will be `youruser/exampleproject`
    * The fork will still know of the original remote repository, but will not commit, pull, or push to it by default
2. Repeat steps 1 through 5 from the *Branch and Pull Request Model* above
3. Create a pull request proposing `youruser/exampleproject:awesome_new_feature` be merged into 
   `researchgroup/exampleproject:master`, or whatever branch you want
4. Allow continuous integration tests to run, discuss
5. Repeat step 2 and 4
6. Allow the maintainers of `researchgroup/exampleproject` to merge


# More useful links

The documentation for git:

https://git-scm.com/

A good guide on using git:

https://www.atlassian.com/git/


Some example projects on GitHub that are actively developed:

https://github.com/pandegroup/openmm

https://github.com/numpy/numpy

## Help Make this Page Better

Want to contribute to this repository? Have a suggestion for an improvement?
Spot a typo? We're always looking to improve this document for the betterment of all.

* Please feel free to [open a new issue](https://github.com/choderalab/software-development/issues/new) with your feedback and suggestions!
* Or [make a pull request](https://github.com/choderalab/software-development/compare) from your branch or fork!

|__Previous:__||__Next:__|
|:---|---|---:|
|[Licensing Guidelines](https://github.com/choderalab/software-development/blob/master/LICENSING_GUIDELINES.md)|[Back to Top](https://github.com/choderalab/software-development/blob/master/README.md)|[Python Coding Conventions](https://github.com/choderalab/software-development/blob/master/PYTHON_CODING.md)|

[github_fork]: https://help.github.com/articles/fork-a-repo/