# Complex Workflow

This repository contains an example of a complex GitHub Actions workflow that demonstrates running jobs across multiple operating systems and job dependencies.

## Features

- **Multi-platform CI**: Runs jobs on Ubuntu, Windows, and macOS runners.
- **Job Dependencies**: Ensures specific jobs only run after others are completed.
- **Simple demonstration**: Each job executes a basic command for illustration.

## Workflow Overview

The workflow file `.github/workflows/complex.yml` includes:

- **ubuntu**: Runs on Ubuntu.
- **windows**: Runs on Windows.
- **macos**: Runs on macOS.
- **depends**: Runs after the above jobs complete.

Example snippet:

```yaml
jobs:
  ubuntu:
    runs-on: ubuntu-latest
    steps:
      - run: date

  windows:
    runs-on: windows-latest
    steps:
      - run: date

  macos:
    runs-on: macos-latest
    steps:
      - run: date

  depends:
    needs: [ubuntu, windows, macos]
    runs-on: macos-latest
    steps:
      - run: date
