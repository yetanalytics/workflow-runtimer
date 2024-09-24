# yetanalytics/workflow-runtimer

This repository uses GitHub Actions to create Java runtimes for use in Yet projects like [SQL LRS](https://github.com/yetanalytics/lrsql). This workflow is built off of the [runtimer](https://github.com/yetanalytics/runtimer) workflow, but conforms to our current guidelines for workflow naming and tagging. 

## Reusable GitHub Action

This repo contains a [reusable workflow](https://docs.github.com/en/actions/learn-github-actions/reusing-workflows) you can call up in a GitHub Action:

``` yaml
  build:
    uses: yetanalytics/workflow-runtimer/.github/workflows/runtimer.yml@< sha | tag | branch >
    with:
      java-version: '11'
      java-distribution: 'temurin'
      java-modules: 'java.base,java.logging,java.naming,java.xml,java.sql,java.transaction.xa,java.security.sasl,java.management'
  draft_release:
    needs: build
    runs-on: ubuntu-latest
    steps:
      ...
```

This will create runtimes for the following operating systems:
- MacOS Monterey 12
- Ubuntu 20.04
- Windows Server 2022

