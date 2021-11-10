# yetanalytics/runtimer

This repository uses GitHub Actions to create Java runtimes for use in Yet projects like [SQL LRS](https://github.com/yetanalytics/lrsql)

## Reusable GitHub Action

This repo contains a [reusable workflow](https://docs.github.com/en/actions/learn-github-actions/reusing-workflows) you can call up in a GitHub Action:

``` yaml
  build:
    uses: yetanalytics/runtimer/.github/workflows/runtimer.yml@< sha | tag | branch >
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

## (DEPRECATED) Release JRE Runtime Packages

Create JRE runtimes:

1. Edit the [workflow file](.github/workflows/main.yml)
2. Push a tag
3. You'll find a draft release waiting for you for the given tag, describe and publish it.

That's it!
