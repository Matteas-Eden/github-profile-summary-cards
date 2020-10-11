# GitHub Profile Summary Cards

![Unit Tests](https://github.com/vn7n24fzkq/github-profile-summary-cards/workflows/Unit%20Tests/badge.svg)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards/blob/master/LICENSE)
![release](https://img.shields.io/github/v/release/Matteas-Eden/github-profile-summary-cards.svg)

This repo is a fork of Yi-Heng's work [here](https://github.com/vn7n24fzkg/github-profile-summary-cards), which itself was inspired by David's work with [profile-summary-for-github](https://github.com/tipsy/profile-summary-for-github)

The action contained in this repository generates your github profile summary cards and pushes them to your repo.
You can also trigger the action by yourself after adding it.

`After you add this to your workflow, your should trigger the workflow then you can use those cards immediately.`

| :warning: | If your workflow does not generate all cards in output folder, then you need to use [Personal Access Token](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) instead of GITHUB_TOKEN in workflow.  |
| :-------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

[Creating a Personal Access Token
](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)

[Personal token permissions](https://github.com/Matteas-Eden/github-profile-summary-cards/wiki/Personal-access-token-permissions)

---

## Examples

![](https://raw.githubusercontent.com/Matteas-Eden/Matteas-Eden/master/profile-summary-card-output/github/0-profile-details.svg)
![](https://raw.githubusercontent.com/Matteas-Eden/Matteas-Eden/master/profile-summary-card-output/github/1-repos-per-language.svg)
![](https://raw.githubusercontent.com/Matteas-Eden/Matteas-Eden/master/profile-summary-card-output/github/2-most-commit-language.svg)
![](https://raw.githubusercontent.com/Matteas-Eden/Matteas-Eden/master/profile-summary-card-output/github/3-stats.svg)

<!-- [More example with themes](https://github.com/Matteas-Eden/github-profile-summary-cards-example/tree/master/profile-summary-card-output) -->

---

## Wiki

[How do I add this to my profile README?](https://github.com/Matteas-Eden/github-profile-summary-cards/wiki/Add-to-my-profile-README)

---

## GitHub Actions Usage

### `GITHUB_TOKEN`

| :warning: | If you get this error `Error: Resource not accessible by integration` then you need to use a [Personal Access Token](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) instead of GITHUB_TOKEN . |
| :-------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

The default token doesn't have permission for accessing private content, so if you want to calculate using that you will need to use [Personal Access Token](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets).

After the action is finished, you can see the output is pushed to a folder which is named `profile-summary-card-output`.

`Note: The cards might not be updated too frequently, because GitHub raw files have a caching time.`

```yml
name: GitHub-Profile-Summary-Cards

on:
  schedule: # execute every 24 hours
    - cron: "* */24 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate

    steps:
      - uses: actions/checkout@v2
      - uses: Matteas-Eden/github-profile-summary-cards@release
        env: # default use ${{ secrets.GITHUB_TOKEN }}, you can change to your personal access token
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          USERNAME: ${{ github.repository_owner }}
```

---

## Run Locally

- Built on NodeJS v12, so only that and above is supported.
- Add GITHUB_TOKEN to `.env` file, e.g. `GITHUB_TOKEN=abcdefghijklmnopqrstuvwxyz123456789`

```
yarn install
```

```
yarn run run [username]
```

:star: Feel free to fork the repo and create a PR! All contributions welcome! :star:
