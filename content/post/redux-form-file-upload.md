---
author: "Saad Aouad"
date: 2018-05-08
linktitle: Upload file using React and redux-form
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Upload file using React and redux-form
description: This example demonstrates how i can upload a file and post it using React and redux-form

weight: 10
---

This example demonstrates how i can upload a file and post it using `React` and `redux-form`.

If you've setting up `redux-form` with an input `type="file"`, you should have encountered a browser error like the following error on Chrome:

```
Uncaught DOMException: Failed to set the 'value' property on 'HTMLInputElement': 
This input element accepts a filename, which may only be programmatically set to the empty string.
```
For a security reasons, input with `type="file"` don't support setting the value property programmatically, ref https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#File_inputs.

