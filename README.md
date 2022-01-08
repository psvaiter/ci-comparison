# CI Comparison

This project is intended to compare CI pipeline as code from different vendors.

### Bitbucket Pipelines

- ❌ support multiple configuration files
- ✅ git clone depth specification
- ✅ run pipeline based on changes of a specific fileset
- ⬜ reuse steps
- ⬜ reuse jobs (customized with parameters)
- ❌ conditional steps
- ✅ manual approval / trigger
    - ❌ selected approvers
    - ❌ explicit rejection
- ❌ abandon release
- ❌ environment variables separated by stage
    - separated by deployment environment
    - only one step can be marked as deployment for a sepecific environment
- ✅ dedicated pull request configuration
- ❌ status badges

### CircleCI

- ❌ support multiple configuration files
- ❌ git clone depth specification
- ❌ run pipeline based on changes of a specific fileset
    - (alternative 1) use a `setup workflow` that always run and path-filtering orb
    - (alternative 2) use an always run job that executes a script responsible to detect files changed in git log and trigger the corresponding workflow job via API ([see more](https://medium.com/labs42/monorepo-with-circleci-conditional-workflows-69e65d3f1bd0))
- ✅ reuse steps (with commands)
- ✅ reuse jobs (customized with parameters)
- ✅ conditional steps
- ✅ manual approval / trigger
    - ❌ selected approvers
    - ❌ explicit rejection
- ❌ abandon release
- ❌ environment variables separated by stage (there's not such a concept in CircleCI)
    - focused on secret only as values cannot be read nor edited
    - non-sensitive values should be versioned along pipeline config
- ❌ dedicated pull request configuration (all commits trigger the workflows and a project configuration can be enabled to trigger only for branches with pull requests open)
- ✅ status badges