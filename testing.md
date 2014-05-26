# Testing

Now that our application is coded, we need to run it locally for testing. To follow Heroku convention, we are not going to run `node main.js` directly but we are going to use **Foreman**.

[Foreman](https://github.com/ddollar/foreman) is tool to run and manage procfile based applications.

### Installation of Foreman

| If you have... | Install with... |
| -- | -- |
| Ruby (MRI, JRuby, Windows) | $ gem install foreman |
| Mac OS X | Download and install: [foreman.pkg](http://assets.foreman.io/foreman/foreman.pkg) |

### Running the application

Starting our applciation locally using foreman is really simple, run the command:

```
$ foreman start
```

You can now open a browser and take a look at **http://localhost:5000**.
