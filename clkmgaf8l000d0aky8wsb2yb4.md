---
title: "6 Mistakes I make often while handling Environment Variables in NODE JS (using dotenv)"
seoTitle: "6 Mistakes I make often while handling Environment Variables in NODE J"
seoDescription: "In this blog, we will explore the common mistakes I frequently make while dealing with environment variables in Node.js, using the popular dotenv package"
datePublished: Fri Jul 28 2023 10:38:28 GMT+0000 (Coordinated Universal Time)
cuid: clkmgaf8l000d0aky8wsb2yb4
slug: 6-mistakes-i-make-often-while-handling-environment-variables-in-node-js-using-dotenv
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690540591493/1ffed629-7a29-4497-b5a2-9aef0f778074.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690540652079/2c003759-8395-4fdd-80d5-514e515fa314.png
tags: dotenv, env, environment-variables

---

Handling environment variables is an essential aspect of modern web development, particularly in Node.js applications. As developers, we strive to create secure, scalable, and maintainable code. However, when it comes to managing environment variables in Node.js, it's surprisingly easy to overlook crucial best practices.

In this blog, we will explore the common mistakes I frequently make while dealing with environment variables in Node.js, using the popular `dotenv` package for loading configurations. **<mark>FIrstly, I have gone through a short setup guide and if you don't need it feel free to jump to the mistakes section.</mark>**

### A short setup guide for using Environment Variables using dotenv in Node JS

1. **Create a Node.js Project:** Start by creating a new directory for your Node.js project and navigate into it. Initialize your project with the following command:
    

```bash
mkdir my-nodejs-app
cd my-nodejs-app
npm init -y
```

1. **Install** `dotenv` Package: Install the `dotenv` package, which allows you to load environment variables from a `.env` file into `process.env`. Run the following command:
    

```bash
npm install dotenv
```

1. **Create a** `.env` File: In the root of your project, create a `.env` file. This file will store your environment variables in the format `KEY=VALUE`. For example:
    

```javascript
PORT=3000
DB_CONNECTION_STRING=mongodb://localhost:27017/mydatabase
API_KEY=your_api_key_here
```

1. **Load Environment Variables:** In your entry file (e.g., `index.js`), require and load the `dotenv` package as the first line of code:
    

```javascript
require('dotenv').config();
```

1. **Use Environment Variables in Your Code:** You can now access the environment variables defined in the `.env` file using `process.env.KEY`, where `KEY` is the name of the environment variable. For example:
    

```javascript
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});
```

1. **Run Your Application:** Start your Node.js application using:
    

```bash
node index.js
```

# **MISTAKES I make often**

### **<mark>Exposing Environment Variables in Code Repositories:</mark>**

Never commit your `.env` files or any sensitive configuration files to version control systems like Git. Doing so could lead to accidental exposure of sensitive information.

### **<mark>Wrapping value with a quote:</mark>**

You don't have to wrap the value of the environment variables inside the .env file with the quotation. 'dotenv' package will do that for you.

### **<mark>Declaring Env. Variables Like Normal Variables :</mark>**

don't use const, var, let before environment variables. They will be just like key-value pair.

```plaintext
/.env

NODE_ENV = test
PORT = 3003
MONGODB_URI = mongodb+srv://username:password@bloglist.gkxx04c.mongodb.net/?retryWrites=true&w=majority
TEST_MONGODB_URI = mongodb+srv://username:<test123>@password.gkfnybe.mongodb.net/?retryWrites=true&w=majority
```

### **<mark>Storing Production Secrets in Development Environment:</mark>**

Using the same environment variables for development and production is a major risk. Use separate configurations for each environment, and ensure that production secrets are not accessible during development.

### **<mark>Not Backing Up Environment Variable Configurations:</mark>**

Keep backup copies of your environment variable configurations, especially for production. Accidental loss of configuration files can lead to application downtime.

### **<mark>Not Restarting the App After Environment Variable Changes:</mark>**

Restart the application after the Environment Variable Changes otherwise they won't work.

Thank you for reading ❤️ Happy Coding