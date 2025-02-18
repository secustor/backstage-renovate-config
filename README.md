# backstage-renovate-config
Holds Renovate presets targeted at Backstage repos

> [!NOTE]
> Be aware that this requires significant trust in the owner of this repository as it always the case for external Renovate presets!
This is as it can introduce changes without your input in case you are not requiring approval for PRs or allow merging changes in without PRs.
YOU HAVE BEEN WARNED!

## Usage
This repository contains a set of Renovate presets that can be used to configure Renovate for Backstage repositories.

To use these presets, you need to add a `renovate.json` file to your repository that looks like this:
```json
{
  "extends": [
    "github>secustor/backstage-renovate-config"
  ]
}
```
The above config will use the `default` preset.

If you want to use different presets, you can specify them like this:
```json
{
  "extends": [
    "github>secustor/backstage-renovate-config:self-hosted.json5"
  ]
}
```
The above config will use the `self-hosted` preset.

For more information on how to configure Renovate presets, see the [Renovate documentation](https://docs.renovatebot.com/config-presets/)

## Available full config presets

### `default`

This preset is the default one and is meant
to be used for Backstage repositories where ever they are hosted.
It is an opinionated preset to be used for the most common use cases.

### `app`

This preset is currently the same as the `default` preset,
but is intended for users of the Mend.io Github App.
In the future, it might contain additional features that are only available for users of the app.

### `self-hosted`

Requires access to `postpostUpgradeTasks` and `allowedPostUpgradeCommands` which are only available for self-hosted Renovate instances.
This means that [`allowedPostUpgradeCommands`](https://docs.renovatebot.com/self-hosted-configuration/#allowedpostupgradecommands) is configured to allow running `yarn backstage-cli versions:bump` commands

## Feature presets

### Unsupported Framework Upgrades
Prevent upgrades to frameworks that are not supported by Backstage.

### Group by plugin
Groups all PRs based on the plugin. Therefore, all updates of the `catalog` are grouped together including `catalog`, `catalog-backend` and so on. 

### Exclude ESM updates
Backstage does not support ESM at the moment. This means updates which are ESM-only will break the setup. 
This rule prevents updates to known ESM-only packages. 

### Update `backstage.json`
This rule will update the `backstage.json` file in the repository to the latest Backstage release.
It is used by full config presets, but can also be used standalone.

## Contributing
If you want to propose a new preset or modify an existing one, you can open a PR with the changes.

