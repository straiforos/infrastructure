# TVision 360 Infrastructure Project

This project contains infrastructure configurations and functionalities that are used by TVision 360, a fork of the openHAB project. It builds upon the foundation laid by openHAB, extending and customizing it to meet specific requirements.

## Quick Links
- Repository: [straiforos/infrastructure](https://github.com/straiforos/infrastructure)
- Packages: [GitHub Packages](https://github.com/straiforos/infrastructure/packages)
- Original Project: [openhab/infrastructure](https://github.com/openhab/infrastructure)
- License: [EPL-2.0](LICENSE)

## Project Setup

### Prerequisites
- Java 17
- Maven 3.8+
- Git

## TVision 360 Installation

#### Environment Variables
The CI/CD process requires specific configurations for building and deploying the project. We use GitHub for our version control and CI/CD needs.

For local development and CI/CD, we use GitHub Packages to manage our custom versions of TVision 360 packages, which are based on openHAB but include our modifications and enhancements.

Key configuration files:

1. `.github/workflows/main.yml`: This file defines our CI/CD workflow in GitHub Actions. It includes steps for building the project with Maven and deploying artifacts to GitHub Packages.

2. `ci_settings.xml`: This file contains the Maven settings for CI/CD. It includes server configurations for our Maven repository, using token-based authentication.

3. `.gitpod.yml`: This file configures the Gitpod environment for development. It specifies the Docker image to use (circleci/openjdk:17-buster-node) and defines an initialization task to verify the project.

To set up your local environment:

1. Ensure you have Java 17 and Maven installed.
2. Clone the repository from GitHub.
3. If using Gitpod, the environment will be automatically set up according to `.gitpod.yml`.

Note: To access GitHub Packages, you'll need a Personal Access Token with the appropriate permissions (read:packages, write:packages). These tokens should be configured in your CI/CD environment secrets or your local Maven settings.