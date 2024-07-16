# Runs Source Operation Toolkit Auto Update 
GitHub action that runs the source operations toolkit to run an auto-update source operation.

## Inputs
* `github-token` - Github [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) with access rights to the target repository so we can work with the github api. **REQUIRED**.
* `platformsh_token` - A Platform.sh API Token. **REQUIRED**
* `update_branch_name` - The branch name the toolkit should target for running the update. _Optional_. Defaults to `''` 
which causes the toolkit to use the default branch name of `update`


## Example usage:
See `Run source ops` step below
```yaml
name: Trigger Source Operations on a Schedule
on:
  schedule:
    # Run at 00:15 every day
    - cron: '15 0 * * *'
  workflow_dispatch:

jobs:
  run-sourceops:
    name: run-sourceops
      steps:
        - name: 'Run source ops'
          id: run-source-op
          uses: platformsh/gha-run-sourceops-update@main
          with:
            github_token: ${{ secrets.TEMPLATES_GITHUB_TOKEN }}
            platformsh_token: ${{ secrets.TEMPLATES_CLI_TOKEN }}
```
