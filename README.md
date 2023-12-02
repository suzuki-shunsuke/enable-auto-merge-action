# enable-auto-merge-action

GitHub Actions to enable auto-merge

## How to use

GitHub App

```yaml
jobs:
  enable-auto-merge:
    runs-on: ubuntu-latest
    permissions: {}
    if: |
      ! failure() && ! cancelled() && github.event.pull_request.user.login == 'renovate[bot]' && contains(github.event.pull_request.body, ' **Automerge**: Enabled.')
    steps:
      - uses: suzuki-shunsuke/enable-auto-merge-action@main
        with:
          pr_number: ${{github.event.pull_request.number}}
          merge_method: squash
          github_app_id: ${{secrets.APP_ID}}
          github_app_private_key: ${{secrets.APP_PRIVATE_KEY}}
```

GitHub Actions Token

```yaml
      - uses: suzuki-shunsuke/enable-auto-merge-action@main
        with:
          pr_number: ${{github.event.pull_request.number}}
          github_token: ${{github.token}}
```

## LICENSE

[MIT](LICENSE)
