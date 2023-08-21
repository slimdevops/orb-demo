# Slim Scanner CircleCI Orb: Node.JS Demo
CircleCI Orb Demo Project to demonstrate configuration with a Node.JS project with Docker Container. 

# Setting up CircleCI Slim.AI Orb
Slim.AI has a public CircleCI Orb that's configurable for your Node.JS project with a Docker Container. This Orb conducts vulnerability scans, creates container profiles, and generates reports, allowing you to seamlessly access these artifacts from the CircleCI pipeline. As your project grows and scales, all these images and their associated data are available on the Slim platform for comprehensive analysis over time.

[Blog: Node.JS Example](https://www.slim.ai/blog/introducing-slim-s-scanner-orb-for-circleci)

## Project Environment Variables
Your Node.JS project will need the following environment variables:
```
DOCKERHUB_PASSWORD=
DOCKERHUB_USERNAME=
SLIM_ORG_ID=
SLIM_API_TOKEN=
CONNECTOR_ID=
```
- `DOCKERHUB_PASSWORD` and `DOCKERHUB_USERNAME` are your Docker Hub credentials. Sign up [here](https://hub.docker.com/signup)
- `SLIM_ORG_ID` and `SLIM_API_TOKEN` are found in the Slim Platform, from your Profile Settings, in the Tokens and Organization tabs. Sign up [here](https://portal.slim.dev/login)
- `CONNECTOR_ID` is found in the Slim Platform, under My Registries, after connecting a new Dockerhub registry.

## About the `.circleci/config.yml` file
The Slim.AI Orb is imported into your project here along with other `orbs`, with a organization identifier and orb slug, for example `slimdevops/slim-ai-test-orb@0.0.5`. Other notable areas of the configuration include:

- `parameters` contain CircleCI Orb meta information about the Docker image and connector used by Slim.AI. It specifies the Docker image (`image-name`) and the tag for `cimg/base` (`cimg-tag`)
- `jobs` outlines tasks in the workflow. `publishLatestToHub` builds and pushes the Node.js app's Docker image to Docker Hub.
- `workflows` defines the sequence of jobs. The engine-execution workflow first publishes the image, then scans the image using the 'slim-ai-test-orb/scan' job.  


## CircleCI Artifacts
With each project build, the orb will generate Artifacts viewable in your CircleCI workflows. Find the JSON output of the container profile `XRay.json` and vulnerability scan `vuln.json`. Start with the `readme.html`, found in the CircleCI artifacts tab, to navigate to the Slim portal for images and reports.


## Slim Community
For more information about configuring containers, vulnerability scans, or this orb example, check out [SlimDevOps Community](https://community.slim.ai/) and the [blog](https://www.slim.ai/blog/)
