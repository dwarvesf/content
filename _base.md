---
tags:
  - dwarves
  - work
  - home
title: Home
date: 2023-12-11
description: A collection of notes for everything we do and operate at Dwarves. This is where we keep our internal notes.
authors:
  - minhcloud
  - monotykamary
  - hnh
menu: 
toc: false
notice: 
type: 
hide_frontmatter: true
event_date: 
hide_title: true
---
Welcome to Dwarves Notes, a collection of notes for everything we do and operate at Dwarves. Dwarves are a group of technology innovation advocates. This project is a part of our information engine, where we consolidate know-how and expertise from and for our team as part of our MMA system: **Mastery**, **Meaning**, and **Autonomy**.

We believe that behind every success comes great preparation, accumulation and compound every single day. This note repo contains our notes and studies for any upcoming challenges, new tech, hiring, bounty, etc.


![[information_flow.png]]


## Radar Index

<!-- col-2 #1 -->
<!-- radar-latest-1 -->
```dataview
LIST WITHOUT ID "[[" + file.path + "|" + title + "]]"
FROM "radar" AND !"radar/_index" AND !"radar/_base"
LIMIT 5
```
<!-- radar-latest-1 -->
<!-- radar-latest-2 -->
```dataview
LIST WITHOUT ID "[[" + file.path + "|" + title + "]]"
FROM "radar" AND !"radar/_index" AND !"radar/_base"
LIMIT 5
```
<!-- radar-latest-2 -->
<!-- /col-2 #1 -->
## Upcoming Events

```dataview
LIST WITHOUT ID "[[" + file.path + "|" + title + "]] - " + event_date
FROM #event
LIMIT 3
WHERE event_date < date(today)
SORT event_date ASC
WHERE !contains(file.path, "_index") AND !contains(file.path, "_base")
```



## Open Bounty

```dataview
TABLE WITHOUT ID
	"[[" + file.path + "|" + title + "]]" as Title,
	"🧊 " + bounty as "💰 Bounty",
	status as Status,
  join(PICs) as PIC,
  functional as Function
FROM "earn" AND !"earn/_index" AND !"earn/_base"
WHERE title != null AND (status = "Open")
SORT date DESC
```

## Memos

```dataview
LIST WITHOUT ID "[[" + file.path + "|" + title + "]] - " + join(authors, ", ")
FROM "memo" AND !"memo/_index" AND !"memo/_base"
WHERE title != NULL
SORT date DESC
LIMIT 10
```

## Open positions

```dataview
LIST WITHOUT ID "[[" + file.path + "|" + title + "]]"
FROM "hiring/open-positions"
WHERE hiring = true
```
