# CI Comparison

This project is intended to compare CI pipeline as code from different vendors.

### CircleCI

- ❌ git clone depth specification
- ❌ run pipeline based on changes of a specific fileset
    - 🟡 possible (but complex) with a setup workflow that always run and path-filtering orb
- ✅ reuse steps (with commands)
- ✅ reuse jobs (customized with parameters)
- ✅ conditional steps
- ✅ manual approval
- ❌ explicit rejection (user has to cancel workflow instead)
- ❌ abandon release
- ❌ environment variables separated by stage (there's not such a concept in CircleCI)