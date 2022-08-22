---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "gitlab_project_membership Data Source - terraform-provider-gitlab"
subcategory: ""
description: |-
  The gitlab_project_membership data source allows to list and filter all members of a project specified by either its id or full path.
  -> Note exactly one of projectid or fullpath must be provided.
  Upstream API: GitLab REST API docs https://docs.gitlab.com/ee/api/members.html#list-all-members-of-a-group-or-project
---

# gitlab_project_membership (Data Source)

The `gitlab_project_membership` data source allows to list and filter all members of a project specified by either its id or full path.

-> **Note** exactly one of project_id or full_path must be provided.

**Upstream API**: [GitLab REST API docs](https://docs.gitlab.com/ee/api/members.html#list-all-members-of-a-group-or-project)

## Example Usage

```terraform
# By project's ID
data "gitlab_project_membership" "example" {
  project_id = 123
}

# By project's full path
data "gitlab_project_membership" "example" {
  full_path = "foo/bar"
}

# Get members of a project including all members
# through ancestor groups
data "gitlab_project_membership" "example" {
  project_id = 123
  inherited  = true
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- `full_path` (String) The full path of the project.
- `inherited` (Boolean) Return all project members including members through ancestor groups
- `project_id` (Number) The ID of the project.
- `query` (String) A query string to search for members

### Read-Only

- `id` (String) The ID of this resource.
- `members` (List of Object) The list of project members. (see [below for nested schema](#nestedatt--members))

<a id="nestedatt--members"></a>
### Nested Schema for `members`

Read-Only:

- `access_level` (String)
- `avatar_url` (String)
- `expires_at` (String)
- `id` (Number)
- `name` (String)
- `state` (String)
- `username` (String)
- `web_url` (String)

