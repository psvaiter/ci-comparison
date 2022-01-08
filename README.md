# CI Comparison

This project is intended to compare CI pipeline as code from different vendors.

### CircleCI

- ❌ support multiple configuration files
- ❌ git clone depth specification
- ❌ run pipeline based on changes of a specific fileset
    - (alternative 1) use a `setup workflow` that always run and path-filtering orb
    - (alternative 2) use an always run job that executes a script responsible to detect files changed in git log and trigger the corresponding workflow job via API ([see more](https://medium.com/labs42/monorepo-with-circleci-conditional-workflows-69e65d3f1bd0))
- ✅ reuse steps (with commands)
- ✅ reuse jobs (customized with parameters)
- ✅ conditional steps
- ✅ manual approval
- ❌ explicit rejection (user has to cancel workflow instead)
- ❌ abandon release
- ❌ environment variables separated by stage (there's not such a concept in CircleCI)