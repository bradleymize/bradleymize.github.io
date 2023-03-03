---
title: Misc
date: Last Modified 
permalink: /misc.html
eleventyNavigation:
  key: misc
  title: Misc
---

* Dark mode overlay. Paste into browser dev tools console
  ```js
  const div = document.createElement("div");
  div.style='width: 100vw;height: 100vh;top: 0;left: 0;position: fixed;pointer-events: none;background: rgba(0,0,0,0.45);'
  document.body.appendChild(div);
  ```

* Alternative dark mode overlay
  ```css
  * {
    color: #fff !important;
    background-color: #333 !important;
  }
  *:hover {
    background-color: #555 !important;
  }
  ```
