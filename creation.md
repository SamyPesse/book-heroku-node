# Creating the Application

The first of this course is to create a Node.js application that can run on Heroku and locally (for testing).

### Creation of a Git Repository

Our source code is going to be stored in a Git repository. Heroku uses Git for deployment, and it's also a better habit to use git.

To create a new empty repository, run on a terminal:

```
$ mkdir myapp
$ cd myapp
$ git init
```

We are now going to work on this `myapp` folder.

You can also host this repository on [GitHub](https://github.com), this is optional but advised:

1. Create a repository on GitHub
2. On a terminal in the `myapp` folder run: `git remote set-url upstream <git url for the repository>`

The url for the repository on GitHub is in the format: `https://github.com/<username>/<repository>.git`.

### Creation of a base for a Node.js application

Now that our git repository is ready, we can start working on writting our node.js application.

In a terminal in the `myapp` folder, run:

```
$ npm init
```

It will ask you for multiple questions and generate a `package.json` file. This file will contain the list of your dependencies (the librairies our program will depend on) and some others descriptives informations.

### Commit our base

It's time to commit our first commit for this application:

```
$ git add package.json
$ git commit -m "Base package.json"
```

And push it to GitHub:

```
$ git push
```
