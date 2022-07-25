# Generate token and private checkout

Super simple composite action to generate a GitHub installation token and checkout a private repository using it. Requires a GitHub App installed to the private repository you're trying to clone, with `contents:read` permission.

Under the hood it depends on:
- https://github.com/tibdex/github-app-token
- https://github.com/actions/checkout

## Inputs:

## `app_id`

**Required** The ID of your GitHub app

## `private_key`

**Required** The private key for your GitHub app

## `installation_id`

**Required** The installation ID for your GitHub app (must be installed to the repository you're cloning)

## `repository`

**Required** The repository you want to checkout

## `ref`

**Required** The git ref you want to checkout

## `path`

**Optional** The path you want to clone to. Default to `"."`

## Outputs:

## `token`

The GitHub token generated. Useful in case you plan to do additional work with it (in addition to pulling the repository).

## Usage
```yml
- name: Checkout secrets
  uses: Drowze/action-gen-token-and-private-checkout@v1.0.0
  with:
    app_id: ${{ secrets.APP_ID }}
    private_key: ${{ secrets.APP_PRIVATE_KEY }}
    installation_id: ${{ secrets.APP_INSTALLATION_ID }}
    repository: Organisation/secrets
    ref: main
    path: secrets
```
