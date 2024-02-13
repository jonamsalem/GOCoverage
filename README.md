# Go-Coverage

This GitHub Action performs unit tests, generates a coverage report, and checks if each file's coverage meets the threshold. 

Coverage that does not meet the required threshold will fail the step, ans list the undercovered files under the action logs.

By default, when the test fails, an HTML coverage report will be generated as an artifact which is stored for 2 days. 

Additonally, users will have the option to generate the artifact regardless of the status of the coverage.

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
        uses: jonamsalem/Go-Coverage@v1
        with:
          threshold: 80  #custom threshold - if not provided set to 70
          generate_artifact: true #generate artifact regardless of test status
