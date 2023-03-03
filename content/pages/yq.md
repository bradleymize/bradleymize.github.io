---
title: jq
date: Last Modified 
permalink: /jq.html
eleventyNavigation:
  key: jq
  title: jq / yq
---

- Get parent node based on presence of child key
  ```bash
  echo "${yaml}" | jq '[.. | select(type == "object" and has("repository")) | (.repository | split("/") | last) + ":" + .tag]'
  ```
- Something else