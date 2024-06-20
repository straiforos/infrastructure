# openHAB Infrastructure Project

This project contains infrastructure configurations and functionalities that are used by openHAB Community projects.

## TVision 360 installation

#### Environment variables
CICD requires configureable project id, and package url for deployment/publishing the jar. Local development requires the same url to fetch our custom versions of openhab packages. 

Add to your local what the `.gitpod.yml` has.

```
echo "MVN_REPO_URL=\${CI_SERVER_URL}/\${CI_PROJECT_ID}/packages/maven" >> ~/.bashrc
```