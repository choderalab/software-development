# Continuous Integration (CI)

* What is CI? 
Continuous integration (CI) is the process of methodical code merging and testing from multiple sources in an
effort to ensure that all code on a project works well with each other. 
CI in practice is typically an automated process which checks newly proposed code from a developer 
against existing code to ensure the changes do not break what is already in place. 

* Why do we need CI
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

#. Entirely automated process
#. Scheduled and Triggered actions
#. Visible status to all developers
#. Visible results to all developers
#. Logged outputs
#. Isolated build and testing environments

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
 
 



# SCRATCH SPACE, remove for final
* What is CI?
* Why do we need CI?
* What should abstract good CI look like?
 * Best Practices?
* What tools are out there right now?
* What do we recommend?
 * As it pertains to GitHub