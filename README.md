# openHAB Infrastructure Project

This project contains infrastructure configurations and functionalities that are used by openHAB Community projects.

## TVision 360 installation

#### Environment variables
CICD requires configurable project id, and package url for deployment/publishing the jar. Local development uses a respoilite url to fetch our custom versions of openhab packages. 

Add to your local what the `.gitpod.yml` has.

```
echo "MVN_REPO_URL=\${CI_SERVER_URL}/\${CI_PROJECT_ID}/packages/maven" >> ~/.bashrc
```

##### Local Respoilite Maven artifactory

Install [Respoilite](https://reposilite.com/guide/about)

Add token with a name, secret, and permission of a manger. `token-generate test m -s 123`

Gitlabs repository requires no releases versus snapshots yet reposilite does.
We use empty env variables to make the dynamic configuration work.

Add to your local machines environment variables `export MAVEN_RELEASE_ENDPOINT=releases` and `export MAVEN_SNAPSHOT_ENDPOINT=snapshots`.