# Guestbook - Sample Application

Kickstart microservices application development in nodejs

Try it now:

[![Open in Cloud Code](http://gstatic.com/cloudssh/images/open-btn.svg)](vscode://googlecloudtools.cloudcode/shell?repo=https://github.com/GoogleCloudPlatform/cloud-code-samples.git&subpath=/nodejs/nodejs-guestbook)

## Overview

The application consists of 3 microservices:

- *Frontend* - serves HTML pages to the users
- *Backend* - exposes endpoint to read/save messages to the Guestbook
- *Database* - stores guestbook entries. We picked MongoDB for data storage due to its simplicity.

![Architecture Diagram](./img/diagram.png)

- [Anatomy of Cloud Code Template](https://cloud.google.com/code/docs/vscode/creating-an-application)

> The focus of the demo is showing microservices composition and configuration, as well as developer productivity using Cloud Code. We focus on simplicity and hence it's not production ready. As such, database was implemented as a stateless service, with minimal configuration. For production scenarios, consider using [replica sets](https://docs.mongodb.com/kubernetes-operator/master/tutorial/deploy-replica-set/) and [stateful sets](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/).

## Prerequisites

The sample is best experienced using one of the IDEs supported by [Cloud Code](https://cloud.google.com/code/):

- [VS Code](https://cloud.google.com/code/docs/vscode/install)
- [IntelliJ](https://cloud.google.com/code/docs/intellij/install)

> NOTE: If using VSCode, Cloud Code can handle all prerequisites installation.
----

## Configuration

### Kubernetes

Sample configuration is stored at **~/kubernetes-manifests** folder in YAML files.

*guestbook-**_microservice_name_**.deployment.yaml* defines environment variables that hold addresses of fellow microservices for communication purposes.

**EXAMPLE:**

```yaml
env:
    - name: PORT
      value: "8080"
    - name: GUESTBOOK_DB_ADDR
      value: "node-guestbook-mongodb:27017"
```

### Skaffold

Configuration that describes how the code is built, tested and deployed using [Skaffold](skaffold.dev).

The sample comes with 2 skaffold profiles:

- [default] - building container images locally, using Docker.
- [cloudbuild] - building container images on GCP, using [Cloud Build](https://cloud.google.com/cloud-build/docs/).
More details on Skaffold configuration [here](https://skaffold.dev/docs/).

## Debugging

Debugging configuration for *vscode* is stored in *~/.vscode/launch.json*.
>DOCKERFILE of *frontend* and *backend* is configured to start with debugger attached by default.

Hit F5 to start remote debugging.

More details and troubleshooting [here](https://cloud.google.com/code/docs/vscode/debug).

## Build & Deploy

### Using Cloud Code
![Deploy the app](https://cloud.google.com/code/docs/vscode/images/regular-deploy-workflow.gif)
Full details [here](https://cloud.google.com/code/docs/vscode/deploying-an-application).

### Using Command Line

[Skaffold](https://github.com/GoogleContainerTools/skaffold) is a command line tool that can be used to build, push, and deploy your container images

```bash
skaffold run --default-repo=gcr.io/your-project-id-here/cloudcode
```

## Additional Links

### Cloud Code

- [Adding Kubernetes Cluster](https://cloud.google.com/code/docs/vscode/adding-a-cluster)
- [Set up a Google Kubernetes Engine Cluster](https://cloud.google.com/code/docs/vscode/quickstart#creating_a_google_kubernetes_engine_cluster)
- [YAML editing](https://cloud.google.com/code/docs/vscode/yaml-editing)
- [Deploy the app](https://cloud.google.com/code/docs/vscode/quickstart#deploying_your_app)
- [Continuous Deployment](https://cloud.google.com/code/docs/vscode/quickstart#initiating_continuous_deployment)
- [View Container Logs](https://cloud.google.com/code/docs/vscode/quickstart#viewing_container_logs)
- [Debug Your Code](https://cloud.google.com/code/docs/vscode/quickstart#debugging_your_application)
- [Open a Terminal in Your Container](https://cloud.google.com/code/docs/vscode/quickstart#opening_a_terminal_in_your_container)
- [Setting up existing app](https://cloud.google.com/code/docs/vscode/setting-up-an-existing-app)
- [Using Stackdriver Log Viewer]
