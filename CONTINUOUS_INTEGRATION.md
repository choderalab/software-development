# Continuous Integration

Continuous integration (CI) is the process of methodically merging and testing code from multiple sources in an effort to ensure that all the pieces of a project work well with each other. In practice, CI is typically an automated process which checks newly proposed code from a developer against existing code to ensure the changes do not break what is already in place.

The need for CI comes from multiple developers working on the same complex software project. Developers cannot reasonably maintain complex software with multiple, interdependent features by hand. A developer **could** be responsible for ensuring that every new bit of code, feature, and bug fix does not introduce an error somewhere else in the code or otherwise break the interdependency of the code, however, that is not saying they **should**. Doing so would be a large waste of that developer's time and talent that could be better spent on adding new features or bug fixes. A better option would be to automate this type of code checking in a way that minimizes both developer input and developer time, while also introducing good coding habits.

We provide [several examples](#examples-to-help-you-get-started) if you want to get started right away.

## What should good Continuous Integration look like?

Without going into specific software options, we first consider what good general rules a CI process should have:

1. Complete automation
1. Scheduled and triggered actions
1. Visible status to all developers
1. Visible results to all developers
1. Logged outputs
1. Isolated build and testing environments

Let us cover each of these items in detail.

### Complete automation

CI processes should not involve developer input to execute and run. Once the initial build is set up, CI should act in a way that does not require a developer to manually queue up a check, and/or have to issue individual commands to ensure functionality. Of course, you could allow a developer to queue up a manual job as a debugger, but that should not be the default operating procedure.

### Scheduled and triggered actions (e.g. nightly builds)

The events which cause a CI process to run should be both time-based and developer-action-based. Having both of these events helps reduce errors introduced by developers of your code, and by developers of external code.

A CI process should run regularly on the code base, e.g. every night. This ensures that your codebase still works against external dependencies which may have published changes. Let's take an example of some Python based code which depends on `numpy`. If the developers push a `numpy` build overnight which changes one of the functions that your code relies on, it can cause your code to unexpectedly fail. If you did not have the timed build, there is a chance that this bug would not have been caught until after your new feature was developed, forcing you to go back and redo your work, after you figured out what the new bug was.

Developer actions should automatically trigger a CI process. When a developer wants to add new code, the CI package should verify that the new code will not break anything. This serves not only as a means of bug checking, but also validation that all components of a code continue to work well with each other. Consider the following example of upgrading a codebase from Python 2 to Python 3 compatibility. Beyond syntax changes, there could be much older code in the code base which may unexpectedly break. Even beyond the codebase's functionality, the deployment of your code on your platform may no longer work due to the upgrade. If you don't run CI, you may not detect this until you think you are ready to deploy.

### Status visible to all developers

CI processes are not meant to be hidden actions or secretive black boxes. Developers should know when CI is running so they can see if their proposed code is being tested. Similarly, other developers will want to see if someone is proposing new code that is being tested.

### Results visible to all developers

All developers should see the results of CI processes. This not only helps ensure that new code will likely be good to merge, but it also helps in the debugging process when it does not.

### Output logs

CI process logs should be stored for a length of time. Having a record of past CI runs allows comparison between different instances to debug any issues that may arise. You are not required to keep the logs forever, but you should hang on to them long enough to extract useful analytics over time.

### Isolated build and testing environments

The CI process should be entirely isolated from your production environment. This ensures that tests and debugging are not accidentally pushed to live environments. CI runs can be very frequent and resource-intensive, based on the number of developers and how many tests the CI process runs. CI processes should also be run on separate resources than your live environment to avoid resource drains.

## GitHub Continuous Integration tools for you and your code

Here we cover some CI options which can be integrated right now into your GitHub code! This is by no means an exhaustive list, but GitHub keeps a handy page of programs which can be integrated [here](https://github.com/integrations).

By no means do you need all of these tools on every project. You should consider your individual needs and choose the set of CI tools that work for you.

### Travis

[Travis CI](https://docs.travis-ci.com/) is a platform designed for instant integration to GitHub. You simply add a `.travis.yml` file in the root of a repository you have admin access to, then go to your Travis account and enable Travis on that repository. There are some [GitHub-side setup](https://github.com/integrations/travis-ci) steps to enable Travis on your projects, but it's very straightforward.

Travis primarily works for Unix-based testing, and triggers its runs any time a PR is created **or** updated. There are also settings to build on pushes, and everything is controlled through very simple options on your Travis settings.

Travis will automatically report itself in any PR on GitHub once enabled and you can even restrict the ability to merge a PR if Travis does not pass.

Logs of builds are kept for an extended length of time on Travis which can be compared and debugged by anyone (although only admins have access to manage the builds).

### AppVeyor

[AppVeyor](https://www.appveyor.com/) is a platform very similar to Travis, but it works for Windows builds instead. If you want your code to run on Windows, we highly recommend using this program.

Integration is available through the [GitHub Page](https://github.com/integrations/appveyor)

### CircleCI

[CircleCI](https://circleci.com/) is a CI platform with a few extra features. These features include testing and deployment on mobile platforms (Android and iOS), automatic rounding up of extra files created during build, and automatic dependency resolution.

## Examples to help you get started

Here we provide some references to existing example CI files and scripts that you can copy to help you get started on your own CI. These are actual CI scripts that are used in production software.

One thing to note is that beyond simply "Fetch Code", none of the CI platforms in these examples **do** anything unless told to. In general, these examples all fetch the code, and run some tests which, on fail, generate an error that can cause the CI process itself to fail out and refuse the changes.

CI is not limited to one language!

### Example: Travis CI Compiles and Tests Your Code:


[YANK's Travis-ci file](https://github.com/choderalab/yank/blob/master/.travis.yml) does several things:

1. Pulls the code base down (automatic from Travis, for pull requests its automatically gets the proposed code)
1. Installs a local copy of the code and all its dependencies
1. Runs the package's tests
    * If these tests fail, the CI process fails, as intended
1. Runs the identical process on three versions of Python
1. Invokes a script after success to do some user-defined action.

This is a rather simple example one could use. The Python calls such as `conda` and `pip` are **not** a requirement of the CI platform, but of the project they're applied to.


Another similar example is the [Omnia MD Conda Builder](https://github.com/omnia-md/conda-recipes/blob/master/.travis.yml), which tells Travis to create a [Docker](https://www.docker.com/) image, run the image (which pulls and compiles the code). Its the same basic process, but through a Docker image instead.


### Example: AppVeyor build and install scripts.

[MDTraj's AppVeyor file](https://github.com/mdtraj/mdtraj/blob/master/appveyor.yml) is a very simple file to set up, which in turn invokes a project-specific file to actually run the tests.

This file is a good bare-bones script to get you up and running on CI. It simply sets up two architectures, installs some basic Python needs, then runs a script specific to the repository. AppVeyor, like many other CIs, is designed to read a failure in a script as a failure in the whole CI process, so you don't have to worry about writing scripts which pass a fail state explicitly to AppVeyor.

## Tips for Getting Started with Your CI

1. Start from a working build script from another repository
    * Modify as needed
1. Start with a free option
    * Many CI platforms, especially those with GitHub Integration are free for a small number of repositories
    * Try different ones out, see what works for you and your code
1. Start experimenting with CI and settings
    * Don't be afraid to break something in the CI script! All the suggestions here are isolated environments that are spun up and shut down on demand
    * **Disclaimer**: Scripts you write which actually push to or interact with a live server will still run no matter where they're run from. It's up to your judgment if you want those as part of your CI platform.
1. Start reading the docs for your CI platform
    * The examples here don't even begin to scratch the surface of all the settings you could use
    * Remember that you don't necessarily need all these options to make a good CI environment
1. Start writing tests for CI to run!
    * CI alone cannot fully test your code, its up to you to write the tests CI will run to ensure everything works
1. Start now!
    * CI will save you, and anyone else working on your code so much time, you will wonder why you did not start sooner
    * Given many CI options are free, how easy it is to set up with GitHub Integration, and how low-risk it is, there is no reason not to give CI a try!

## Help Make this Page Better

Want to contribute to this repository? Have a suggestion for an improvement?
Spot a typo? We're always looking to improve this document for the betterment of all.

* Please feel free to [open a new issue](https://github.com/choderalab/software-development/issues/new) with your feedback and suggestions!
* Or [make a pull request](https://github.com/choderalab/software-development/compare) from your branch or fork!

|__Previous:__||__Next:__|
|:---|---|---:|
|[Unit Testing](https://github.com/choderalab/software-development/blob/master/UNIT_TESTING.md)|[Back to Top](https://github.com/choderalab/software-development/blob/master/README.md)|[Documentation](https://github.com/choderalab/software-development/blob/master/DOCUMENTATION.md)|
