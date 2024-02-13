# Coverage Action

This GitHub Action performs unit tests, generates a coverage report, and checks if each file's coverage meets the threshold (default is 70%). If the coverage does not meet the required threshold, the specific files will be listed under the action logs & an HTML coverage report will be generated as an artifact. 

## Usage

To use this action in your workflow, create a `.github/workflows/example.yml` file in your repository. Below is an example of how to implement the action:
```yaml
name: Test Coverage

on: [push]

jobs:
  test-coverage:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Go
        uses: actions/setup-go@v3

      
      - name: Run Coverage Action
        uses: jonamsalem/GOCoverage@v1
        with:
          threshold: 80
