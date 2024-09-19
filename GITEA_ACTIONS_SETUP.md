# Setting up Gitea Actions for openHAB CI

This guide will help you set up the Gitea Actions pipeline for the openHAB project.

## Prerequisites

1. Ensure you have administrator access to the Gitea repository.
2. Make sure Gitea Actions are enabled for your Gitea instance.

## Steps to Set Up

1. **Create the Workflow File**:
   - Create a new file at `.gitea/workflows/main.yml` in your repository.
   - Copy the contents of the workflow from the [main.yml](.gitea/workflows/main.yml) file.

2. **Set Up Secrets**:
   You need to set up the following secret in your Gitea repository:
   - `PACKAGE_TOKEN`: The token for authenticating with the Maven repository

   To set up the secret:
   1. Go to your repository settings in Gitea.
   2. Navigate to "Secrets" or "Environment Variables" section.
   3. Add the secret with its corresponding value.

3. **Verify Java Version**:
   - The workflow uses Java 11 (openjdk-11). If you need a different version, modify the container image in the `main.yml` file.

4. **Update pom.xml**:
   - Ensure your `pom.xml` file includes the correct `distributionManagement` section for the Maven repository.
   - The `tvision360.repo.url` property should be set to the URL of your Maven repository.

5. **Create ci_settings.xml**:
   - Create a `ci_settings.xml` file in the root of your repository with the provided content.

6. **Commit and Push**:
   - Commit the `.gitea/workflows/main.yml` file, updated `pom.xml`, and `ci_settings.xml` to your repository.
   - Push the changes to the `main` branch.

7. **Verify Workflow**:
   - Go to the "Actions" tab in your Gitea repository.
   - You should see the "openHAB CI" workflow listed.
   - The workflow will run automatically on pushes to the `main` branch and for pull requests targeting `main`.

## Customization

- If you need to disable the `openhab-snapshot-repository` profile, add `-DnoOhSnapRepo` to the Maven commands in the workflow.
- Adjust the workflow as needed for any specific build or test requirements of your project.

## Troubleshooting

- If the workflow fails, check the workflow run logs for error messages.
- Ensure the `PACKAGE_TOKEN` secret is correctly set up in your Gitea repository.
- Verify that your `pom.xml` file is correctly configured with the `tvision360.repo.url` property.
- If you encounter authentication issues during deployment, double-check that the `PACKAGE_TOKEN` is correct and that the associated user has the necessary permissions to deploy artifacts.

## Notes

- The current setup uses a fixed URL for the TVision360 repository. If you need to use a different repository, update the `tvision360.repo.url` property in the `pom.xml` file.
- The workflow now includes steps for installing Node.js, which may be required for certain build processes.
- The deployment step now uses the `ci_settings.xml` file for authentication, which simplifies the Maven command.

For more information on Gitea Actions, refer to the [Gitea Actions documentation](https://docs.gitea.io/en-us/actions/).