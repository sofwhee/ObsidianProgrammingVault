Environment variables allow us to keep values on our local and production environments distinct and safe as we develop our app.

We can understand an environment as the context in which code is being executed—all the variables, objects, functions available to the code. We can think of an environment as a unique machine executing code.

In programming, most of the time we use two main environments: **development** and **production**.

The development environment is your local computer. The editors/IDEs you use to write code. The compilers and interpreters that you use to run and execute code on your machine. The operating system installed on your machine. The local network capacity and connectivity.

Everything installed on your machine is under your development environment. Whenever you hear someone referring to “development environment” remember that they are talking about developing something on their computer.

The production environment is the final product. The live product that your customers will use daily and interact with.

## What Are Environment Variables

An environment variable is made up of a name/value pair, like this:

```
API_KEY=1234567890
```

## How Are Environment Variables Useful?

The most common use case for environment variables is being able to set up different configuration options for both environments.

## Are Environment Variables Secure?

To make sure that you’re not exposing your environment variables in your git repository, you can add a new filename inside your .gitignore file:

```
.env
```

You can have as many env files as you want. Most of the time, you’re going to use at least two env files—one for production and one for development. It is a common practice to name the development environment file as .env.development. The production environment file is often named .env.

You can add them both on your .gitignore and make sure that all your environment variables are safe and are not going to be available for everyone to see:

```
.env
.env.development
```