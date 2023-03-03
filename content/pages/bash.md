---
title: Bash
date: Last Modified 
permalink: /bash.html
eleventyNavigation:
  key: bash
  title: bash
---

* Edit variable in loop and persist outside
  Don't use pipes, those cause subshells:
  ```bash
  counter=0
  while read -r line
  do
    counter=((counter+1))
  done <<< "${multiLineThing}
  echo "Count: ${counter}"
  ```
