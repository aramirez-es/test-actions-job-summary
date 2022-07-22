# Test Actions Job Summary

The goal of this repository is to show how the Job Summary works on GitHub Actions
with multiple nesting level in composite actions.

The [Entrypoint](.github/workflows/entrypoint.yml) is a simple workflow file with few steps

* Checkout the code
* Run a composite action

The Composite Action is a sequence of simple steps. Some of these steps produce markdown
output piped into the `$GITHUB_STEP_SUMMARY` but also runs another composite action:

* Simple Setup step
* Run a nested composite action
* Simple wrap up step
