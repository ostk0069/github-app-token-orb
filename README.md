# GitHub App Token Orb

This CircleCI Orb can be used to impersonate a GitHub App when secrets.GITHUB_TOKEN's limitations are too restrictive and a personal access token is not suitable.


[![CircleCI Build Status](https://circleci.com/gh/ostk0069/github-app-token-orb.svg?style=shield "CircleCI Build Status")](https://circleci.com/gh/ostk0069/github-app-token-orb) [![CircleCI Orb Version](https://badges.circleci.com/orbs/ostk0069/github-app-token.svg)](https://circleci.com/orbs/registry/orb/ostk0069/github-app-token) [![GitHub License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://raw.githubusercontent.com/ostk0069/github-app-token-orb/master/LICENSE) [![CircleCI Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com/c/ecosystem/orbs)

## Usage

1. Create GitHub App. Follow the instruction [here](https://docs.github.com/en/developers/apps/building-github-apps/authenticating-with-github-apps)
2. Get, App Id, Installation Id, and Private Key
3. encode your private key to base64. run `base64 xxxxxxx.xxxxxxx.private-key.pem | cat`
4. Edit your .circleci/config.yml to get it ready.

## Example

```yml
version: '2.1'

orbs:
  github-app-token: ostk0069/github-app-token@0.1.0

workflows:
  use-my-orb:
    jobs:
      - github-app-token/fetch-token:
          app_id: << your app id >>
          base64_private_key: << your private key >>
          installation_id: << your installation id >>
```

## Parameters

PARAMETER|DESCRIPTION|REQUIRED|DEFAULT|TYPE
---|---|---|---|---|
app_id|ID of the GitHub App|Yes|-	|string
base64_private_key|Base64 encoded Private key of the GitHub App|Yes|-	|string
env_name|Enable to Customize Token ENV Name|No|GITHUB_APP_TOKEN	|string
installation_id|The ID of the installation for which the token will be requested (defaults to the ID of the repository's installation)|Yes|-	|integer


## Resources

[CircleCI Orb Registry Page](https://circleci.com/orbs/registry/orb/ostk0069/github-app-token) - The official registry page of this orb for all versions, executors, commands, and jobs described.

[CircleCI Orb Docs](https://circleci.com/docs/2.0/orb-intro/#section=configuration) - Docs for using, creating, and publishing CircleCI Orbs.

### How to Contribute

We welcome [issues](https://github.com/ostk0069/github-app-token-orb/issues) to and [pull requests](https://github.com/ostk0069/github-app-token-orb/pulls) against this repository!
