---
title: Docker
date: Last Modified 
permalink: /docker.html
eleventyNavigation:
  key: docker
  title: Docker
---

* Enable bash completion
  ```bash
  curl https://raw.githubusercontent.com/docker/docker-ce/master/components/cli/contrib/completion/bash/docker -o /etc/bash_completion.d/docker.sh
  
  . /etc/bash_completion.d/docker.sh
  ```

* Delete all images containing a string
  ```bash
  docker images | grep <search> | awk '{print $1 ":" $2}' | xargs docker rmi
  ```
