---
title: Using Google sheets as a database.
stardate: -270782.041
tags:
  - google-docs
  - spreadsheets
  - database
  - javascript
---

A lot of times when you're building a static website it's easier to just copy and past content in as the project progress than to bother setting up a full on database. Most digital agencies use some kind of 'content matrix', which is just a fancy word for spreadshet, to keep track of all this content. The problem is most of the time this content changes while development is in progress. Content gets out of a sync, the developer wastes time copying and pasting, and human errors occur.

The good news is that Google's spreadsheet tool, has an API that'll spit out json object that represents your spreadsheet.
