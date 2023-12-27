---
layout:       post
title:        "Internet-Draft: draft-rathnayake-xml2rfc-unicode"
description:  "I-D about how xml2rfc outputs various Unicode characters"
date:         2023-12-27 23:23:23
categories:   internet-draft i-d draft xml2rfc ietf
---

[xml2rfc](https://github.com/ietf-tools/xml2rfc/) is the tool used to generate
[RFC](https://en.wikipedia.org/wiki/Request_for_Comments) and
[Internet-Drafts (I-D)](https://en.wikipedia.org/wiki/Internet_Draft).
xml2rfc converts XML documents to various formats like HTML, PDF and text.
The [draft-rathnayake-xml2rfc-unicode](https://datatracker.ietf.org/doc/draft-rathnayake-xml2rfc-unicode/)
is an experiment to see how various Unicode characters are represented in those
various output formats.

I used a [couple of Python scripts](https://github.com/kesara/xml2rfc-unicode/)
to generate a list of Unicode characters and the Unicode blocks that they
belong to.
Then these were embedded in my draft XML with another Python script.

The first revision I-D is available in various formats:
 * [HTML](https://www.ietf.org/archive/id/draft-rathnayake-xml2rfc-unicode-00.html)
 * [text](https://www.ietf.org/archive/id/draft-rathnayake-xml2rfc-unicode-00.txt)
 * [PDF](https://github.com/kesara/xml2rfc-unicode/raw/main/draft-rathnayake-xml2rfc-unicode-00.pdf)
 * [PDF (HTMLized)](https://datatracker.ietf.org/doc/pdf/draft-rathnayake-xml2rfc-unicode-00)
