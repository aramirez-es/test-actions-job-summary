# Test Actions Job Summary

The goal of this repository is to show how the `Job Summary` works on GitHub Actions
with composite actions.

The [Entrypoint](.github/workflows/entrypoint.yml) is a simple workflow file with few steps

* Checkout the code
* Run a composite action

The [Composite Action](./composite/action.yml) is a sequence of simple steps. Some of these steps produce markdown
output piped into the `$GITHUB_STEP_SUMMARY`.

* Simple Setup step
* Run any other step
* Simple wrap up step

## Expected Behaviour

Every content piped to `$GITHUB_STEP_SUMMARY` within the Composite Action gets shown in the
Job summary for the workflow defined as Entrypoint.

## Actual Behaviour

Only the latest content piped `$GITHUB_STEP_SUMMARY` in the Composite Action gets shown.
