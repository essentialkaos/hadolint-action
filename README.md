<p align="center"><a href="#readme"><img src="https://gh.kaos.st/hadolint-action.svg"/></a></p>

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
        uses: actions/checkout@v3

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

### License

[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

<p align="center"><a href="https://essentialkaos.com"><img src="https://gh.kaos.st/ekgh.svg"/></a></p>
