---
title: "Create a Web Server in Node.js using Express and the ES6 Module"
seoTitle: "Node.js: Create a Basic Web Server using the ES6 module"
seoDescription: "Using ES6 in Node.js Server: writing ES6 module, using"
datePublished: Wed Aug 23 2023 12:12:28 GMT+0000 (Coordinated Universal Time)
cuid: cllnp3gjh000b0alfew0t20x3
slug: create-a-web-server-in-nodejs-using-express-and-the-es6-module
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692788896213/376499b2-4a89-415c-b9cd-9be4bea6ea50.jpeg
tags: express, javascript, server, backend, es6

---

When viewing a webpage in a browser, a request is made to another computer, which then generates a webpage for you as a response. The computer you send your request to is known as a web server. When you type a URL into your web browser, your computer sends a request to a web server. The web server then sends back the requested information, which is usually an HTML page or a JSON object. Node.js allows us to write backend codes in Javascript, even though Javascript has traditionally been used to write frontend codes. For this article, we’ll be learning how to build web servers using the ES6 syntax and Express with Node.js.

## Prerequisites

To run npm commands on your machine, you must first install Node.js. You can also visit [here](https://nodejs.org/en/download) to download and install Node.js on your machine. In addition, you need to have a good grasp of JavaScript and how to create Node.js applications in particular.

### What is ES6?

ES6 is the newly released version of the javascript programming language whose proper name is ECMAScript. ES6 succeeds the previous ES5 version and it was released in 2011. It adds several features to javascript such as classes and others to make development easier. You can read more [here](https://www.makeuseof.com/tag/es6-javascript-programmers-need-know/)

## Initializing npm and setting up your package.json to accept ES6

We need to initialize a new package.json file in the root directory of our project file by running the command below in your terminal

```javascript
npm init -y
```

With that, we’d have initialized a npm package, you’ll see the package.json file in your folder

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692790082880/afb9db66-59d3-43d9-9d38-7c5dd0e3a96b.png align="center")

In the package.json file, add `"type": "module"` beneath the `“main”.` Adding that line enables the ES6 modules and your package.json file should look like this:

```javascript
{
  "name": "simple-server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^3.0.1"
  }
}
```

Also, install Nodemon by

```plaintext
npm i -–save-dev nodemon
```

Then, add the following line as a `start` script in your package.json file

```javascript
    "start": "nodemon --experimental-modules --es-module-specifier-resolution=node index.js"
```

Your code should look like this

```javascript
{
  "name": "simple-server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "nodemon --experimental-modules --es-module-specifier-resolution=node index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^3.0.1"
  }
}
```

## Installing Express 

To install the express framework to create our servers, run the code below in your terminal

```plaintext
npm i express
```

## Setting up your Index.js file and creating a basic server

The next thing we have to do is to create our index.js file, set up our web server by importing express using the ES6 import syntax, listen to our port and then create a get route to test if our code is working.

First, we import express using the ES6 import option and set up our app

```javascript
import express from "express";
const app = express();
```

Next, we create our port and listen to it to get our server running

```javascript
const PORT = 5000;

app.listen(PORT, () => {
    console.log(`Server is running on Port ${PORT}`)
})
```

Then, we create a route to test if our server is up and running

```javascript
app.get('/', (req, res) => {
    res.send('This is my server using the ES6 syntax')
});
```

## Running the Server

Once everything has been set, we need to run our server to check if it actually worked. Run `npm start` in your terminal and the web server will start listening on port 5000.

Open your browser, then go to `http://localhost:5000`, you should see a successful response with the message: <mark>“This is my server using the ES6 syntax”.</mark>

![Running the server](https://cdn.hashnode.com/res/hashnode/image/upload/v1692791788491/d4754759-e0ea-43d9-ba42-5a39c58ada16.png align="center")

If you have any issues, please double-check that you followed all of the steps correctly. This article should help you to start writing Node.js applications using the ES6 syntax, especially if you are also writing React and switching between ES5 for Node.js and ES6 for React.

## Conclusion

This article teaches you how to write ES6 node.js applications without using Babel or other complex dependencies. Node does not directly support ES6 imports and will throw an error if you try to use them. However, by adding the module type and the start script, you can use Node's experimental support for ES modules, which supports ES6 syntax and allows you to type and run your code.