# orb-demo
CircleCI Orb Demo Project to demonstrate configuration with a Node.JS project with Docker Container. 

# Setting up CircleCI Slim.AI Orb
Slim.AI has a public CircleCI Orb, quickly configurable to run on your Node.JS project with a Docker Container. This Orb runs a vulnerability scan, creates a container profile, and makes a report for you to easily access these artifacts from the CircleCI pipeline. Find a collection of these images in the Slim.AI platform, to analyze overtime as you build and the project scales. 

## Project Environment Variables
Your Node.JS project will need the following environment variables added to your `.env` file:
```
DOCKERHUB_PASSWORD=
DOCKERHUB_USERNAME=
FAV_COLLECTION_ID=
ORG_ID=
SAAS_KEY=
```
- `DOCKERHUB_PASSWORD` and `DOCKERHUB_USERNAME` are your Docker Hub credentials. Sign up [here](https://hub.docker.com/signup)
- `FAV_COLLECTION_ID`, `ORG_ID`, and `SAAS_KEY` are found in the Slim Platform, from your Profile Settings, in the Tokens and Organization tabs. Sign up [here](https://portal.slim.dev/login)


## About the `.circleci/config.yml` file
The Slim.AI Orb is imported into your project here along with other `orbs`, with a organization identifier and orb slug, for example `slimdevops/slim-ai-test-orb@0.0.15`. Other notable areas of the configuration include:
- `parameters` contain CircleCI Orb meta information about the Docker image and connector used by Slim.AI
- `jobs` defines `publishLatestToHub` which runs the scans and creates artifacts to be stored in Slim Platform
- `steps` run commands for vulnerability scan,  takes a snapshot of the container image, and generates artifacts including the results contained in `readme.html`

## CircleCI Artifacts
With each project build, the orb will generate Artifacts viewable in your CircleCI workflows. Find the JSON output of the container profile `XRay.json` and vulnerability scan `vuln.json`. Start with the `readme.html` to navigate to your collections of images and reports.


## Slim Community
For more information about configuring containers, vulnerability scans, or this orb example, check out [SlimDevOps Community](https://community.slim.ai/) and the [blog](https://www.slim.ai/blog/)