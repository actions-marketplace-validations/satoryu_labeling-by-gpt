# Labeling by GPT

When creating new issue, this action puts labels to an issues in the repository autocratically without pre-defined rule.
This is powered by OpenAI completion API to choose suitable labels.

Please note that this action supports only `issues` trigger and the two types: `opened` and `edited`.

## Inputs

### `openai-api-key`

**Required** Your OpenAI API Key.

### `github-token`

Optional.
GitHub API token to access GitHub API.
The default value is `secrets.GITHUB_TOKEN`, an API token provided for an action.
Be sure of that this token has a permission to put labels to an issue.
[This document](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#setting-the-permissions-of-the-github_token-for-your-repository) would help you.

## Example

```yaml
on:
  issues:
    types: [opened, edited]

jobs:
  test:
    name: test
    runs-on: ubuntu-latest

    steps:
      - uses: satoryu/labeling-by-gpt@main
        with:
          openai-api-key: ${{ secrets.OPENAI_API_KEY }}
```
