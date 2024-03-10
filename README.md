# Go-Coverage

This GitHub Action performs unit tests, generates a coverage report, and checks if each file's coverage meets the threshold (%code covered by tests). 

Coverage that does not meet the required threshold will fail the step.

The logs will display the total statement coverage +  if relevant, the coverage of each undercovered file

When the test fails, an HTML coverage report will be generated as an artifact which is stored for 2 days. 

## Usage

Users will have the option to set two custom conditions:
* `threshold` - default set to 70%
* `generate_artifact` -  generate the cover report artifact when test passed (by default set to false). Note that failed tests will ALWAYS generate the report.

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
          threshold: 80 
          generate_artifact: true

```

## Example Result
```
github.com/jonamsalem/test-coverage/test	coverage: 33.3% of statements
github.com/jonamsalem/test-coverage/test	0.003s	coverage: 33.3% of statements

Files under threshold ( 90% ):
        github.com/jonamsalem/test-coverage/test/add.go (50.0%)
  

Error: Process completed with exit code 1.
With the provided path, there will be 1 file uploaded
Starting artifact upload ...
```

## Example Artifact


![Screenshot 2024-02-13 at 2 53 50 PM](https://github.com/jonamsalem/Go-Coverage/assets/133527937/891b30a5-5839-48c2-a17f-d8de97183d60)

