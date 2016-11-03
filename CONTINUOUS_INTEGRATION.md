# Continuous Integration (CI)

Continuous integration (CI) is the process of methodical code merging and testing from multiple sources in an
effort to ensure that all code on a project works well with each other. 
CI in practice is typically an automated process which checks newly proposed code from a developer 
against existing code to ensure the changes do not break what is already in place. 

The need for CI comes from multiple developers working on the same complex software project. 
Developers cannot reasonably maintain complex software with multiple, interdependent features 
by hand. A developer **could** be responsible for ensuring that every new bit of code, feature, 
and bug fix does not introduce an error somewhere else in the code or otherwise break 
the interdependency of the code, however, that is not saying they **should**. Doing 
so would be a large waste of that developer's time and talent that could be better 
spent on adding the new features or bug fixes. A better option would be to automate this 
type of code checking in a way that minimizes both developer input, and developer time 
while also introducing good coding habits. 
 
## What should good CI look like?

Without going into specific CI options, we first consider what good general 
rules a CI process should have:

1. Entirely automated process
1. Scheduled and Triggered actions
1. Visible status to all developers
1. Visible results to all developers
1. Logged outputs
1. Isolated build and testing environments

Let us cover each of these items in detail. 

### Entirely Automated Process

CI processes should not involve developer input to execute and run. Once the 
initial build is setup, CI should act in a way that does not require a 
developer to manually queue up a check, and/or have to issue individual 
 commands to ensure functionality. Of course, you could allow a developer 
 to queue up a manual job as a debugger, but that should not be the default 
 operating procedure.
 
### Scheduled and Triggered Actions

The events which cause a CI process to run should be both time based 
and developer action based. Having both of these events helps reduce 
errors introduced by developers of your code, and by developers of 
external code

There should be an interval of time which 
passes that causes an automatic CI process to run on the code base, e.g. 
every night. This ensures that your codebase still works against 
external dependencies which may have published changes. Lets take an 
example of some Python based code which depends on `numpy`. If the 
developers push a `numpy` build overnight which changes one of the functions 
that your code relies on, it can cause your code to unexpectedly fail. 
If you did not have the timed build, there is a chance that this bug 
would not have been caught until after your new feature was developed, 
forcing you to go back and redo your work, after you figured out what 
the new bug was. 
 
Developer actions should automatically trigger a CI process to run. 
When a developer wants to add new code, that code should be verified 
that it will not break anything. This severs not only as a means of bug 
checking, but also validation that all components of a code continue to 
work well with each other. Consider the following example of upgrading a 
codebase from Python 2 to Python 3 comparability. Beyond syntax changes, 
there could be much older code in the code base which may unexpectedly 
break. Even beyond the codebase's functionality, the deployment of your 
code on your platform may no longer work due to the upgrade. If you did 
not run CI, you may not detect this until you think you are ready to 
deploy.

### Visible Status to All Developers

CI process are not meant to be hidden actions or secreative black boxes. 
Developers should know when CI is running so they can see if their 
proposed code is being tested. Similarly, other developers will want 
to see if someone is proposing new code that is being tested.

### Visible Results to All Developers

All developers should see the results of CI processes. This not only 
helps ensure that new code will likely be good to merge, but it also 
helps in the debugging process when it does not.

### Logged Outputs

CI process logs should be stored for a length of time. Having a record of 
past CI runs allows comparison between different instances to debug any 
issues that may arise. It is not required to keep the logs forever, 
but long enough that they can developers can use them if need be.

### Isolated Build and Testing Environments

CI process should be entirely isolated from your production environment. 
This ensures that tests and debugging are not accidentally pushed to 
live environments. CI runs can be very frequent and resource intensive 
based on the number of developers and how many tests CI runs. CI 
processes should be run on separate resources than your live 
environment to avoid resource drains.

## GitHub CI Tools for You and Your Code

Here we cover some CI options which can be integrate right now into your 
GitHub code! This is by no means an exhaustive list, but GitHub keeps 
a handy page programs which can be integrated [here](https://github.com/integrations). 

By no means do you need all of these tools on every project. You should 
consider your individual needs and choose the set of CI tools that 
work for you. 

### Travis

[Travis CI](https://docs.travis-ci.com/) is a platform designed for 
instant integration to GitHub. You simply add a `.travis.yml` file 
in the root of a repository you have admin access to, then go to your 
Travis account and enable Travis on that repository. There are some 
[GitHub side setup](https://github.com/integrations/travis-ci) to enable 
Travis on your projects, but its very strait forward.

Travis primarily works for Unix based testing and triggers its runs 
any time a PR is created **or** updated. There are also settings 
to build on pushes, and everything is controlled through very simple 
options on your Travis settings.

Travis will automatically report itself in any PR on GitHub once enabled 
and you can even restrict the ability to merge a PR if Travis does not 
pass. 

Logs of builds are kept for an extended length of time on Travis which 
can be compared and debugged by anyone (although only admins have 
access to manage the builds).

### AppVeyor

[AppVeyor](https://www.appveyor.com/) is a platform very similar to Travis, but it instead works for 
Windows builds. If you want your code to run on Windows, we highly 
recommend using this program.

Integration is avalable through the [GitHub Page](https://github.com/integrations/appveyor)

### CircleCI

[CircleCI](https://circleci.com/) is a CI platform with a few extra 
features. These features include testing and deployment on mobile platforms (Android 
and iOS), they can automatically round up build artifacts (extra files 
created during build), and automatic dependency resolution to name a few. 
