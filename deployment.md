# Deployment on Heroku

We just test our application, and it's working fine. Now it's time to deploy it on Heroku to make it available for everybody.

### Create an application on Heroku

If you haven't already, sign up on [Heroku](https://heroku.com). It's free and easy!

Click on the button "Create a new app" and enter a name for your application. You can select the region that you want, it doesn't change anything for the deployment.

### Commit your changes

The first is to commit your changes (main.js and Procfile):

List all the changes that needs using:

```
$ git status
```

You can see that the folder `node_modules` is contained in the list. This folder contains all the dependencies, we installed using **NPM**. We need to add this folder to a `.gitignore` file:

Copy and paste the content of [GitHub Node .gitignore](https://github.com/github/gitignore/blob/master/Node.gitignore) to a file named `.gitignore`.

If you run `git status` again, you can see that `node_modules/` is no longer present in the list.

You can now commit the other changes using:

```
$ git add .
$ git commit -m "Base code"
```
