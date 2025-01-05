# Gitea Actions for TVision360 CI

This document provides an overview of the Gitea Actions setup for TVision360 projects.

## Understanding Gitea Actions

Gitea Actions is a CI/CD feature built into Gitea, similar to GitHub Actions. It allows you to automate your software workflow directly in your Gitea repository. Workflows are defined in YAML files and run when specific events occur, such as pushes or pull requests.

## Key Components

Our CI setup consists of the following key files:

1. [`.gitea/workflows/main.yml`](.gitea/workflows/main.yml): Defines the CI workflow, including build, test, and deployment steps.

2. [`pom.xml`](pom.xml): Contains project configuration and dependencies, including the `distributionManagement` section for the Maven repository.

3. [`ci_settings.xml`](ci_settings.xml): Provides Maven settings for CI, including authentication for the Maven repository.

## Workflow Overview

The CI workflow, defined in `main.yml`, does the following:

1. Triggers on pushes to the `main` branch and pull requests targeting `main`.
2. Sets up a Java 11 environment.
3. Builds the project using Maven.
4. Deploys artifacts to the Maven repository.

## Repository Secret

The workflow uses a repository secret:

- `PACKAGE_TOKEN`: Used for authenticating with the Maven repository during deployment.

## Customization

You can customize the workflow by modifying the `main.yml` file. Adjust build steps, add tests, or include additional jobs as needed for your project.

## Troubleshooting

If you encounter issues:

1. Check the workflow run logs in the Gitea Actions tab.
2. Verify the `PACKAGE_TOKEN` secret is correctly set up.
3. Ensure the `pom.xml` and `ci_settings.xml` files are properly configured.

For more details on Gitea Actions, refer to the [official documentation](https://docs.gitea.io/en-us/actions/).