# Licensing

## Law

[Berne Convention](https://en.wikipedia.org/wiki/Berne_Convention) ([1971 revision ratified by Italy](http://www.normattiva.it/uri-res/N2Ls?urn:nir:stato:legge:1978-06-20;399!vig=))

## Helpers

### GitHub

[GitHub created](https://help.github.com/articles/licensing-a-repository/) http://choosealicense.com/

It suggests:
* MIT - as simple and permissive
* Apache 2.0 - as permissive though addressing patents
* GPLv3 - as copyleft and addressing patents

It also [lists licenses for non-software](https://choosealicense.com/non-software/).

### OpenBSD

https://www.openbsd.org/policy.html

For new code it prefers the ISC license in the following [modified wording (additional copyright years should be separated by a comma, e.g. "Copyright (c) 2003, 2004")](https://cvsweb.openbsd.org/cgi-bin/cvsweb/src/share/misc/license.template?rev=OPENBSD_6_3):

```
Copyright (c) YYYY YOUR NAME HERE <user@your.dom.ain>

Permission to use, copy, modify, and distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

It dismisses the Apache 2.0 license as:
* Non-fully permissive, because "some of your rights will terminate if you claim in court that the code violates a patent";
* Unpredictable "because a patent license cannot be granted under Copyright law, but only under contract law ... [that] differs wildly among jurisdictions".

### Free Software Foundation

https://www.gnu.org/licenses/license-list.html

It notes that [the OpenBSD license is the ISC license with the ambiguous "and/or" clarified as "and"](https://www.gnu.org/licenses/license-list.html#ISC).

### tl;drLegal

https://tldrlegal.com/

## How to apply licenses

### Apache 2.0

From https://choosealicense.com/licenses/apache-2.0/

> Create a text file (typically named LICENSE or LICENSE.txt) in the root of your source code and copy the text of the license into the file.
> Note: The Apache Foundation recommends taking the additional step of adding a boilerplate notice to the header of each source file. You can find the notice at the very end of the license in the appendix.

From https://www.apache.org/dev/apply-license.html

> The method described in the appendix is only suitable for copyright owners. ...
> Section 4d of the license provides for attribution notices to be included with a work in a NOTICE file, such that the attribution notices will remain, in some form, within any derivative works. Apache projects MUST include correct NOTICE documents in every distribution.
> ... a correct NOTICE file MUST be included in the same directory as the LICENSE file.
> Each original source document (code and documentation, but excluding the LICENSE and NOTICE files) SHOULD include a short license header at the top.

From https://www.apache.org/legal/src-headers.html#notice and https://www.apache.org/legal/src-headers.html#faq-examplenotice

```
Apache [PRODUCT_NAME]
Copyright [XXXX-XXXX] The Apache Software Foundation

This product includes software developed at
The Apache Software Foundation (http://www.apache.org/).
```

NOTICE non-Apache Foundation examples:
* https://github.com/moby/moby/blob/v17.05.0-ce/NOTICE
* https://github.com/grafana/grafana/blob/v5.1.1/NOTICE.md
