---
title: Git
date: Last Modified 
permalink: /git.html
eleventyNavigation:
  key: git
  title: git
---

* List pruned branches bash alias
  ```bash
  alias pruned="echo 'Branches with deleted remote:' && git branch -vv | awk '{print \$1,\$4}' | grep 'gone]' | awk '{print \$1}'"
  ```

* Clone shortcut for bitbucket bash alias (for accounts w/ large number of repos)
  ```bash
  clone () {
    cd ~/git
    git clone git@bitbucket.org:<account>/$1.git
    cd $1
  }
  ```
