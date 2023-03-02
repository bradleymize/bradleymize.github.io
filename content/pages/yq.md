---
title: yq
date: Last Modified 
permalink: /yq.html
eleventyNavigation:
  key: yq 
  order: 1
  title: yq
---
(DRAFT) Get parent node based on presence of child key
```bash
echo "${yaml}" | yq '[.. | select(type == "object" and has("repository")) | (.repository | split("/") | last) + ":" + .tag]'
```
