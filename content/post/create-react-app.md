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

```
my-app
├── node_modules
├── public
│   └── favicon.ico
│   └── index.html
│   └── manifest.json
└── src
    └── App.css
    └── App.js
    └── App.test.js
    └── index.css
    └── index.js
    └── logo.svg
    └── registerServiceWorker.js
├── .gitignore
├── package.json
├── README.md
├── yarn.lock

```

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

### **Runs test using Jest**
Runs test watcher using Jest.

By default, runs tests related to files changed since the last commit.

```
npm test
```
or
```
yarn test
```

[Read more about how this working](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#running-tests)

### **Builds app for production**
Builds the app for production to the `build` folder, using

```
npm run build
```
or 
```
yarn build
```