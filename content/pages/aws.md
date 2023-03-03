---
title: AWS
date: Last Modified 
permalink: /aws.html
eleventyNavigation:
  key: aws
  title: AWS
---

* Get resources without a particular tag
  ```bash
  aws resourcegroupstaggingapi get-resources --query 'ResourceTagMappingList[?!not_null(Tags[?Key == `<tag name>`].Value)] | []'
  ```

* Get resources with a specific tag + value
  ```bash
  aws resourcegroupstaggingapi get-resources --tag-filters Key=<tag name>,Values=<tag value>
  ```
