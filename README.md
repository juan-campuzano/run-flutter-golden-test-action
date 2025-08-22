# Run Flutter Golden Tests Action

[![Version](https://img.shields.io/badge/version-v0.0.1-blue)](https://github.com/juan-campuzano/run-flutter-golden-test-action/releases/tag/v0.0.1)

A reusable GitHub Action to run Flutter golden tests in CI environments and upload failure artifacts for easy inspection.

## Features

- Sets up Flutter (configurable channel) in CI
- Caches dependencies (`pub`) for faster runs
- Executes golden tests using `xvfb-run` for headless environments
- Uploads failure artifacts (diffs, actual vs. expected images) as downloadable artifacts
- Configurable artifact retention period

## Usage

### In your workflow (`.github/workflows/ci.yml`)

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: ["**"]

jobs:
  golden_tests:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Run Flutter Golden Tests
        uses: juan-campuzano/run-flutter-golden-test-action@v0.0.1
        with:
          flutter-channel: stable         # Optional: defaults to 'stable'
          retention-days: 7               # Optional: defaults to 7
