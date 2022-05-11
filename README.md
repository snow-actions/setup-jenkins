[![Test](https://github.com/snow-actions/composite-action-template/actions/workflows/test.yml/badge.svg)](https://github.com/snow-actions/composite-action-template/actions/workflows/test.yml)

# Create a Composite Action

Click the `Use this template` to bootstrap the creation of a [composite action](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action).:rocket:

This template includes tests, a validation workflow and versioning guidance.

Learn how to use this template at [Wiki](https://github.com/snow-actions/composite-action-template/wiki).

## Usage

See [action.yml](action.yml)

### Basic

```yml
steps:
  - uses: snow-actions/composite-action-template@v1.0.0
```

### Optional

```yml
steps:
  - uses: snow-actions/composite-action-template@v1.0.0
    with:
      who-to-greet: Your name
```

## Environment variables

| Name | Description | Default | Required |
| - | - | - | - |
| `WHO_TO_GREET` | Who to greet | `World` | no |

## Inputs

| Name | Description | Default | Required |
| - | - | - | - |
| `who-to-greet` | Who to greet | `World` | yes |

## Outputs

| Name | Description |
| - | - |
| `greet` | The word we greeted you |

## Supported

### Runners

- `ubuntu-20.04`
- `ubuntu-18.04`
- `windows-2022`
- `windows-2019`
- `macos-11`
- `macos-10.15`
- `self-hosted`

### Events

- Any
<!--
- `push`
- `pull_request`
-->

## Dependencies

- [actions/cache](https://github.com/actions/cache) >= 3.0.0
- [GitHub CLI](https://cli.github.com/) >= 2.6.0

## Contributing

Welcome.
