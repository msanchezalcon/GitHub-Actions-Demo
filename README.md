# GitHub Actions Demo
## Running **Super-Linter** from the Marketplace

Welcome to this demo where we showcase how to automate code quality checks using **Super-Linter**, a powerful GitHub Action that analyzes source code and reports issues as console output and status checks.

## What is Super-Linter?

**Super-Linter** is a combination of several linters that help ensure your code follows best practices and conforms to industry standards. It automatically checks code syntax and styling across multiple languages and formats.

In this example, the linter is triggered whenever code is pushed to the repository, ensuring that all new code is checked against our linting rules before it is merged.


## Key Terminology for Understanding GitHub Actions

- **Events**: Trigger the workflow (e.g., code push, pull request).
- **Jobs**: Independent tasks that run in the workflow, either sequentially or in parallel.
- **Runner**: The server (GitHub-hosted or self-hosted) that runs your jobs.
- **Steps**: Individual commands or tasks within a job.
- **Actions**: Predefined reusable components used in steps to perform tasks.


## Setting Up Your First GitHub Action

### 1. Define Your Workflow in a YAML File

Create a new YAML file under `.github/workflows` to define your GitHub Action.

```yaml
name: Super-Linter

on: push

jobs:
  super-lint:
    name: Lint code base
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Run Super-Linter
        uses: github/super-linter@v4
        env:
          DEFAULT_BRANCH: main
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### What Does This Workflow Do?

1. **Event**: The workflow is triggered whenever code is pushed to the repository.
2. **Job**: A job named **super-lint** runs to check the code quality.
3. **Environment**: The job runs on the latest **Ubuntu** server hosted by GitHub.
4. **Steps**:
   - **Checkout Code**: Pulls the latest code from the repository.
   - **Run Linter**: Runs the **Super-Linter** to check if the code adheres to the linting standards.

With this setup, every push to your repository automatically triggers a linter check, ensuring code quality and conformity to standards.


### 2. Push Some Code and Check the Results

For the purpose of this demo, we intentionally added errors to a Python file to demonstrate the linter in action.

![Super-Linter Status](https://github.com/user-attachments/assets/cfe784e2-78db-49a1-ac34-3959c4ff9c21)


### 3. Review the Logs and Fix Your Code

In case of failure, examine the detailed logs to identify the issues, fix your code, and push the changes again.

![Super-Linter Logs](https://github.com/user-attachments/assets/834aabfb-4cf2-4cb4-83e0-c145d0d82d37)


### 4. Explore the GitHub Marketplace

Check out the [GitHub Marketplace](https://github.com/marketplace?type=actions) for more pre-built GitHub Actions you can integrate into your workflows. Many options are available for automating tests, deployments, and much more.
