# quick-gha

A collection of reusable GitHub Actions workflows to streamline CI/CD processes for various projects.

This repository provides pre-configured workflows for common tasks such as:

*   Pull Request checks (linting, testing)
*   Automated deployments
*   Commit message validation
*   Package releases
*   And more!

## Usage

To use a workflow from this repository in your project:

1.  **Copy the workflow file:** Choose the workflow you need from the appropriate directory (e.g., `pr-checks`, `deploy`, `release`) and copy the `.yml` file into the `.github/workflows` directory of your project.

2.  **Configure the workflow:** Open the copied workflow file in your project and modify it as needed. Pay close attention to:

    *   **Triggers:** Adjust the `on` section to specify when the workflow should run (e.g., `push`, `pull_request`).
    *   **Branches:** Specify the branches the workflow should apply to.
    *   **Environment variables and secrets:** Set any required environment variables or secrets in your project's settings. Secrets should *never* be committed directly to your repository.
    *   **Input parameters:** Some workflows use input parameters for customization. Check the workflow file for details.

3.  **Commit the changes:** Commit the copied workflow file to your project's repository.

## Workflows

### Pull Request Checks (`pull_request/`)

*   **`pull_request.yaml`:** Runs linting and unit tests on every pull request.

    ```yaml
    # Example usage in your project's .github/workflows/pull_request.yaml
    name: PR Checks
    on:
      pull_request:
        branches: [main]
    jobs:
      # ... (contents of the pull_request.yaml from this repo)
    ```

### Deploy (`deploy/`)

*   **`deploy.yaml`:** Deploys your application to a production server on pushes to the `main` branch.

    ```yaml
    # Example usage in your project's .github/workflows/deploy.yaml
    name: Deploy to Production
    on:
      push:
        branches: [main]
    jobs:
      # ... (contents of the deploy-to-production.yml from this repo)
    ```

### Commit Checks (`commit`)

*   **`commit.yaml`:** Validates commit messages to enforce conventional commits.

    ```yaml
    # Example usage in your project's .github/workflows/commit.yaml
    name: Commit Message Check
    on:
      pull_request_target:
    jobs:
      # ... (contents of the commit.yaml from this repo)
    ```

### Release (`release/`)

*   **`release.yaml`:** Automates package releases using semantic-release.

    ```yaml
    # Example usage in your project's .github/workflows/release.yaml
    name: Release Package
    on:
      push:
        branches:
          - main
    jobs:
      # ... (contents of the release.yaml from this repo)
    ```

## Contributing

Contributions are welcome! If you have a useful GitHub Action workflow that you would like to share, please open a pull request.

## License

[MIT License](LICENSE) (or choose your preferred license)