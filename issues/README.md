# issues

This is a GitHub action that provides support for issue validation.

## Commands

### `"filter spam"`

This action is used to check whether or not an issue has been populated.

It currently validates that:
- the issue body is not empty
- the issue body is not only the contents of the issue template

If either of the above is not true, then the filter will return successfully
and allow the next action to run (e.g to reply with a comment and auto close).

The inverse command is available as `"filter not_spam"`

Usage:
```hcl
action "action-issue-valid" {
  uses = "endocrimes/issues/filter@master"
  args = "action synchronized"
}
```

