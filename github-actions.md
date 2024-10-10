# GitHub Actions

- [What is GitHub Actions?](#what-is-github-actions)
- [How It Works](#how-it-works)
- [Workflow File](#workflow-file)
- [Secrets](#secrets)

## What is GitHub Actions?

GitHub Actions is a CI/CD platform that allows you to automate your build, test, and deployment workflows directly within your GitHub repository.

## How It Works

GitHub Actions operates on workflows and actions. **Workflows** are defined by a YAML file and can consist of one or more jobs. **Jobs** are sets of steps that execute on the same runner. A **step** can either be a custom script or an **action**.

**Runner** is a OS that executes the jobs(tasks) in your workflow.

## Workflow File

A workflow file is a YAML file placed in the `.github/workflows` directory of your repository. This file defines your workflow configuration.

Example:
```yml
name: CI # The name of the workflow
on: [push] # push events to any branch trigger the workflow
jobs:
  build: # The name of the job
    runs-on: ubuntu-latest # The type of machine to run the job on
    steps:
      - uses: actions/checkout@v2 # Action for checking out a repo
      - name: Run a script # The name of the step
        run: echo Hello, world!
```

**Breaking down the actions/checkout@v2:**

- actions/: Indicates official actions provided by GitHub.
- checkout: This action is used for checking out (copying) the code from the repo.
- @v2: Specifies the version of the action.

In simple terms, this action is used to copy the code from the repo to the runner. This enables subsequent steps in the workflow, such as building, running tests, etc.



## Secrets

**Secrets** are encrypted environment variables that you create in a repository or organization. They can store sensitive information, such as API keys, access tokens, and passwords. You reference secrets using the `secrets` context.

Example:

1. Create new repository secret on GitHub: Repository Settings > Secrets > Actions
2. Get secret from yaml
```yml
steps:
  - name: Log in to Docker Hub
    uses: docker/login-action@v1
    with:
      username: ${{ secrets.DOCKERHUB_USERNAME }}
      password: ${{ secrets.DOCKERHUB_PASSWORD }}
```
