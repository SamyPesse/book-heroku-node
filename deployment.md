{% raw %}
# Deployment on Heroku

We just test our application, and it's working fine. Now it's time to deploy it on Heroku to make it available for everybody.

### Create an application on Heroku

If you haven't already, sign up on [Heroku](https://heroku.com). It's free and easy!

Click on the button "Create a new app" and enter a name for your application. You can select the region that you want, it doesn't change anything for the deployment.

### Install the Heroku Command Line Tool

First, install the Heroku Toolbelt on your local workstation. You can find it at [toolbelt.heroku.com](https://toolbelt.heroku.com/).


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

### Pushing to Heroku

It is now time to push to Heroku. In the configuration or homepage of your Heroku application, you can see a GIT url with the following format:

```
git@heroku.com:{{ application name }}.git
```

To deploy a new release of your application, simply run:

```
$ git push heroku master
```

Heroku will log the installation of the node dependencies and the launch of your application.

Once it's done you can open your application using:

```
$ heroku open
```
{% endraw %}
