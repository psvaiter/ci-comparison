# CI Comparison

This project is intended to compare CI pipeline as code from different vendors.

### Azure Pipelines

### Bitbucket Pipelines

- ❌ support multiple configuration files
- ✅ git clone depth specification
- ✅ run pipeline based on changes of a specific fileset
- ⬜ reuse steps
- ⬜ reuse jobs
- ❌ conditional steps
- ✅ manual approval / trigger
    - ❌ selected approvers
    - ❌ explicit rejection
- ❌ abandon release
- ❌ environment variables separated by stage
- ✅ dedicated pull request configuration
- ❌ status badges

Notes:
- separated by deployment environment
- only one step can be marked as deployment for a sepecific environment

### CircleCI

- ❌ support multiple configuration files
- ❌ git clone depth specification
- ❌ run pipeline based on changes of a specific fileset
- ✅ reuse steps (with commands)
- ✅ reuse jobs (customized with parameters)
- ✅ conditional steps
- ✅ manual approval / trigger
    - ❌ selected approvers
    - ❌ explicit rejection
- ❌ abandon release
- ❌ environment variables separated by stage (there's not such a concept in CircleCI)
- ❌ dedicated pull request configuration
- ✅ status badges

Notes:
- Canceled workflows does not update status in GitHub, keeping the yellow circle on commit.
- In order to run pipeline based on files changed, there are two alternatives:
    - (alternative 1) use a `setup workflow` that always run and path-filtering orb
    - (alternative 2) use an always run job that executes a script responsible to detect files changed in git log and trigger the corresponding workflow job via API ([see more](https://medium.com/labs42/monorepo-with-circleci-conditional-workflows-69e65d3f1bd0))
- Environment variables are all registered in the same place regardless the deployment environment. Also values cannot be read or edited so it makes more convenient to keep only secrets registered in UI and non-sensitive values registered in configuration file.
- All commits trigger the workflows. A project configuration can be enabled to trigger only for branches with pull requests open.