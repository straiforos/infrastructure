# TVision 360 Infrastructure Project

This project contains infrastructure configurations and functionalities that are used by TVision 360, a fork of the openHAB project. It builds upon the foundation laid by openHAB, extending and customizing it to meet specific requirements.

## TVision 360 Installation

#### Environment Variables
The CI/CD process requires specific configurations for building and deploying the project. We are using a self-hosted Gitea instance for our version control and CI/CD needs.

For local development and CI/CD, we use our Gitea repository to manage our custom versions of TVision 360 packages, which are based on openHAB but include our modifications and enhancements.

Key configuration files:

1. `.gitea/workflows/main.yml`: This file defines our CI/CD workflow in Gitea Actions. It includes steps for building the project with Maven and deploying artifacts to our Maven repository.

2. `ci_settings.xml`: This file contains the Maven settings for CI/CD. It includes server configurations for our Maven repository, using token-based authentication.

3. `.gitpod.yml`: This file configures the Gitpod environment for development. It specifies the Docker image to use (circleci/openjdk:17-buster-node) and defines an initialization task to verify the project.

To set up your local environment:

1. Ensure you have Java 17 and Maven installed.
2. Clone the repository from our Gitea instance.
3. If using Gitpod, the environment will be automatically set up according to `.gitpod.yml`.

Note: The exact URLs and tokens needed for repository access should be obtained from your project administrator. These are typically set as environment variables or secrets in the CI/CD environment.