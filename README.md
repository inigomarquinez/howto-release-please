# HOW TO - Release please

POC to use Google's [release-please github action](https://github.com/google-github-actions/release-please-action) to create releases.

## Steps

1. You need to follow the steps described [here](https://github.com/google-github-actions/release-please-action#setting-up-this-action).
2. The GitHub action can be configured with [these parameters](https://github.com/google-github-actions/release-please-action#setting-up-this-action).
3. release-please requires a GitHub token to access the GitHub API. You configure this token via the token configuration option.

## Take into account

- It is highly recommended that you use **squash-merges** when merging pull requests (ser more details [here](https://github.com/googleapis/release-please#linear-git-commit-history-use-squash-merge)).

    ![squash and merge](/assets/squash-and-merge.png)

- `RequestError [HttpError]: Error creating Pull Request: Resource not accessible by personal access token`
    
    This means that you need to add **read and write** access to the `Pull Requests` persmissions of your GitHub token. [see here](https://docs.github.com/en/rest/git/refs?apiVersion=2022-11-28#create-a-reference)

    ![pull requests permission](/assets/pull-requests-permission.png)

## Useful links

- [Release Please](https://github.com/googleapis/release-please)
- [Release Please Action](https://github.com/google-github-actions/release-please-action)
- [Conventional Commits](https://www.conventionalcommits.org)
- [commitlint](https://commitlint.js.org/#/)
- [husky](https://typicode.github.io/husky/)
- [Permissions required for fine-grained personal access tokens](https://docs.github.com/en/rest/overview/permissions-required-for-fine-grained-personal-access-tokens?apiVersion=2022-11-28)
