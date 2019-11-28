# Philosophy and Scope

## Who should read this guide?

This guide is intended for anyone diving into writing scientific software for computational chemistry.
While the primary audience is intended to be early-stage graduate students in computational chemistry or biophysics
laboratories that are intending to produce software with a life beyond a single use, we believe that these principles
will also benefit even those intending to write single-use software.
Many research projects tend to grow beyond their original scope, and by adopting good practices from the beginning,
it will be easier to deal with this growth without necessarily having to start from scratch.

Many students coming into computational chemistry graduate programs do not have formal software engineering training.
Our intent with this guide is not to provide a rigorous software engineering education, but to identify the key
time saving concepts and recommendations that we have found to be most useful for developing computational chemistry
code.

While a variety of languages are used for computational chemistry
codes---especially to achieve high performance---we focus on [Python](https://www.python.org/) as a high-level language
to glue everything together.
Python has enormously increased productivity by allowing users to take advantage of all manner of useful libraries,
from [linear algebra](http://www.numpy.org/) to [numerical computing](http://scipy.org/) to
[plotting](http://seaborn.pydata.org/) to [GPU-accelerated simulations](http://openmm.org).
Those just starting out with Python will find the
[Software Carpentry courses](http://swcarpentry.github.io/python-novice-inflammation/) and [MolSSI Educational Resources](https://molssi-education.github.io/resources.html) to be excellent resources.
Programmers with basic Python expertise may find books such as [Fluent Python](https://www.amazon.com/Fluent-Python-Concise-Effective-Programming/dp/1491946008) to be very helpful in exploring the more powerful aspects of the Python language.

## Why encourage standards?

Without discouraging innovation and exploration of new approaches, we hope to encourage laboratories producing modern
computational chemistry software to adhere to some common guidelines for the following reasons:

* __Minimize technical debt.__ Any laboratory where every project has a completely different structure, philosophy,
    language, approach to documentation, testing scheme, and deployment strategy will accumulate a huge amount of
    [technical debt](https://en.wikipedia.org/wiki/Technical_debt), leading to high
    [software entropy](https://en.wikipedia.org/wiki/Software_entropy). This makes it difficult to connect software
    components together (because so many things differ in their structure). It also makes it difficult for laboratory
    members to work together, because both must be familiar with a much broader range of tools that encompass both
    projects. Overall time spent on maintenance does not benefit from economies of scale. And when one member of the
    laboratory leaves, there is the danger that remaining members may not be sufficiently familiar with the software
    development strategy to continue the project.
* __Facilitate collaboration.__ If instead, most projects in a laboratory, or in different laboratories, are organized
    along similar principles, it immediately becomes easier for members to collaborate on shared projects, or to link up
    projects that are organized similarly. Little time is wasted in becoming familiar with other projects because they
    follow similar organizing principles.
* __Minimize barriers to users.__ Software that presents a similar interface to users makes it very easy for users to
    get started with a new piece of software very quickly. For example, the [msmbuilder](http://msmbuilder.org/) and
    [pyemma](http://pyemma.org) projects present similar interfaces to users, both roughly following the
    [scikit-learn](http://scikit-learn.org/) philosophy of how models are fit to data.
* __Encourage interoperability.__ To make software interoperable, data must flow from one tool to another. To avoid
    having to construct bridges between tools from scratch each times, adopting standard ways of exchanging
    information---especially in computational chemistry codes---can make it easy for multiple codes to interoperate
    without special glue code.

## What does this guide contain?

We intend to cover only the most important aspects of the critical components of software development for computational
chemistry, providing pointers for those who wish to read about certain topics in more depth.

## Instant Skeletal Package from a Cookiecutter

The [Molecular Sciences Software Institute (MolSSI)](http://molssi.org) provides a Computational Molecular Sciences (CMS) [cookiecutter](https://github.com/MolSSI/cookiecutter-cms)
for users who want to have an automated fresh Python package created for them which follows the recommendations
presented in this guide.
A [cookiecutter](http://cookiecutter.readthedocs.io) template provides an automated way to set up files and directories inside a git repository tailored to the application of interest in a manner that already has working functionality, making it easy for the developer to dive in and start coding while adhering to best practices.
We highly encourage people to start from this cookiecutter as it automatically creates
the [structure], files for [continuous integration], [documentation], [distribution], [version control],
[licensing], and others, saving 30-60 minutes of work!

The MolSSI CMS Cookiecutter and its two-line installation instructions can be found at:

**[Computational Chemistry Cookiecutter](https://github.com/MolSSI/cookiecutter-cms)**

## Help Make this Page Better

Want to contribute to this repository? Have a suggestion for an improvement?
Spot a typo? We're always looking to improve this document for the betterment of all.

* Please feel free to [open a new issue](https://github.com/choderalab/software-development/issues/new) with your feedback and suggestions!
* Or [make a pull request](https://github.com/choderalab/software-development/compare) from your branch or fork!

|__Previous:__|__Next:__|
|:---|---:|
|[Table of Contents](https://github.com/choderalab/software-development/blob/master/README.md)|[Licensing Guidelines](https://github.com/choderalab/software-development/blob/master/LICENSING_GUIDELINES.md)|


[structure]: https://github.com/choderalab/software-development/blob/master/STRUCTURING_YOUR_PROJECT.md
[continuous integration]: https://github.com/choderalab/software-development/blob/master/CONTINUOUS_INTEGRATION.md
[documentation]: https://github.com/choderalab/software-development/blob/master/DOCUMENTATION.md
[distribution]: https://github.com/choderalab/software-development/blob/master/PACKAGING_AND_DEPLOYMENT.md
[version control]: https://github.com/choderalab/software-development/blob/master/VERSION_CONTROL.md
[licensing]: https://github.com/choderalab/software-development/blob/master/LICENSING_GUIDELINES.md
