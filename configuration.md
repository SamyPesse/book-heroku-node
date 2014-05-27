# Configuration

In this chapter, we'll learn how to manage different configurations for our applications (locally and in production).

### Environment variables

The best way to configure an application on Heroku is to use **environment variables**. It's a key value storage managed by the system  that can affect the way running processes will behave on a computer.

Exemple of an env variable:

```
MESSAGE=Hello World
```

You can list all current environment variables using the command `env`.

Heroku defines by default 2 environement variables:

* `PORT` which equals the port our application should be running on.
* `DYNO` which gives you a id/name for the current process dyno.


### With Node.js

In Node.js, it's really easy to read environment variable, the varibale `process.env` is an object containing all current env variables.

We already used it to start our application on the right port: ```var port = Number(process.env.PORT || 5000);```.

Notice that environment variables are always **string**.

### Modifying our application

We are going to change our application to show a message instead of "Hello World" that will be stored in a en environment variables.

Edit the **main.js** file to change the `app.get` to:

```js
app.get('/', function(req, res) {
  res.send(process.env.MESSAGE || 'Default message!');
});
```

If you run the application using `foreman start` and access `http://localhost:5000`, you'll see : `Default message!`.

But you can test changing the value of **MESSAGE** in your terminal and running the application with:

```
$ export MESSAGE=Hello
$ foreman start
```

### Storing a fixed configuration for foreman

You don't want to define using `export` our all configuration each time you want to start working on your application!

So we need to store our configuration in a file. By default foreman use a file named `.env` but we are going to use this file for your production configuration.

So we'll store our configuration in a file named `.env.local`:

```
MESSAGE=Hello from the local version
```

And we need to update foreman configuration by writting the file `.foreman`:

```
port: 5000
env: .env.local
```

You can then test using `foreman start` and see teh output: `Hello from the local version`.

### Deployment of a production configuration

We are going to store our production configuration in a file named `.env`:

```
MESSAGE=Hello from the production version
```

Then we need to commit all these changes and deploy the last update of our code to Heroku:

```
# Commit changes
$ git add .
$ git commit -m "Use environment variables as configuration"

# Deploy to heroku
$ git push heroku master
```

But if you take a look at your application (using `heroku open`), you can see that the message is still "Default message!". It's because we didn't pushed your configuration to heroku yet.

For this we are going to use the plugin [heroku-config](https://github.com/ddollar/heroku-config), install it using:

```
$ heroku plugins:install git://github.com/ddollar/heroku-config.git
```

And then we can push our all configuration using:

```
$ heroku config:push
```

Now take a look at your application and you'll see "Hello from the production version".

### Managing Heroku configuraiton by hand

| I want to... | Command |
| -- | -- |
| List all my configuraton | `heroku config` |
| Get a variable value | `heroku config:get MESSAGE` |
| Set a variable value | `heroku config:set MESSAGE=Test` |
| Delete a variable | `heroku config:unset MESSAGE` |

And with the plugin **heroku-config**:

| I want to... | Command |
| -- | -- |
| Push my .env to heroku | `heroku config:push` |
| Update my .env with my heroku config | `heroku config:pull` |
| Rewrite my .env with my heroku config | `heroku config:pull --overwrite` |

