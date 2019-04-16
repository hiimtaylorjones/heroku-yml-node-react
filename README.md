# Heroku YML Node + React Tutorial

This is a quick walkthrough of how to get a containerized Node app up and running on Heroku.

## Getting started

Its suggested that you have Docker installed on your local machine to properly test out
images. However, since Heroku builds the images based off `heroku.yml` and the `Dockerfile` here, it isn't necessary. 


First and foremost, we'll want to create an app instance on Heroku:

```
heroku create
```

Next, we'll set the stack of our applicaiton to be a container

```
heroku stack:set container
```

We then can push and build our application on Heroku via:

```
git push heroku master
```