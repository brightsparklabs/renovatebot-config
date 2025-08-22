# Renovatebot Config

This repository exposes a standard RenovateBot config file to be imported by other `renovate.json5` configurations.
See https://docs.renovatebot.com/configuration-options/

## Rules

This config has 2 main rules:

. Minor/Patch Updates - Automatically merged.
. Major Updates - PR created.

## Usage

To use this config, import it in the `renovate.json5` file of the specific repository.

```json
{
    extends: [
        'config:recommended',
        'github>brightsparklabs/renovatebot-config'
    ],
}
```

## Changes

There are a couple of things which should be configured by the importing repository.

### Reviewers

You will need to define which users will be asked to review any PR created by RenovateBot.
This can be donw by either their username (in the Github/Bitbucket platform hosting that repository) or by a group.

```json
{
    reviewers: [
        '<some-user>',
        '<another-user>',
        'team:<some-group>',
    ],
}
```

### Rules

Custom rules can be included for any project-specific requirements.

```json
{
    packageRules: [
        {
            # Sets up a Gradle rule to not upgrade past `8.x.x`.
            "groupName": "Gradle",
            "matchManagers": ["gradle-wrapper"],
            "allowedVersions": "<=8.x"
        },
}
],
```
