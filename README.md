# Deployment of example JS application to the Kubernetes

This repository consist of the sample app with the kubernetes config yamls, Dockerfile and helm chart to do the deployment of this source code into the kubernetes cluster.

## Requirements
To deploy the NodeJS application below requirements are needed.

* Kubernetes cluster(Or minikube)
* Helm 3.2.4
* Kubectl
* Docker

## Getting started

1. Building docker image is needed. It can be done with the below command.
```sh
docker build -t dhenasmile/sample-node-app:1.0 .
```

2. This example node codebase use Mangoose to connect with the MongoDb for storing data. This MongoDb server also deployed as a standalone instance with the persistence storage in the Kubernetes cluster and through added as a dependency to the helm chart.

3. Running below command will take care of all the creating the deployment, secrets, and services to the kubernetes cluster.
```sh
helm install nodejs .
```
## Application Structure

- `app.js` - The entry point to our application. This file defines our express server and connects it to MongoDB using mongoose. It also requires the routes and models we'll be using in the application.
- `config/` - This folder contains configuration for passport as well as a central location for configuration/environment variables.
- `routes/` - This folder contains the route definitions for our API.
- `models/` - This folder contains the schema definitions for our Mongoose models.
- `node-chart/` - This folder contains the helm chart and templates files and mongoDB chart for the standalone deployment.
- `Dockerfile` - Dockerfile to build the image with the nodejs application.  
