## What is Express?

Espress is a fast, unopinionated and minimalist web framework for Node.js

- Express is a "**server-side**" or "**back-end**" framework.
- It's not comparable to client-se frameworks like React, Angulas & Vue.
- It can be used in combination with those frameworks to build full stack applications.

### Why use express?

- Makes building web applications with Node.js MUCH easier
- Used for both server apps as well as API/Microservices
- Extremely light, fast and free
- Full control of request and response
- By far the most popular Node framework
- Great to use with client side frameworks as it's all JavaScript

### Basic server syntax

`const express = require('express');`

// Init express
`const app = express();`

// Create your endpoints/route handlers
`app.get('/', funtion(req, res) {`
  `res.send('Hello World!');`
`})`

// Listen on a port
`app.listen(5000);`


### Express Middleware

**Middleware functions** are functtions that have access to the **request** and **response** object.
Express has built in middleware but middleware also comes from 3rd party packages as well as custom middleware.

- Execute any code
- Make changes to the request/response objects
- End response cycle
- Call next middleware in the stack

*Let's jump in to text editor:*
- `npm init -y` // `-y` to avoid answering any questions
- Now we can install express, but there are couple of this to install: `npm i express`
- Create a main entrypoint file: `index.js`

In case you don't need to reset the server everytime, we can install a package called *nodemon*, which will constantly watch our server so we don't need to keep loading the server.
- `npm i -D nodemon` . `-D` to install as dev dependencie as we don't use in production.
- To use it we have to go to our `package.json` and we need to create a script: we will create two script:
  - `"start": "node index"`  - to run node index to likely use in deployment
  - `"dev": "nodemon index"` - nodemon will constantly watching the server
- Then we run: `npm run dev`

We use middleware to handle with data send via post method using: `app.use(express.json())` and `app.use(express.urlencoded({ extended: false }))` to handle url encoded data.

Usually when dealing with id's in using a database like mongoDB or mySQL, Postgress it usually creates the id for us.
For this case we are going to install uuid to generate random id for us: `npm i uuid`.
And we use `id: uuid.v4()` to generate a random universal id.

### Rendering Template

We are going to use `express-handlebars`.
- If we go to github for that: https://github.com/ericf/express-handlebars
- We need to install `$ npm install express-handlebars`
- Basicaly we can have a views folder and we can create a main layout to wrap everything and we can create individual views to render them using `res.render()`:

`
var express = require('express');
var exphbs  = require('express-handlebars');

var app = express();

app.engine('handlebars', exphbs());
app.set('view engine', 'handlebars');

app.get('/', function (req, res) {
    res.render('home');
});

app.listen(3000);
`
So, stop the server and install `npm install express-handlebars` and we go ahead and run our server again.

`const exphbs = require('express-handlebars')`. We have to add a muddleware to know how to use handlebars: 



























