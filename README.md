# action-python

## Usage

This example workflow would build, lint, and test a python project.

```
workflow "Build and Test" {
  on = "push"
  resolves = [
    "Test",
  ]
}

action "Build" {
  uses = "gieseladev/python-actions@3.7"
  args = "pip install -r requirements.txt"
}

action "Lint" {
  uses = "gieseladev/python-actions@3.7"
  args = "black --check"
  needs = ["Build"]
}

action "Test" {
  uses = "gieseladev/python-actions@3.7"
  args = "pytest"
  needs = ["Lint"]
}
```
