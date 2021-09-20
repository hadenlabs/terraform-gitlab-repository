<!--


  ** DO NOT EDIT THIS FILE
  **
  ** 1) Make all changes to `provision/generator/README.yaml`
  ** 2) Run`task readme` to rebuild this file.
  **
  ** (We maintain HUNDREDS of open source projects. This is how we maintain our sanity.)
  **


  -->

[![Latest Release](https://img.shields.io/github/release/hadenlabs/terraform-gitlab-project)](https://github.com/hadenlabs/terraform-gitlab-project/releases) [![Lint](https://img.shields.io/github/workflow/status/hadenlabs/terraform-gitlab-project/lint-code)](https://github.com/hadenlabs/terraform-gitlab-project/actions?workflow=lint-code) [![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit) [![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow)](https://conventionalcommits.org) [![KeepAChangelog](https://img.shields.io/badge/Keep%20A%20Changelog-1.0.0-%23E05735)](https://keepachangelog.com)

# terraform-gitlab-project

terraform gitlab project

## Requirements

This is a list of plugins that need to be installed previously to enjoy all the goodies of this configuration:

- [python](https://www.python.org)
- [taskfile](https://github.com/go-task/task)

## Usage

```hcl

   module "main" {
      source = "hadenlabs/project/gitlab"
      version = "0.2.0"

      providers = {
        gitlab = gitlab
      }

      name        = "project-example"
      description = "gitlab project"
      visibility  = "public"
  }

```

Full working example can be found in [examples](./examples) folder.

## Examples

### common

```hcl

  module "main" {
      source = "hadenlabs/project/gitlab"
      version = "0.2.0"

      providers = {
        gitlab = gitlab
      }

      name        = "project-example"
      description = "gitlab project"
      visibility  = "public"
  }

```

### with group new

```hcl

  resource "gitlab_group" "example" {
    name        = "example"
    path        = "example"
    description = "An example group"
  }

  module "main" {
      source = "hadenlabs/project/gitlab"
      version = "0.2.0"

      providers = {
        gitlab = gitlab
      }

      namespace_id = gitlab_group.example.id
      name        = "project-example"
      description = "gitlab project"
      visibility  = "public"
  }

```

### with group exist

```hcl

  data "gitlab_group" "example" {
    full_path = "example"
  }

  module "main" {
      source = "hadenlabs/project/gitlab"
      version = "0.2.0"

      providers = {
        gitlab = gitlab
      }

      namespace_id = data.gitlab_group.example.id
      name        = "project-example"
      description = "gitlab project"
      visibility  = "public"
  }

```

 <!-- BEGIN_TF_DOCS -->

## Requirements

| Name                                                                     | Version |
| ------------------------------------------------------------------------ | ------- |
| <a name="requirement_terraform"></a> [terraform](#requirement_terraform) | >= 0.14 |
| <a name="requirement_gitlab"></a> [gitlab](#requirement_gitlab)          | >=3.5.0 |
| <a name="requirement_local"></a> [local](#requirement_local)             | >=1.3.0 |

## Providers

| Name                                                      | Version |
| --------------------------------------------------------- | ------- |
| <a name="provider_gitlab"></a> [gitlab](#provider_gitlab) | >=3.5.0 |

## Modules

No modules.

## Resources

| Name | Type |
| --- | --- |
| [gitlab_project.this](https://registry.terraform.io/providers/gitlabhq/gitlab/latest/docs/resources/project) | resource |

## Inputs

| Name | Description | Type | Default | Required |
| --- | --- | --- | --- | :-: |
| <a name="input_description"></a> [description](#input_description) | The description of the project. | `string` | n/a | yes |
| <a name="input_name"></a> [name](#input_name) | The name of the project. | `string` | n/a | yes |
| <a name="input_namespace_id"></a> [namespace_id](#input_namespace_id) | The namespace (group or user) of the project. | `string` | `null` | no |
| <a name="input_settings"></a> [settings](#input_settings) | Create and manage settings. | `map(any)` | `{}` | no |
| <a name="input_tags"></a> [tags](#input_tags) | topics or tags of project. | `list(string)` | `[]` | no |
| <a name="input_visibility"></a> [visibility](#input_visibility) | The visibility of the project private or public. | `string` | `"private"` | no |

## Outputs

| Name                                                        | Description             |
| ----------------------------------------------------------- | ----------------------- |
| <a name="output_instance"></a> [instance](#output_instance) | output instance project |

<!-- END_TF_DOCS -->

## Help

**Got a question?**

File a GitHub [issue](https://github.com/hadenlabs/terraform-gitlab-project/issues).

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/hadenlabs/terraform-gitlab-project/issues) to report any bugs or file feature requests.

### Development

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

1.  **Fork** the repo on GitHub
2.  **Clone** the project to your own machine
3.  **Commit** changes to your own branch
4.  **Push** your work back up to your fork

5.  Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to rebase the latest changes from "upstream" before making a pull request!

## Module Versioning

This Module follows the principles of [Semantic Versioning (SemVer)](https://semver.org/).

Using the given version number of `MAJOR.MINOR.PATCH`, we apply the following constructs:

1. Use the `MAJOR` version for incompatible changes.
1. Use the `MINOR` version when adding functionality in a backwards compatible manner.
1. Use the `PATCH` version when introducing backwards compatible bug fixes.

### Backwards compatibility in `0.0.z` and `0.y.z` version

- In the context of initial development, backwards compatibility in versions `0.0.z` is **not guaranteed** when `z` is increased. (Initial development)
- In the context of pre-release, backwards compatibility in versions `0.y.z` is **not guaranteed** when `y` is increased. (Pre-release)

## Copyright

Copyright © 2018-2021 [Hadenlabs](https://hadenlabs.com)

## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## License

The code and styles are licensed under the LGPL-3.0 license [See project license.](LICENSE).

## Don't forget to 🌟 Star 🌟 the repo if you like terraform-gitlab-project

[Your feedback is appreciated](https://github.com/hadenlabs/terraform-gitlab-project/issues)
