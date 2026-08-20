# NCAP GHA Branch Automation Demo

Personal GitHub demo for testing the NCAP deployment-branch approach.

## One-time setup

1. GitHub repo -> Settings -> Environments -> New environment
2. Create environment: `NCAP-NONPROD`
3. GitHub repo -> Settings -> Actions -> General
4. Under Workflow permissions select `Read and write permissions`
5. Save.

No PAT or manually-created GITHUB_TOKEN secret is required.

## Test

1. Actions -> Demo Deploy -> Run workflow
2. Enter `main`
3. After successful deployment, the workflow updates:
   `NCAP_NONPROD_LAST_DEPLOYED_BRANCH`
4. Actions -> Create Deployment Branch -> Run workflow
5. The workflow automatically creates the next release branch using today's UTC date
   and the incremented version from the saved last-deployed branch. For example,
   `release/081726_v114PSUP` becomes `release/082026_v115PSUP` when run on August 20, 2026.
6. If `release/082026_v115PSUP` already exists and was not deployed on PSUP, the workflow displays a warning containing the branch and developer name.
7. After displaying the warning, the workflow automatically creates `release/082026_v116PSUP` and its matching staging branch.

The environment variable is updated only after a successful deployment.
