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
    "github>secustor/backstage-renovate-config:self-hosted"
  ]
}
```
The above config will use the `self-hosted` preset.

For more information on how to configure Renovate presets see the [Renovate documentation](https://docs.renovatebot.com/config-presets/)

## Available full config presets

### `default`
This preset is the default one and is meant to be used for Backstage repositories that are hosted on GitHub and makes use of features provided the hosted Mend App

## Contributing
If you want to propose a new preset or modify an existing one, you can open a PR with the changes.

