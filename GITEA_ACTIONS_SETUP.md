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
   You need to set up the following secrets in your Gitea repository:
   - `MAVEN_REPO_URL`
   - `MAVEN_RELEASE_ENDPOINT`
   - `MAVEN_SNAPSHOT_ENDPOINT`

   To set up secrets:
   1. Go to your repository settings in Gitea.
   2. Navigate to "Secrets" or "Environment Variables" section.
   3. Add each secret with its corresponding value.

3. **Verify Java Version**:
   - The workflow uses Java 11. If you need a different version, modify the `java-version` field in the "Set up JDK" step of the workflow file.

4. **Commit and Push**:
   - Commit the `.gitea/workflows/main.yml` file to your repository.
   - Push the changes to the `main` branch.

5. **Verify Workflow**:
   - Go to the "Actions" tab in your Gitea repository.
   - You should see the "openHAB CI" workflow listed.
   - The workflow will run automatically on pushes to the `main` branch and for pull requests targeting `main`.

## Customization

- If you need to disable the `openhab-snapshot-repository` profile, add `-DnoOhSnapRepo` to the Maven commands in the workflow.
- Adjust the workflow as needed for any specific build or test requirements of your project.

## Troubleshooting

- If the workflow fails, check the workflow run logs for error messages.
- Ensure all required secrets are correctly set up.
- Verify that your `pom.xml` file is correctly configured to use the environment variables for Maven repository URLs.

For more information on Gitea Actions, refer to the [Gitea Actions documentation](https://docs.gitea.io/en-us/actions/).