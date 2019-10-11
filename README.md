# semantic-release [![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org) [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release). 

Drone plugin for making semantic releases based on https://github.com/semantic-release/semantic-release.

## Usage

See [commit message format](https://github.com/semantic-release/semantic-release#commit-message-format) to use it.

Add the following to the drone configuration

```yml
kind: pipeline
name: default

steps:
- name: semantic-release
  image: sqeven/semantic-release
  settings:
    version_file: .tags # the file where the version will be persisted, defaults to .release-version
    git_user_name: sqeven # semantic release committer name (git config user.name)
    git_user_email: sqeven@example.com # semantic release committer email (git config user.email)
    github_token: # semantic release token (for authentication)
      from_secret: token
```

or for BitBucket

```yml
    bitbucket_token: # semantic release token (for authentication)
      from_secret: token
```

or for GitLab

```yml
    gitlab_token: # semantic release token (for authentication)
      from_secret: token
```

or for any git server (including BitBucket cloud which does not support tokens):

```yml
    git_login: bot
    git_password:
      from_secret: password
```

## What it does

Runs on master branch only. Skips any actions below while on other branches.

- automatically creates a semantic version number
- attaches the version number as repo's git tag
- exposes the version number into the file `.release-version`
- automatically creates, populates and pushes CHANGELOG.md to your master branch

## License

MIT
