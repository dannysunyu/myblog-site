+++
title = 'Bootstrapping Microservices V2'
date = 2025-06-29T22:52:19+07:00
draft = false
+++

# Chapter 2

Express is the de facto standard for building HTTP servers on Node.js.

Of course, we could build an HTTP server directly on Node.js without Express,
but Express allows us to do this at a higher level of abstraction, with less code,
and without the nuts-and-bolts code we'd otherwise need using the low-level Node.js API.

```zsh
npm install --save express
```

The --save argument causes the dependency to be added to and tracked in the package.json file. Note that --save isn't
necessary anymore. In older versions of Node.js, this was required; these days, it's the default.

The command npm install by itself (not specifying any particular package) installs all the dependencies listed in
package.json.

The `file index.js` is one of the standard names for the main entry point (_main_ file) of a Node.js application. We
could just as
easily have called it something else, such as main.js or server.js.

We placed the file index.js under the src directory as a convenient way to keep our source code files separated and
easily distinguished from our configuration and other files. The directory doesn't have to be called src —— you can
call it anything you like —— but src is a common name for it. Don't forget to update your package.json file to include
the location of index.js within the src directory.

It's customary during development to set your Node.js application to listen on port 3000.

Environment variables can be thought of as an input or parameter to our microservice.

**Configuring a microservice**

We need a way to configure our microservice so it knows the port number to use when starting the HTTP server. There are
several techniques we might use to configure our microservice, such as configuration files or command-line arguments.
These techniques work, but another has emerged as the standard way to configure a microservice, and it’s well supported
by all the tools we’ll be using. We’ll configure our microservices using **environment variables**.

To run multiple different microservices at the same time, we’ll have to start them on separate **port** numbers.

```zsh
export PORT=3000
```

We can also use environment variables to pass secret and sensitive data into a microservice (e.g., the password for our
database). We need to treat this information carefully, and we shouldn’t store it in the code where everyone in the
company can see it.

Well, to get our microservice ready to run in production, we’ll use a slightly different version of this command:

```shell
npm install --omit=dev
```

We added the argument `--omit=dev` to omit development dependencies and only install those dependencies that are
required
in production. This is important because when creating a Node.js project, we’ll usually have a bunch of these so-called
dev dependencies that we only need to support our development efforts—we don’t want to install these into our production
environment.

**npm script**

Up until now, we’ve run our HTTP server on our dev computer like this:

```zsh
node src/index.js
```

That’s OK, but now we’ll start running our microservice using the following standard convention for Node.js:

```zsh
npm start
```

注：npm start是启用生产环境的惯例。

Invoking the command npm start is the conventional way to start a Node.js application. This is a special case of a npm
script.

The nice thing about this convention is that for almost any Node.js project (at least those that follow this convention)
, we can run `npm start` without actually knowing if the main file is called `index.js` or if it has some other name. We
also don’t need to know if the application takes any special command-line arguments or configuration because those
details can be recorded here as well.

This gives us a single command to remember regardless of whatever project we’re looking at and however the particular
application is started. This makes understanding how to use any Node.js project much easier, even those created by other
people.

So far, we set up our microservice to run on our development computer. That’s all well
and good—we need that for ongoing development and testing—but before we get to
the fun stuff (Docker, Kubernetes, Terraform, etc.), we need to know how to set up
our microservice to run in the production environment.
When I say production environment, what I mean is our customer-facing environment.
That’s where our application is hosted so it can be accessed by our customers. For this
book, our production environment is Kubernetes, and we’re gearing up to run our
application in a Kubernetes cluster to make it publicly accessible.

**Live reloading for fast iteration**

To create our live reload pipeline, we’ll install a package called nodemon. We use nodemon to run our microservice, and
it automatically watches for code changes in our project. When a code change is detected, nodemon automatically restarts
our microservice for us, saving us the effort of doing so manually. This might not sound like it does much at all, but
I’ve found that it makes for a fast and fluid development cycle. Once you’ve tried it, you might wonder how you ever did
without it.

We can install nodemon in our Node.js project as follows:

```shell
npm install --save-dev nodemon
```

Note that now we’re using the `--save-dev` argument. This installs the package as a dev dependency rather than a
production dependency.

### npx command

Now that we’re going to be using nodemon instead, we’ll replace node with nodemon and run it like this:

```shell
npx nodemon src/index.js
```

The npx command that’s suddenly appeared is a useful command that comes with
Node.js and allows us to run locally installed packages directly from the command
line. Before npx was added to Node.js, we used to install modules such as nodemon
globally. [Now we can run tools like this directly from the current project’s dependencies.](#) This really helps us use
the right versions of modules for each project and prevents our computer from being cluttered up with globally installed
modules.

### Debugging the container

When we’re running a container locally, especially one that is having problems, it can be useful to shell into it and
inspect it from the inside. This can help us understand what’s happening inside our container. We can open a shell into 
our container like this:

```shell
docker exec -it <container-id> bash
```
From here, you can use common Linux commands such as `cd`, `ls`, and `ps` to inspect the filesystem and process inside 
the container. This is a valuable technique for debugging and understanding what is going on in your container, so 
please spend some time exploring inside your container.
