# Getting your code out there: Packaging and Deployment

## Don't expect your users to install prerequisites by hand

Anyone who has tried to compile and install [`scipy`](http://scipy.org/) from source can attest that manually installing complex Python dependencies can be a time-consuming nightmare.
If your code makes use of the many wonderful Python packages out there as dependencies, it can quickly become unmanageable to expect users to install these dependencies by hand.

*Don't* simply list all the "prerequisites" your code requires and expect the user to figure out how to install them.
Users that are new to the Python ecosystem may try to install them in any manner of ways, and it's not guaranteed that they will manage to install fully compatible versions.
It is almost guaranteed they will not enjoy installing a large list of dependencies manually.

The more we, as tool providers, can do to simplify the installation process, the better.
If prospective users can easily install your tool and get up and running quickly, they are much more likely to use your tool, get something done, and cite your work.

## Packaging solutions

### The Python Package Index (PyPI)

If your package is pure Python, it's easy to package and deploy to a very wide audience via the [Python Package Index](https://pypi.python.org/pypi).
This site greatly simplifies installation from the user perspective via the tool [`pip`](https://pip.pypa.io) which is available almost universally in common Python distributions.
Installation of a tool like [`pymbar`](https://github.com/choderalab/pymbar) is simplified to:
```bash
pip install pymbar
```
This automatically installs the specified package and its dependencies---which must also be available through PyPI---into the user's current Python installation.
Note that if this is a *system* Python installation, `pip install <packagename>` may ask for an administrator or root password so that the package can be installed into the system Python installation.
This is highly discouraged: We recommend that, whenever possible, user-space Python installations, such as the [Miniconda minimal Python install](http://conda.pydata.org/miniconda.html) installed into the user's home directory, be used.
The user can also [manage multiple environments this way](http://conda.pydata.org/docs/using/envs.html), in case different incompatible dependency versions are needed for different toolchains.

Packages with compiled components or binary libraries that must be distributed alongside them can generally not be deployed via PyPI.
While this is changing with wider support for Python wheels (see [PEP 427](https://www.python.org/dev/peps/pep-0427/), [PEP 491](https://www.python.org/dev/peps/pep-0491/), and [PEP 513](https://www.python.org/dev/peps/pep-0513/)), the recommended approach for codes that depend on platform-specific libraries is the `conda` scheme described below.
