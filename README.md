# 🤔 HOW TO - Release please

POC to use Google's [release-please github action](https://github.com/google-github-actions/release-please-action) to create releases.

## 📝 Instructions

### Prerequisites

1. It is highly recommended that you use **squash-merges** when merging pull requests.
    * Read [this](https://github.com/googleapis/release-please#linear-git-commit-history-use-squash-merge) if you want to know **why**.
    * Read [this](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/configuring-commit-squashing-for-pull-requests) if you want to know **how** to do it.
      <figure>
        <img src="https://raw.githubusercontent.com/inigomarquinez/howto-release-please/main/assets/squash-and-merge.png" alt="Squash and merge" style="width:100%">
        <figcaption style="text-align: center; font-style: italic;">Squash and merge in GitHub</figcaption>
      </figure>

2. release-please requires a **GitHub token** to access the GitHub API.
    * Read [this](https://github.com/google-github-actions/release-please-action#github-credentials) if you want to to know **why**.
    * Read [this](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) if you want to know **how** to do it.
    * Your GitHub token needs to have at least *Read and Write* access to `code` and `pull requests`.
      <figure>
        <img src="https://raw.githubusercontent.com/inigomarquinez/howto-release-please/main/assets/github-token-permissions.png" alt="Github token permissions" style="width:100%">
        <figcaption style="text-align: center; font-style: italic;">Github token permissions</figcaption>
      </figure>
    * The repository needs to have access to the GitHub token so it can be read from the action using the `secrets` context. Read [this](https://docs.github.com/en/actions/security-guides/encrypted-secrets) for more information on configuring encrypted secrets.

3. Commits must follow the **[Conventional Commits](https://www.conventionalcommits.org/)** convention. You can enforce this by using tools such as [commitlint](https://commitlint.js.org/) and [husky](https://typicode.github.io/husky/).

    But apart from the commits, what is really important is that the **pull request title** follows the convention. This is because release-please uses the pull request title to determine the release type. You can use [this GitHub action](https://github.com/marketplace/actions/semantic-pull-request) to ensure it. You can find an example in this same repository. Take a look at the [./.github/workflows/lint-pull-request.yml](https://github.com/inigomarquinez/howto-release-please/blob/main/.github/workflows/lint-pull-request.yml) file.

    <div style="display: grid; grid-auto-flow: column; column-gap: 20px; align-items: center">
      <figure>
        <img src="https://raw.githubusercontent.com/inigomarquinez/howto-release-please/main/assets/invalid-pull-request-title.png" alt="Invalid pull request" style="width:100%" />
        <figcaption style="text-align: center; font-style: italic;">Invalid pull request title format</figcaption>
      </figure>
      <figure>
        <img src="https://raw.githubusercontent.com/inigomarquinez/howto-release-please/main/assets/valid-pull-request-title.png" alt="Valid pull request" style="width:100%" />
        <figcaption style="text-align: center; font-style: italic;">Valid pull request title format</figcaption>
      </figure>
    </div>

### Steps

1. Follow the [steps](https://github.com/google-github-actions/release-please-action#setting-up-this-action) described in the official documentation of the release-please action.

2. Remember that you can customize the GitHub action by using different [configuration parameters](https://github.com/google-github-actions/release-please-action#configuration).

    The most important ones are `token`, `release-type` and `package-name`.

### Take into account

* By default the PR doesn't include all the suported commit types, only the most important ones such as `feat` or `fix`.

  If you want to customize this, you can use the `changelog-types` input parameter as described [here](https://github.com/google-github-actions/release-please-action#overriding-the-changelog-sections).

* Release Please allows you to represent multiple changes in a single commit using footers, as described [here](https://github.com/googleapis/release-please#what-if-my-pr-contains-multiple-fixes-or-features).

## 🎁 Bonus track - Publish to npm

With a few additions, the Release Please action can be made to publish to npm when a Release PR is merged, as described [here](https://github.com/google-github-actions/release-please-action#automating-publication-to-npm).

## 👀 Example

You can find an example in this same repository. Take a look at the [.github/workflows/release-please.yml](https://github.com/inigomarquinez/howto-release-please/blob/main/.github/workflows/release-please.yml) file.

## 🔗 Useful links

* **release please** related documentation:
  - [Release Please](https://github.com/googleapis/release-please)
  - [Release Please action](https://github.com/google-github-actions/release-please-action)

* **GitHub** related documentation:
  - [Configuring commit squashing for pull requests](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/configuring-commit-squashing-for-pull-requests)
  - [Creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
  - [Encrypted secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets)
  - [Permissions required for fine-grained personal access tokens](https://docs.github.com/en/rest/overview/permissions-required-for-fine-grained-personal-access-tokens)

* **Conventional Commits** related documentation:
  - [Conventional Commits](https://www.conventionalcommits.org/)
  - [commitlint](https://commitlint.js.org/)
  - [husky](https://typicode.github.io/husky/)
