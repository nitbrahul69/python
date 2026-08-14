# NCAP GHA Last Deployed Branch Demo

Small Python project to test the GitHub Actions approach for storing the last successfully deployed branch in a GitHub Environment variable.

## What this demo does

1. `deploy.yml` simulates a deployment.
2. Only after a successful deployment, it updates the GitHub Environment variable:
   `NCAP_NONPROD_LAST_DEPLOYED_BRANCH`
3. `create-deployment-branch.yml` reads that variable and creates a new branch from it.

## GitHub setup

Create a GitHub Environment named:

`NCAP-NONPROD`

No Environment variable needs to be created manually. The deployment workflow creates/updates it.

### Important permissions

The workflow needs permission to update repository Environment variables. The demo uses `GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}` and `actions: write`.

If your organization restricts this token, use an approved GitHub App/PAT instead.

## Test

1. Push this project to a GitHub repository.
2. Run **Demo Deploy** manually and enter:
   `main`
3. It will simulate deployment and then set:
   `NCAP_NONPROD_LAST_DEPLOYED_BRANCH=main`
4. Run **Create Deployment Branch**.
5. Enter a new branch name such as:
   `release/081426_v1PSUP`
6. The workflow reads the environment variable and creates the new branch from the saved branch.

For a realistic test, create another branch, run Demo Deploy using that branch, and then run Create Deployment Branch again.
