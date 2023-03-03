---
title: Helm
date: Last Modified 
permalink: /helm.html
eleventyNavigation:
  key: helm
  title: Helm
---

* Trigger deployment restart based on configmap change
  ```yaml
  spec:
    template:
      metadata:
        annotations:
          checksum/someName: {% raw %}{{ include (print $.Template.BasePath "/some-configmap.yaml") . | sha256sum }}{% endraw %}
  ```
