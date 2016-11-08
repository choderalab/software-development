# Licensing

When starting a new software project, there are many questions, from goals and milestones to implementation details.
But one critical detail is often glossed over: the license terms. While it may seem like a nightmare fit only for a lawyer,
there are several open source licenses that are easy to understand and widely used by the community. To describe them, we'll separate
licenses into two categories:

* Permissive: Places no restriction on the use of the code in derivative works, including commercialization. Often only requires citation.

* Copyleft: Requires that derivative works also be open source.

It is also important to remember that different licenses may not be compatible with each other. For instance, if you use a "copyleft" licensed codebase to develop your codebase, you may not be able to use a permissive license. See below for further discussion of this issue. **It is also critical to note that having an open source license does not preclude dual licensing, that is, both open source and commercial (with permission)**

For a comparison of many different licenses, we have found [this table](http://choosealicense.com/appendix/) very useful. Some brief descriptions of common licenses are provided below.

## Permissive Licenses

First, we'll tackle the permissive licenses and give some examples. As mentioned above, these licenses place very few requirements on developers of derivative works or users.

### MIT License

One of the most popular permissive licenses, this license has a very simple form:

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

[MIT license description](http://choosealicense.com/licenses/mit/)

### Apache License

This license is slightly less permissive than the MIT license above. Among other differences, the Apache license requires that derivative works state the changes that were made (though disclosure of source code is not required). Importantly, the Apache license also provides an explicit grant of patent license to users and developers. This prevents developers of derivative works from suing for patent infringement. As the license is more lengthy, we have not reproduced it here. For more information about the Apache licnese, [Check here](http://choosealicense.com/licenses/apache-2.0/).

### BSD License (3-clause, new)

The BSD license is another set of permissive licenses with minor variations between them. The new license has an explicit statement that the authors of the software may not be used to endorse derivative works without permission:

>Neither the name of the copyright holder nor the names of its
  contributors may be used to endorse or promote products derived from
  this software without specific prior written permission.
  
  This is a useful feature for those who are concerned that authors of derivative works may invoke the contributors of the project and damage their reputation in the process.
  
  The BSD license is otherwise similar to the MIT license, and you can [find it here](http://choosealicense.com/licenses/bsd-3-clause/). 
  
  NB: There are also other BSD licenses not discussed here. More details can be found on this [comparison sheet](http://choosealicense.com/appendix/)
  
## Copyleft Licenses

While the permissive licenses facilitate broad use of the code, including use in closed-source derivatives, sometimes it is deemed appropriate to incentivize further open source development. The so-called "copyleft" licenses provide exactly that: they use the copyright concept to require that developers of derivative works _also_ open source the derivative work.

### GPL

Possibly one of the most well-known copyleft licenses, the GPL, or GNU General Public License, places strong conditions on developers of derivative works. Derivative works must not only be open-source, but must also carry the a compatible license, giving it a "viral" property. So, why would you use this license? If you want to make sure that useful derivatives of your work are freely available to other developers, this may be an appropriate license.

While this may seem to make your project undesirable from some, e.g., commercial entities' points of view, it is important to recall that as the developer, you may re-license the code to a group without these restrictions. For a scientific example, the Folding@Home project uses GROMACS, a GPL-licensed software package, but does not need to release the source code of the client as they have [obtained special permission](https://foldingathome.stanford.edu/support/faq/opensource/) from the GROMACS developers.

As the GPL is quite lengthy, we have not reproduced it here, but you may find a fuller description [on this page](http://choosealicense.com/licenses/gpl-3.0/)

### LGPL

When you are writing a library that will primarily be accessed through an interface (not directly modified by developers), LGPL ("Lesser GNU GPL") can be an attractive license. While this places the same restrictions on works derived through modifications, linking and using the code released under the LGPL is relieved of that requirement. This is often a useful compromise for those writing APIs that will be used via their intended interface. For more details, check [this page](http://choosealicense.com/licenses/lgpl-3.0/).

### AGPL

While the GPL and LGPL are intended to ensure that users of code can access the internals, what about code that users never receive? Increasinly, code is being delivered as a service via the Internet, such that users will never see one instruction. The AGPL (GNU Affero General Public License), is intended for this case. It requires that even derivative works only visible through a web service API be made open source. For more information on this license, check [this page](http://choosealicense.com/licenses/agpl-3.0/).

## License Compatibility

Last, but certainly not least, is the issue of license compatibility. In science, we need to be able to incorporate each other's contributions in order to make full use of the body of scientific knowledge. Certainly, we don't want licensing concerns to interfere with scientific productivity. In general, the permissive licenses are not a serious concern for compatibility with derivative works. However, the copyleft licenses may pose an issue; for more information on compatibility with GPL-style licenses, see [this page](https://www.gnu.org/licenses/license-list.en.html).
