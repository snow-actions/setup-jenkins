# Workflows

## Test

- Automatically run `test.yml`.

## Release

1. Manually dispatch `increment-version.yml` and it will create a PR.
2. Manually merge the PR.
3. Automatically trigger `draft-release.yml` and it will create a release.
4. Manually publish the release.
5. Automatically trigger `released.yml` and it will tweet as [@snow_cait](https://twitter.com/snow_cait).
