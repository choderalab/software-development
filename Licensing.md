# Licensing

When starting a new software project, there are many questions, from goals and milestones to implementation details.
But one critical detail is often glossed over: the license terms. While it may seem like a nightmare fit only for a lawyer,
there are several open source licenses that are easy to understand and widely used by the community. To describe them, we'll separate
licenses into two categories:

* Permissive: Places no restriction on the use of the code in derivative works, including commercialization. Often only requires citation.

* Copyleft: Requires that derivative works also be open source.

It is also important to remember that different licenses may not be compatible with each other. For instance, if you use a "copyleft" licensed codebase to develop your codebase, you may not be able to use a permissive license. See below for further discussion of this issue.

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
Developers of derivative works need only include this notice. This is 