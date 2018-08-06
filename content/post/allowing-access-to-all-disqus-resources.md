---
author: "Saad Aouad"
date: 2018-08-06
linktitle: Allowing access to all Disqus resources
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Allowing access to all Disqus resources
description: In this post we must see how we can allowing access to all Disqus resources when you have a Content Security Policy header in your web application

weight: 10
---

In this post we must see how we can allowing access to all Disqus resources when you have a `Content Security Policy` header in your web application.

To have a secured web application, you have to add some HTTP headers with security policies, ref https://content-security-policy.com/.

And if you are using Disqus in your web application, Disqus will not be loaded when your app it's deployed and you should see an error in the console like:

```
Refused to frame 'https://disqus.com/' because it violates the following Content Security Policy directive: "frame-src 'self' ...
```

For resolving this issue, you have to add some url's to configure here:

```
https://disqus.com
https://*.disqus.com
https://*.disquscdn.com
```

As shown below.

```
<meta http-equiv="Content-Security-Policy" content="default-src 'self' 'unsafe-inline' https://disqus.com https://*.disqus.com https://*.disquscdn.com ;">
```