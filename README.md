# Test Actions Job Summary

The goal of this repository is to show how the `Job Summary` works on GitHub Actions
with composite actions.

## Workflow using a Composite Action

The [Entrypoint](.github/workflows/entrypoint-composite.yml) is a simple workflow file with few steps

* Checkout the code
* Run a **composite** action

The [Composite Action](./composite/action.yml) is a sequence of simple steps. Some of these steps produce markdown
output piped into the `$GITHUB_STEP_SUMMARY`.

* Simple Setup step
* Run any other step
* Simple wrap up step

### Expected Behaviour

Every content piped to `$GITHUB_STEP_SUMMARY` within the Composite Action gets shown in the
Job summary for the workflow defined as Entrypoint. As per the [official documentation](https://docs.github.com/en/actions/using-workflows/workflow-commands-for-github-actions#adding-a-job-summary)

> When a job finishes, the summaries for all steps in a job are grouped together into a single job summary and are shown on the workflow run summary page.

### Actual Behaviour

Only the latest content piped `$GITHUB_STEP_SUMMARY` in the Composite Action gets shown.

## Workflow with all the steps inlined

The [Entrypoint](.github/workflows/entrypoint-standalone.yml) is a workflow file with few steps

* Checkout the code
* Simple Setup step
* Run any other step
* Simple wrap up step


### Expected Behaviour

Every content piped to `$GITHUB_STEP_SUMMARY` within the Workflow gets shown in the
Job summary.

### Actual Behaviour

All the content piped to `$GITHUB_STEP_SUMMARY` by each single step in the workflow file
gets bundled and the Job Summary shows it properly.
