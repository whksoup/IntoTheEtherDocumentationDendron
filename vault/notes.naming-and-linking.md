---
id: 7a8ae6a4-b61f-4521-9562-2f0ceadede8d
title: Naming and linking
desc: "Note names become URLs, so name for permanence and link with wikilinks."
updated: 1788417991064
created: 1788417991064
tags: [meta, urls]
---

A file named `notes.naming-and-linking.md` publishes at
`/notes/naming-and-linking`. The filename is the hierarchy path is the
identity, so renaming a note changes every link into it — Dendron will offer
to fix references automatically when you rename through the lookup panel,
but it's still worth choosing the slug deliberately once.

Hierarchy segments are lowercase and hyphenated:
`notes.naming-and-linking`, not `Notes.NamingAndLinking`.

## No date prefixes on notes

Dated names suit a journal, where the date is the identity. These notes get
revised, so a date in the name is a lie within a month. Dates live in the
`created` and `updated` frontmatter instead, which Dendron manages for you.

## Link with wikilinks

`[[Three kinds of page|notes.three-kinds-of-page]]` renders as a normal link
and registers in Dendron's link graph. Backlinks and the graph view come
free — nothing to maintain by hand.
