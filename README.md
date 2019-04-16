# Heroku YML Node + React Tutorial

This is a quick walkthrough of how to get a containerized Node app up and running on Heroku.

## React via Create React App

We'll be leveraging the [`create-react-app`](https://github.com/facebook/create-react-app) project for this tutorial to create an efficient React app with little to no scaffolding required. 

Upon downloading this project, you simply can run `yarn` to install dependencies followed by `npm start` to trigger the server.

## Client Backend via Express

Coming soon.

## Deploying to Heroku

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

We'll use this command for all future pushes to deploy code.