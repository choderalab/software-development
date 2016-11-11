# Licensing Guidelines

When starting a new software project, there are many questions, from goals and milestones to implementation details.
A critical detail is often glossed over: the license terms. While it may seem like a nightmare fit only for a lawyer,
there are several open source licenses that are easy to understand and widely used by the community. To describe them, we'll separate
licenses into two categories:

* [__Permissive__](https://en.wikipedia.org/wiki/Permissive_software_licence): Places no restriction on the use of the code in derivative works, including commercialization. Often only requires citation.

* [__Copyleft__](https://en.wikipedia.org/wiki/Copyleft): Requires that derivative works also be open source.

It is also important to remember that different licenses may not be compatible with each other. For instance, if you use a "copyleft" licensed codebase to develop your codebase, you may not be able to use a permissive license. See below for further discussion of this issue.

**It is also critical to note that having an open source license does not preclude dual licensing, that is, both open source and commercial (with permission).**
Issuing a second license generally requires the approval of all authors, so can be a complex issue (see Relicensing below).

## Recommendations

Because the legal issues associated with maintaining a copyleft license while simultaneously allowing full collaborations can become burdensome, we recommend a permissive license such as the [MIT License](http://choosealicense.com/licenses/mit/).
However, it is important to decide for yourself what priorities you have and what resources you will have available to assist in license management.
Below, we provide a brief overview of several useful licensing options for scientific software.

## Preliminary Resources

For an overview of various licenses for scientific programmers, [this article](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002598) can be useful. For a comparison of many different licenses, we have found [this table](http://choosealicense.com/appendix/) very useful. Some brief descriptions of common licenses are provided below. Finally, the Open Source Initiative (OSI), which is widely trusted to define "open source," can be found [here](https://opensource.org/); its definition of permissible open source licenses is used by many granting agencies (e.g., [the NSF](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1565146)).

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

### GPL

Possibly one of the most well-known copyleft licenses, the GPL, or GNU General Public License, places strong conditions on developers of derivative works. Derivative works must not only be open-source, but must also carry the a compatible license, giving it a "viral" property. So, why would you use this license? If you want to make sure that useful derivatives of your work are freely available to other developers, this may be an appropriate license.

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
It is important to recall that as the developer, you may re-license the code to a group without these restrictions. For a scientific example, the Folding@Home project distributes a binary of a modified version of [gromacs](http://gromacs.org) that includes cryptographic code to prevent tampering or altering scientific results on donor machines; while gromacs is a GPL-licensed software package, Folding@Home has [obtained a special license](https://foldingathome.stanford.edu/support/faq/opensource/) from the gromacs developers for this purpose.

### Changing the license

Sometimes, over the course of a project, the developers may decide that the original license is no longer appropriate. The license can be changed, though, with the consent of the copyright holders. For a list of examples, [the Wikipedia page](https://en.wikipedia.org/wiki/Software_relicensing) is helpful.

### Getting the team on board

In a project with many developers, it can become burdensome to modify the license, or relicense the software. There are solutions, however:

* Permissive licenses such as MIT generally would allow any developer (indeed, anyone) to use the code as she sees fit, thus obviating the legal problem (though not the social one)
* If you're using a copyleft license, but, for instance, want to also offer a commercial license, having developers sign a _Contributor agreement_ can specify when and how these changes can take place.

### Contributor agreement

So, what's a contributor agreement?

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
