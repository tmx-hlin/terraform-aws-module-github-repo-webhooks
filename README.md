
# terraform-aws-module-github-repo-webhooks


## Usage

Create a GitHub Personal Access Token that has `admin:repo_hook` for full control of repository hooks; in otherwords, we need `write:repo_hook` to write repository hooks and `read:repo_hook` to read repository hooks.

```hcl
module "github_webhooks" {
  source              = "git::https://github.com/cloudposse/terraform-github-repository-webhooks.git?ref=master"
  github_organization = "cloudposse"
  github_token        = "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
  github_repositories = "geodesic"
  webhook_url         = "https://atlantis.prod.company.com/"
  content_type        = "json"
  events              = ["issues"]
}
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| active | Indicate of the webhook should receive events. | string | `true` | no |
| enabled | Whether or not to enable this module | string | `true` | no |
| events | A list of events which should trigger the webhook. | list | `<list>` | no |
| github_organization | GitHub organization to use when creating webhook | string | - | yes |
| github_repositories | List of repository names which should be associated with the webhook | list | `<list>` | no |
| github_token | GitHub token used for API access | string | - | yes |
| name | The type of webhook | string | `web` | no |
| webhook_content_type | Webhook Content Type (E.g. json) | string | `json` | no |
| webhook_insecure_ssl | Webhook Insecure SSL (E.g. trust self-signed certificates) | string | `false` | no |
| webhook_secret | Webhook secret | string | `` | no |
| webhook_url | Webhook URL | string | - | yes |
