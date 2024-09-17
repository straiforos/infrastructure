# openHAB Infrastructure Project

This project contains infrastructure configurations and functionalities that are used by openHAB Community projects.

## TVision 360 installation

#### Environment variables
CICD requires configurable project id, and package url for deployment/publishing the jar. We are migrating from GitLab to a self-hosted Gitea instance as a proof of concept to address issues with GitLab groups not allowing connection to its package repository.

For local development, we now use our Gitea repository hosted at repo.tvision360.io to fetch our custom versions of openHAB packages. This replaces the previous GitLab setup.

Key changes in configuration files:

1. `.gitlab-ci.yml`: This file will need to be adapted for Gitea CI/CD. The `MAVEN_REPO_URL` variable and deployment scripts will need to be updated to use Gitea's API endpoints.

2. `ci_settings.xml`: The `<server>` configuration will need to be updated. The `Private-Token` header might need to be replaced with an appropriate authentication method for Gitea.

3. `.gitpod.yml`: Environment variables like `CI_SERVER_URL`, `CI_PROJECT_ID`, and `MVN_REPO_URL` will need to be updated to point to the Gitea instance instead of GitLab.

To set up your local environment:

1. Update the variables in your local environment to match the new Gitea setup. Use the updated `.gitpod.yml` as a reference.
2. Ensure your local `settings.xml` (or `local_settings.xml`) is updated to use the Gitea repository URL.
3. Update any scripts or commands that were using GitLab-specific variables or endpoints.

Note: Exact Gitea equivalents for GitLab variables and endpoints will depend on your Gitea setup. Consult your Gitea administrator for the correct values.