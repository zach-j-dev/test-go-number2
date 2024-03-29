<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://cdn.architect.io/logo/horizontal-inverted.png">
    <source media="(prefers-color-scheme: light)" srcset="https://cdn.architect.io/logo/horizontal.png">
    <img width="320" alt="Architect Logo" src="https://cdn.architect.io/logo/horizontal.png">
  </picture>
</p>

<p align="center">
  A dynamic microservices framework for building, connecting, and deploying cloud-native applications.
</p>

---
# Using Golang on Architect
It is extremely common to run a REST API with a backend database as a standalone service so that it can be consumed by
multiple, disparate applications.

In this example, you'll learn how to capture an app written with [Go](https://go.dev/) and a [Postgres](https://www.postgresql.org/)
database backend as a [dependency](https://docs.architect.io/components/dependencies/) using Architect to enable automated deployments, networking and network security for your application - wherever it gets deployed.

In the `architect.yml` file for this project, we describe this app as two deployable services. However, we also
leverage Architect's [service discovery](//docs.architect.io/components/service-discovery) features to populate environment
secrets by reference. This not only allows us to automatically connect the services to each other, but it also allows
Architect to build strict network policies to whitelist the traffic between these services. Now we won't have any work ahead
of us to promote this stack from local dev all the way through to production!

[Learn more about the architect.yml file](//docs.architect.io/configuration)

## Using the app and API

This service implements GET/POST functionality for a simple `Movies` schema consisting of a `name` and a `rating` between 1 and 5.
You could use it to gather data about anything you want to rate, from your favorite restaurants, movies, and more!

### The `Movies` Schema:

```
  {
    "name": "string",
    "rating": "integer"
  }
```

In the Go service under `server/static/base.tmpl`, uncomment the `user_input` and `user_table` template blocks to interact with the API and Database components of the app.

## Running Locally
The `architect.yml` file is declarative, which allows the Architect Component it describes to be run in any environment,
from local development all the way to production. Follow these steps to clone this repository and run the application
locally.

Once the deployment has completed, you can reach your new service by going to https://app.localhost.architect.sh.

```sh
# Clone the repository and navigate to this directory
$ git clone https://github.com/architect-templates/go.git
$ cd ./go

# Deploy locally using the dev command
$ architect dev architect.yml
```

## Deploying to the Cloud

Want to try deploying this to a cloud environment? Architect's got you covered there, too! It only takes a minute to
[sign up for a free account](https://cloud.architect.io/signup).

You can then [deploy the application](https://docs.architect.io/getting-started/introduction/#deploy-to-the-cloud) by running the command below. Note that “example-environment” is the free environment that is created with your Architect account.

```sh
# Deploy to Architect Cloud
$ architect deploy architect.yml -e example-environment
```
