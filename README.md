<p align="center"><a href="#readme"><img src=".github/images/card.svg"/></a></p>

<br/>

Action for checking scripts with [Hadolint](https://github.com/hadolint/hadolint).

### Usage

Create file `.github/workflows/hadolint.yml`.

Add next code to it:

```yml
name: CI

on:
  push:
    branches: [master, develop]
  pull_request:
    branches: [master]

jobs:
  Hadolint:
    name: Hadolint
    runs-on: ubuntu-latest

    steps:
      - name: Code checkout
        uses: actions/checkout@v4

      - name: Check dockerfiles with Hadolint
        uses: essentialkaos/hadolint-action@v1
        with:
          format: json
          varbose: true
          strict-labels: true
          failure-threshold: warning
          trusted-registry: repo.domain.com
          files: alpine311.docker alpine312.docker

```

| Option | Description | Value |
|--------|-------------|--------|
| `files` | List of dockerfiles to check | _Paths_ |
| `version` | Version of Hadolint | _Version in semver notation_ |
| `format` | The output format for the results | `tty`<br/>`json`<br/>`checkstyle`<br/>`codeclimate`<br/>`gitlab_codeclimate`<br/>`codacy`<br/>`sonarqube` |
| `varbose` | Enables verbose logging | _Boolean_ |
| `strict-labels` | Do not permit labels other than specified in label-schema | _Boolean_ |
| `failure-threshold` | Exit with failure code only when rules with a severity equal to or above given | `error`<br/>`warning`<br/>`info`<br/>`style`<br/>`ignore`<br/>`none` |
| `trusted-registry` | A docker registry to allow to appear in FROM instructions | _String_ |

### License

[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

<p align="center"><a href="https://essentialkaos.com"><img src="https://gh.kaos.st/ekgh.svg"/></a></p>
