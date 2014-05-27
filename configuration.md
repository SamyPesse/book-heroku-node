# Configuration

In this chapter, we'll learn how to manage different configurations for our applications (locally and in production).

### Environment variables

The best way to configure an application on Heroku is to use **environment variables**. It's a key value storage managed by the system  that can affect the way running processes will behave on a computer.

Exemple:

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
