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
description: This example demonstrates how i can upload a file and update his value using redux-form

weight: 10
---

This example demonstrates how i can upload a file and update his value using `redux-form`.

If you've setting up `redux-form` with an input `type="file"`, you should have encountered a browser error like the following error on Chrome:

```
Uncaught DOMException: Failed to set the 'value' property on 'HTMLInputElement': 
This input element accepts a filename, which may only be programmatically set to the empty string.
```
For a security reasons, input with `type="file"` don't support setting the value property programmatically, ref https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#File_inputs.

For handle this warning, it's necessary to set the input value to `null` or remove it to prevent React from trying to set the `value` property on the DOM Input Element:

```
import React from 'react';
import { Field, reduxForm } from 'redux-form';
// ...
<Field name="picture" component="input" type="file" value={null} />
// ...
```

Now we can update the value of `picture` field using method `PATCH`, so let’s start with implement an action redux for this case:

**FYI**: Make you sure to using `multipart/form-data` as a content type, ref https://developer.mozilla.org/en-US/docs/Web/API/FormData/Using_FormData_Objects 

`updatePicture.js`
```
export const updateUserProfile = values => dispatch => {
  const data = new FormData();

  // Don't send the data until a file has been loaded
  if (typeof values.photo !== 'string' && values.photo !== null) {
    data.append('photo', values.photo[0]);
  }

  dispatch({
    types: [
      'UPDATE_USER_PICTURE_REQUEST',
      'UPDATE_USER_PICTURE_SUCCESS',
      'UPDATE_USER_PICTURE_FAILURE',
    ],
    config: {
      // Make you sure to use your exact endpoint
      url: 'http://example.com/users/',
      method: 'PATCH',
      data,
    },
    callback: (success, response) => {
      // ...
    },
  });
};
```

Then you can dispatch your action after implement your simple own reducer:

`submit.js`
```
import {updatePicture} from './updatePicture';

export default (values, dispatch) => {
  dispatch(updatePicture(values));
};
```

<div style="text-align:center">
  <iframe src="https://giphy.com/embed/3o6vXNLzXdW4sbFRGo" width="330" height="269" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
</div>