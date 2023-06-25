## OVERVIEW

GitHub Action for Fork and Pull Request Development

This GitHub Action provides a command to pull the branch of a pull request for reviewers. It automatically appends a pull command to the description of a Pull Request, making it easier for reviewers to pull and review your changes locally.

For example
```
git fetch upstream pull/1/head:feature/add_comment && git checkout feature/add_comment
```

<img width="910" alt="sample_pr" src="https://github.com/kz-d/pr-pull-command/assets/116164465/ef350de4-8678-4369-9313-ad71e3ab2bd6">


## Motivation
If you often find yourself manually copying the branch name or pull request number from the GitHub interface and merging it with your local command every time you receive a pull request for review, this tool might offer a slight boost to your workflow.



## Usage

```yml
on:
  pull_request:
    types: [opened]  # WARN: Cannot specify anything other than 'opened'

permissions:
  contents: read
  pull-requests: write

jobs:
  add-pull-command:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Add a pull command to the description section of a GitHub Pull Request
        uses: kz-d/pr-pull-command@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```


## License
MIT 
