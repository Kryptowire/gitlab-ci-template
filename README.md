# How to use

This template can be copied directly into your `.gitlab-ci.yml` file or can be imported as a remote file.

```yml
include:
  - remote: "https://raw.githubusercontent.com/Kryptowire/gitlab-ci-template/main/analysis.yml"
```

Once the template is included within the file, you can create a new job to run within your pipelines. Jobs that extend this script must define the variables as below.

```yml
mast_analysis:
  stage: test
  variables:
    VERSION: "1.0.0"

    MAST_REST_API: "https://api.kryptowire.com"
    MAST_REST_API_KEY: $MAST_REST_API_KEY

    SCORE_THRESHOLD: $SCORE_THRESHOLD
    MAX_ANALYSIS_TIME: $MAX_ANALYSIS_TIME

    BINARY_FILE_PATH: $BINARY_FILE_PATH
    RESULTS_DIR: $RESULTS_DIR
  extends: .analysis
```

These variables can be filled either directly within the YAML file or can use the CI/CD variables within GitLab.

Users are recommended to use a specific version, however, if a specific version is not defined, this defaults to `latest`
