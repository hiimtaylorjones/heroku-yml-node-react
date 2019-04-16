# Heroku YML Node + React Tutorial

Currently found at: https://quiet-reaches-40976.herokuapp.com/

This is a quick walkthrough of how to get a containerized Node app up and running on Heroku.

## Breaking down the heroku.yml file

Heroku offers a containerization service that allows users to specify configuration aspects of Heroku - along with a provided `Dockerfile` - to build out their Docker app on Heroku. This manifest is pushed up to Heroku and built into a containerized app.

There are a lot of use cases and potential possibilities for using `heroku.yml`, but I want to break down what it would look like for a Node + React app that's included in this project:

`heroku.yml`

```
setup:
  addons:
    - plan: heroku-postgresql
      as: DATABASE
build:
  docker:
    web: Dockerfile
  config:
    NODE_ENV: production
run:
  web: npm start
```

The [`setup` phase](https://devcenter.heroku.com/articles/build-docker-images-heroku-yml#setup-defining-your-app-s-environment) in our example is only specifying which add-ons we want our Heroku 
app to use. In this case, its a straightforward `heroku-postgres` instance. 

The [`build` phase](https://devcenter.heroku.com/articles/build-docker-images-heroku-yml#build-defining-your-build) specifies two things: the docker image locations for each `web` process and the configuration that relates to the build process. 

The [`run` phase](https://devcenter.heroku.com/articles/build-docker-images-heroku-yml#run-defining-the-processes-to-run) is the closest thing to a `Procfile` that containerized apps have. It specifies what each process in a containerized app looks like. For our example, we're just telling it what the `web` process looks like. 

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