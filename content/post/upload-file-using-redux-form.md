---
author: "Saad Aouad"
date: 2018-05-08
linktitle: Upload file using redux-form
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Upload file using redux-form
description: In this example we will explain how to upload a file using redux-form

weight: 10
---

In this example we will explain how to upload a file using `redux-form`.

If you've setting up `redux-form` with an input `type="file"`, you should have encountered with an error like this:

```
Uncaught DOMException: Failed to set the 'value' property on 'HTMLInputElement': 
This input element accepts a filename, which may only be programmatically set to the empty string.
```
For a security reasons, input with `type="file"` don't support setting the value property programmatically, ref <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#File_inputs" target="_blank" rel="noopener noreferrer">developer.mozilla.org/en-US/docs/Web/HTML/Element/input#File_inputs</a>.

To handle this warning, it's necessary to set the input value to `null` or remove it to prevent React from trying to set the `value` property on the DOM Input Element:

```
import React from 'react';
import { Field, reduxForm } from 'redux-form';
// ...
<Field name="picture" component="input" type="file" value={null} />
// ...
```

Now we can update the value of `picture` field using method `PATCH`. So let’s start with implement a redux action for that:

```
// updatePicture.js

export const updatePicture = values => dispatch => {
  const data = new FormData();

  // Don't send the data until a file has been loaded
  if (typeof values.picture !== 'string' && values.picture !== null) {
    data.append('picture', values.picture[0]);
  }

  dispatch({
    types: [
      'UPDATE_PICTURE_REQUEST',
      'UPDATE_PICTURE_SUCCESS',
      'UPDATE_PICTURE_FAILURE',
    ],
    config: {
      url: 'http://example.com/update-picture/',
      method: 'PATCH',
      data,
    },
    callback: (success, response) => {
      // add your callback code
    },
  });
};
```

Then you can dispatch your action after implementing your simple own reducer:

```
// submit.js

import {updatePicture} from './updatePicture';

export default (values, dispatch) => {
  dispatch(updatePicture(values));
};
```
