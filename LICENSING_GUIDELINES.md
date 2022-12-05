# Licensing Guidelines

When starting a new software project, there are many questions, from goals and milestones to implementation details.
A critical detail is often glossed over: the license terms.
Explicitly specifying a license that gives your users permission to use, modify, and distribute your work is an important part of the process of reproducible science;
without explicitly specifying a license that describes how your work may be used, you may inadvertently greatly limit the impact of your work because copyright and related law restricts how others can use it.
While licenses may seem to be complex (and boring) legal documents, fortunately, several open source licenses are both widely used by the community and easy to understand.
To describe them, we'll separate licenses into two categories:

* [__Permissive__](https://en.wikipedia.org/wiki/Permissive_software_licence): Places no restriction on the use of the code in derivative works, including commercialization. Often only requires citation.

* [__Copyleft__](https://en.wikipedia.org/wiki/Copyleft): Requires that derivative works also be open source.

It is also important to remember that different licenses may not be compatible with each other. For instance, if you use a "copyleft" licensed codebase to develop your codebase, you may not be able to use a permissive license. See below for further discussion of this issue.

**It is also critical to note that having an open source license does not preclude dual licensing, allowing authors to distribute the code under different licenses to different parties.**
Issuing a second license generally requires the approval of all authors, so can be a complex issue (see Relicensing below).

## The Reproducible Research Standard

In [The Legal Framework for Reproducible Scientific Research](https://ieeexplore.ieee.org/document/4720221/) (PDF available [here](https://web.stanford.edu/~vcs/papers/Legal-STODDEN2009.pdf)), Victoria Stodden introduces the [Reproducible Research Standard](https://web.stanford.edu/~vcs/talks/VictoriaStoddenCommuniaJune2009-2.pdf), a set of recommendations for ensuring that the entire research compendium associated with a computational research product is released in a manner that ensures maximum utility to the research community while ensuring the authors get appropriate credit for their work.
Notably, the research compendium includes heterogeneous components, such as code, documentation, data, associated manuscripts, and auxiliary material, for which different licenses are appropriate.
While software licenses such as the [MIT License](http://choosealicense.com/licenses/mit/) are suitable to describe how code can be used, modified, and redistributed, it does not make sense when applied to documentation or data since these are not code.

## Recommendations

Following the legal guidance of the Reproducible Research Standard, we recommend a permissive license such as the [MIT License](http://choosealicense.com/licenses/mit/) or the [3-Clause BSD License](https://opensource.org/licenses/BSD-3-Clause) for code, and the [Creative Commons By Attribution (CC-BY) 4.0 License](https://creativecommons.org/licenses/by/4.0/) for other components.

## Other Resources

It is important to decide for yourself what priorities you have and what resources you will have available to assist in license management.
Below, we provide a brief overview of several useful licensing options for scientific software.
For an overview of various software licenses aimed at the scientific programmer, [this article](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002598) can be useful.
For a comparison of many different licenses, we have found [this table](http://choosealicense.com/appendix/) very useful.
Finally, the Open Source Initiative (OSI), which is widely trusted to define "open source," can be found [here](https://opensource.org/); its definition of open source licenses is used by many granting agencies (e.g., [the NSF](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1565146)) to define which licenses are permissible under the terms of the grant.

## Permissive Licenses

First, we'll tackle the permissive licenses and give some examples. As mentioned above, these licenses place very few requirements on developers of derivative works or users.

### MIT License

One of the most popular permissive licenses, [the MIT license](http://choosealicense.com/licenses/mit/) has a very simple form:

```
MIT License

Copyright (c) [year] [fullname]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

As you can see, this license grants permission for users and developers to do as they please, and indemnifies the developers against any warranty claims.
Developers of derivative works need only include this notice. This can be ideal for academics, since it allows broad use of new ideas yet still can ensure that the appropriate people receive credit for their works.

[MIT License](http://choosealicense.com/licenses/mit/)

### Apache License 2.0

This license is slightly less permissive than the MIT license above. Among other differences, the [Apache license 2.0](https://www.apache.org/licenses/LICENSE-2.0) requires that derivative works state the changes that were made (though disclosure of source code is not required). Importantly, the Apache license also provides an explicit grant of patent license to users and developers. This prevents developers of derivative works from suing for patent infringement. As the license is more lengthy, we have not reproduced it here.

[Apache License](https://www.apache.org/licenses/)

### BSD License (3-clause, new)

The BSD license is another set of permissive licenses with minor variations between them. The new license has an explicit statement that the authors of the software may not be used to endorse derivative works without permission:

> Neither the name of the copyright holder nor the names of its
> contributors may be used to endorse or promote products derived from
> this software without specific prior written permission.

This is a useful feature for those who are concerned that authors of derivative works may invoke the contributors of the project and damage their reputation in the process.

The BSD license is otherwise similar to the MIT license, and you can [find it here](http://choosealicense.com/licenses/bsd-3-clause/).

*Note:* There are also other BSD licenses not discussed here. More details can be found on this [comparison sheet](http://choosealicense.com/appendix/)

[BSD License (3-clause, new)](http://choosealicense.com/licenses/bsd-3-clause/)

## Copyleft Licenses

While the permissive licenses facilitate broad use of the code, including use in closed-source derivatives, sometimes it is deemed appropriate to incentivize further open source development. The so-called ["copyleft"](https://en.wikipedia.org/wiki/Copyleft) licenses provide exactly that: they use the copyright concept to require that developers of derivative works _also_ open source the derivative work.

While incentivizing further open source development indeed is a worthy goal, it is important to note that many "copyleft" licenses may also dissuade commercial software vendors from relying on your software because of how it might affect their software, so choosing these could in some cases narrow your user base or make commercial vendors more reluctant to collaborate.

### GPL

Possibly one of the most well-known copyleft licenses, the GPL, or GNU General Public License, places strong conditions on developers of derivative works. Derivative works must not only be open-source, but must also carry a compatible license, giving it a "viral" property. So, why would you use this license? If you want to make sure that useful derivatives of your work are freely available to other developers, this may be an appropriate license.

As the GPL is quite lengthy, we have not reproduced it here, but you may find a fuller description [on this page](http://choosealicense.com/licenses/gpl-3.0/)

[GNU Public License (GPL) 3.0](http://choosealicense.com/licenses/gpl-3.0/)

### LGPL

When you are writing a library that will primarily be accessed through an interface (not directly modified by developers), LGPL ("Lesser GNU GPL") can be an attractive license. While this places the same restrictions on works derived through modifications, linking and using the code released under the LGPL is relieved of that requirement. This is often a useful compromise for those writing APIs that will be used via their intended interface. For more details, check [this page](http://choosealicense.com/licenses/lgpl-3.0/).

[Lesser GNU Public License (LGPL) 3.0](http://choosealicense.com/licenses/lgpl-3.0/)

### AGPL

While the GPL and LGPL are intended to ensure that users of code can access the internals, what about code that users never receive? Increasingly, code is being delivered as a service via the Internet, such that users will never see one instruction. The AGPL (GNU Affero General Public License), is intended for this case. It requires that even derivative works only visible through a web service API be made open source. For more information on this license, check [this page](http://choosealicense.com/licenses/agpl-3.0/).

[GNU Affero General Public License (AGPL)](http://choosealicense.com/licenses/agpl-3.0/)

## Relicensing

### Dual license

What if you like the idea of the GPL, but also have commercial partners interested in your code but not the GPL? Or what if your scientific collaborators have written incompatible code?
It is important to recall that as the developer, you may re-license the code to a group without these restrictions. For a scientific example, the Folding@Home project distributes a binary of a modified version of [GROMACS](http://gromacs.org) that includes cryptographic code to prevent tampering or altering scientific results on donor machines; Folding@Home [obtained a special license](https://foldingathome.org/support/faq/opensource) from the GROMACS developers for this purpose, even though GROMACS was then a GPL-licensed software package (and now LGPL-licensed).

### Changing the license

Sometimes, over the course of a project, the developers may decide that the original license is no longer appropriate. The license can be changed with the consent of all copyright holders.
For a list of examples, [the Wikipedia page](https://en.wikipedia.org/wiki/Software_relicensing) is helpful.

### Getting the team on board

In a project with many developers, it can become burdensome to modify the license, or relicense the software. There are solutions, however:

* Permissive licenses such as MIT generally would allow any developer (indeed, anyone) to use the code as she sees fit, thus obviating the legal problem (though not the social one)
* If you're using a copyleft license, but, for instance, want to also offer a commercial license, having developers sign a _Contributor agreement_ can specify when and how these changes can take place.

### Contributor Agreement

Because the consent of all authors is generally needed to issue new licenses, having contributors to your code execute a _Contributor Agreement_ can help ensure that it's easy to issue additional licenses for the code when needed.

From the OSI FAQ:
>Many open source projects will only accept patches (code contributions or documentation contributions) from people who have submitted a legal document known as a contributor agreement. Contributor agreements are not open source licenses — rather, they are a way for the contributor to tell the project that it has the right to distribute the new contributions under the project's existing open source license. (Some contributor agreements also allow for the project to distribute the contributions under other open source licenses too, which enables projects to change their license in the future, and some agreements even allow the project to distribute the contributions under any license the project wants.)

[Source](https://opensource.org/faq#contributor-agreements)

## License Compatibility

Next is the issue of license compatibility. In science, we need to be able to incorporate each other's contributions in order to make full use of the body of scientific knowledge. Certainly, we don't want licensing concerns to interfere with scientific productivity. In general, the permissive licenses are not a serious concern for compatibility with derivative works. However, the copyleft licenses may pose an issue; for more information on compatibility with GPL-style licenses, see [this page](https://www.gnu.org/licenses/license-list.en.html).

## Help Make this Page Better

Want to contribute to this repository? Have a suggestion for an improvement?
Spot a typo? We're always looking to improve this document for the betterment of all.

* Please feel free to [open a new issue](https://github.com/choderalab/software-development/issues/new) with your feedback and suggestions!
* Or [make a pull request](https://github.com/choderalab/software-development/compare) from your branch or fork!

|__Previous:__||__Next:__|
|:---|---|---:|
|[Philosophy and Scope](https://github.com/choderalab/software-development/blob/master/PHILOSOPHY_AND_SCOPE.md)|[Back to Top](https://github.com/choderalab/software-development/blob/master/README.md)|[Structuring Your Project](https://github.com/choderalab/software-development/blob/master/STRUCTURING_YOUR_PROJECT.md)|
