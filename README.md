# regolith-action

A GitHub Action for Regolith Bedrock Addon compiler pipeline.

## Usage

### Pre-requisites

Create a workflow `.yml` file in your `.github/workflows` directory.

### Inputs

| Input          | Description                         | Default   |
| -------------- | ----------------------------------- | --------- |
| `profile`      | Regolith profile to run             | `default` |
| `github_token` | GitHub token to get private filters | None      |
| `branch`       | Branch to check out and build       | None (uses the existing checkout) |

### Example workflow

```yml
name: Example workflow
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: Bedrock-OSS/regolith-action@v1.0.3
        with:
          profile: default
```

### Building a specific branch

```yml
name: Build branch
on:
  workflow_dispatch:
    inputs:
      branch:
        description: "Branch to build (empty = default branch)"
        required: false
        default: ""
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: Bedrock-OSS/regolith-action@v1.0.3
        with:
          profile: default
          branch: ${{ inputs.branch }}
```
