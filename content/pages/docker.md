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

* Listing all images in a repository (also works via browser)
  ```bash
  curl -s https://<domain>/v2/_catalog | jq
  ```

* List all tags for an image (newest at top; via browser, newest will be at the bottom)
  ```bash
  curl -s https://<domain>/v2/<image>/tags/list | jq '.tags | reverse'
  ```
