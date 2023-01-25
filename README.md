## **MERN_STACK IMPLEMENTATION**
---
---

MERN stack consist of the following stacks, MongoDB, ExpressJS, ReactJS and NODEJS.

1. MongoDB: A document-based, No-SQL database used to store application data in a form of documents.
2. MongoDB: A document-based, No-SQL database used to store application data in a form of documents.
3. ReactJS: A frontend framework developed by Facebook. It is based on JavaScript, used to build User Interface (UI) components.
4. Node.js: A JavaScript runtime environment. It is used to run JavaScript on a machine rather than in a browser.

![MERN](./images/MERN.PNG)

Here as others, we will follow the steps below.

### **1. BACKEND CONFIGURATION**

- Update Ubuntu by running the code below

    `sudo apt update`

- Next, upgrade ubuntu by running the code below

    `sudo apt upgrade`

- Lets get the location of Node.js software from ubuntu repository using [NodeSource](https://github.com/nodesource/distributions/blob/master/README.md) 

    `curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - `

- Install Node.js on the server

    `sudo apt-get install -y nodejs`

- The command above installs both nodejs and npm. NPM is a package manager for Node like apt for Ubuntu

- You can check the version of the nodejs and npm by running the code below.

    `npm -v and node -v`

- Next we make a folder called Todo and cd into it.

    `cd Todo`

- Next, we will use the command npm init to initialize our project, so that a new file named package.json will be created. This file will normally contain information about our application and the dependencies that it needs to runs.

    `npm init`

### **1a. INSTALL EXPRESSJS**

Express is a framework for Node.js, therefore a lot of things developers would have programmed is already taken care of out of the box. Therefore it simplifies development, and abstracts a lot of low level details.

- To use express we have to install it using npm

    `npm install express`

- Next we create a file index.js with the code below.

    `touch index.js`

- Next install dotenv for environmental variable

    `npm install dotenv`

- Then we open the index.js in vim and paste the below code into it.

```
const express = require('express');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
next();
});

app.use((req, res, next) => {
res.send('Welcome to Express');
});

app.listen(port, () => {
console.log(`Server running on port ${port}`)
});
```

- Now save and exit vim

- Now run the below code to start the server.

    `node index.js`

![RUNNING SERVER](./images/RUNNING%20SERVER.PNG)

- Now we need to open this port (5000) in EC2 Security Group as shown below.

![EC2 inbound rule](./images/EC2%20INBOUND%20RULE.PNG)

- Open up your browser and try to access your server’s Public IP 

