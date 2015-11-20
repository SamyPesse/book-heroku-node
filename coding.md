# Coding the application

Now that the git repository and the node module structure are setup, we are ready to start coding the application.

This application will be a simple hello world.

### Instaling our dependencies

In node.js, the dependencies are listed in the **package.json** file. All dependencies from this file can be installed using the command `npm install .`.

An other dependency can be installed and added to the package.json using: `npm install name@version --save`.

Our application will depend on: `express@4.3.1`.

So install it using:

```
$ npm install express@4.3.1 --save
```

### Hello World

[Express](http://expressjs.com/) is web application framework for node, it makes it really easy to write web application using node.

Write in a file named **main.js**:

```js
var express = require("express");
var app = express();

app.get('/', function(req, res) {
  res.send('Hello World!');
});

var port = Number(process.env.PORT || 5000);
app.listen(port, function() {
  console.log("Listening on " + port);
});

```

This code will simply create an application using Express. Define an handling method for a get request on the root path. And start the web server on the port defined by the environment variable `PORT` or `5000`.

### Run Script

Heroku convention needs a `Procfile` file that defines how to start the application. You can learn more about **Procfile** in the [Heroku documentation](https://devcenter.heroku.com/articles/procfile).

Write in a file named **Procfile**:

```
web: node main.js
```

This file simply tell Heroku that for starting this application, it needs to start a web dyno by running the command `node main.js`.
