# Documentation

## Have a good README

The `README.md` of a GitHub repo is like a welcome mat: It's the first thing you see when you arrive on a project's doorstep.
The easier you can make it for users or other developers to glean important information about your project, the better.

Here are some great examples of `README.md` files:
- [`mdtraj`](https://github.com/mdtraj/mdtraj/blob/master/README.md)
- [`MDAnalysis`](https://github.com/MDAnalysis/mdanalysis/blob/develop/README.rst)
- [`holy-build-box`](https://github.com/phusion/holy-build-box/blob/master/README.md)

Many of these `README.md` files include a series of badges at the top.
These badges are not only visual indicators of certain information---whether the repo is in a healthy state with passing tests, which channels are available for obtain the tool, which version number is current, and how many times the software has been downloaded---they provide quick links to a variety of useful integrated services.

Some useful badges:
- [Travis badge](https://docs.travis-ci.com/user/status-images/)
- [AppVeyor badge](https://www.appveyor.com/docs/status-badges/)
- [pypi version and downloads badges](http://codeinthehole.com/writing/pypi-readme-badges/)
- [Anaconda Cloud version and download badge](https://anaconda.org/anaconda/anaconda/badges)
- [Depsy badge](http://blog.impactstory.org/introducing-depsy/)
- [Zenodo DOI badge](https://guides.github.com/activities/citable-code/)

## Documentation is the primary way to learn about how code works.

There are many tools that can be used to write documentation. The easiest to start with is the GitHub wiki, which uses markdown syntax just like the rest of GitHub.

### GitHub wiki

If you're already hosting your project on [GitHub](http://github.com), perhaps the easiest to start with is [Github wiki](https://help.github.com/articles/about-github-wikis/) which uses the same [GitHub markdown syntax](https://guides.github.com/features/mastering-markdown/).
GitHub wikis are [version controlled](https://help.github.com/articles/viewing-a-wiki-s-history-of-changes/), and can even be [edited like a standard Git repository](https://help.github.com/articles/adding-and-editing-wiki-pages-locally/).

Helpful guide on GitHub wikis:
https://guides.github.com/features/wikis/

Some good examples of wiki-based documentation:
* [`D3.js`](https://github.com/d3/d3/wiki): https://github.com/d3/d3/wiki

### Sphinx

If you need something slightly more powerful, consider using [Sphinx](http://www.sphinx-doc.org/en/1.4.8/), which has excellent support for producing beautiful Python documentation.
From the same documentation source, you can build both HTML (online) and PDF (offline) versions, among [many others supported](http://www.sphinx-doc.org/en/1.4.8/builders.html).

Hosting a [sphinx](http://www.sphinx-doc.org/en/1.4.8/) project can be tricky on its own, but is almost trivial if you have a public GitHub repository, since you can use [Read the Docs](https://docs.readthedocs.io/en/latest/getting_started.html) (RTD), which automatically rebuilds and hosts the documentation every time you commit to your repository.
This [template](https://github.com/readthedocs/template) and this [tutorial](http://www.sphinx-doc.org/en/stable/tutorial.html) can help you easily get started.

If you're using [`conda`](http://conda.pydata.org/docs/) for your code, you may want to check out [this step by step guide](https://github.com/choderalab/Protons/blob/master/howto-documentation.rst) on setting up a `conda` project with [RTD](https://readthedocs.org).

Some good examples of Sphinx documentation:

* Sphinx docs, hosted on Read the Docs: [protons](http://protons.readthedocs.io) | [ensembler](http://ensembler.readthedocs.io)
* Sphinx docs, built by travis and hosted on S3: [openmm](http://docs.openmm.org/7.1.0/userguide/index.html) | [mdtraj](http://mdtraj.org/) | [pymbar](http://pymbar.org/) | [yank](http://getyank.org) | [pymc](https://github.com/pymc-devs/pymc/tree/master/docs)

### Other documentation schemes

* [readme.io](http://readme.io): A collaborative system for writing documentation
* [GitBook](https://www.gitbook.com): An online collaborative publishing toolchain

## Clear examples encourage use of code

Almost nobody reads the complete user documentation for a tool before jumping in.
Attention spans are limited; if it takes more than a few minutes to figure out how to accomplish the desired action with a new code---especially if that action is perceived as common---it's likely the user will give up and try a different approach.

Many users---yourself included---find the easiest way to get started with a new code is to try out a working example similar to the task of interest and then tweak things from there.
_Clear, simple, working examples are the quickest way to get someone using your code._

Good examples of good examples:
* [mdtraj](http://mdtraj.org) has a great [page of examples](http://mdtraj.org/1.8.0/examples/index.html) to help users dive right in.
* [MDAnalysis](http://www.mdanalysis.org/) starts with a [great simple example](http://www.mdanalysis.org/pages/basic_example/) to illustrate how easy it is to use.

## Changelogs

Documenting what has changed with each revision or release of your code is an important part of recording when new features were added, existing features were changed, or when critical bugs were fixed.

[autoprotocol](http://autoprotocol.org) has a great example of good [changelog documentation](http://autoprotocol-python.readthedocs.io/en/latest/changelog.html) using [RTD](https://readthedocs.org/)

## Help Make this Page Better

Want to contribute to this repository? Have a suggestion for an improvement?
Spot a typo? We're always looking to improve this document for the betterment of all.

* Please feel free to [open a new issue](https://github.com/choderalab/software-development/issues/new) with your feedback and suggestions!
* Or [make a pull request](https://github.com/choderalab/software-development/compare) from your branch or fork!

|__Previous:__|__Next:__|
|:---|---:|
|[Continuous Integration](https://github.com/choderalab/software-development/blob/master/CONTINUOUS_INTEGRATION.md)|[Python Optimization](https://github.com/choderalab/software-development/blob/master/PYTHON_OPTIMIZATION.md)|
