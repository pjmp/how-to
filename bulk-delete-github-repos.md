### Perquisites:

- [Personal access tokens](https://github.com/settings/tokens) with `delete_repo` scope.
- `curl`, `xargs` & [jq](https://stedolan.github.io/jq/)
- token exported as `GITHUB_TOKEN` to the current shell session.

### Command:

```sh
curl -s --GET -H "Authorization: token $GITHUB_TOKEN" "https://api.github.com/user/repos" \
  | jq -r '.[].full_name' \
  | xargs -Irepo curl -XDELETE -H "Authorization: token $GITHUB_TOKEN" https://api.github.com/repos/repo
```

### Explanations:

