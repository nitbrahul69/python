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
5. Enter a new branch such as:
   `release/081426_v1PSUP`
6. The workflow creates it from the saved last-deployed branch.

The environment variable is updated only after a successful deployment.

| Date | Environment | Branch | Creator |
|---|---|---|---|
| 2026-08-19 13:38:57Z | NCAP-NONPROD | staging/081726_v111PSUP | nitbrahul69 |
| 2026-08-21 03:17:23Z | NCAP-NONPROD | staging/082126_v118PSUP | nitbrahul69 |
