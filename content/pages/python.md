---
title: Python
date: Last Modified 
permalink: /python.html
eleventyNavigation:
  key: python
  title: Python
---

- Mocking the class of a `MagicMock`
  ```python
  mock_thing = MagicMock()
  type(mock_think).__name__ = "MyFakeClass"
  ```