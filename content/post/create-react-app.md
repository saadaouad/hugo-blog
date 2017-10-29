---
author: "Saad Aouad"
date: 2017-10-28
linktitle: Create React App
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Create React App
description: Create React app with no build configuration 
weight: 10
---


> You don’t need to install or configure tools like Webpack or Babel...
They are preconfigured and hidden so that you can focus just on the code!

## **Getting Started**

### **Installation**

```
npm install -g create-react-app
```
or 
```
yarn global add create-react-app
```

### **Create app**
To create a new app make you sure to run

```
create-react-app my-app
cd my-app
```

Try to open the current folder in your editor, you should see the initial structure below.

<img src='https://i.imgur.com/sqejkoC.png' alt='Structure app'>

### **Run app in development environment**

```
npm start
```
or 
```
yarn start
```
The app should be compiled successfully

```
Compiled successfully!

You can now view my-app in the browser.

  Local:            http://localhost:3000/
  On Your Network:  http://192.168.1.150:3000/

Note that the development build is not optimized.
To create a production build, use yarn build.
```
>The page will automatically reload if you make changes to the code.

### **Builds app for production**
Builds the app for production to the `build` folder, using

```
npm run build
```
or 
```
yarn build
```
```
➜  my-app yarn build
yarn run v1.2.1
warning You are using Node "7.7.1" which is not supported and may encounter bugs or unexpected behavior. Yarn supports the following semver range: "^4.8.0 || ^5.7.0 || ^6.2.2 || ^8.0.0"
$ react-scripts build
Creating an optimized production build...
Compiled successfully.

File sizes after gzip:

  40.13 KB  build/static/js/main.cc499d2e.js
  299 B     build/static/css/main.c17080f1.css

The project was built assuming it is hosted at the server root.
To override this, specify the homepage in your package.json.
For example, add this to build it for GitHub Pages:

  "homepage" : "http://myname.github.io/myapp",

The build folder is ready to be deployed.
You may serve it with a static server:

  yarn global add serve
  serve -s build

✨  Done in 8.90s.
```