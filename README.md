# @wewise/typescript-config

Shared TypeScript base configuration used across wewise projects.

This package contains a single `base.json` TypeScript config that you can extend in your project.

Usage

- Install the package (from npm or your package registry):

  npm install @wewise/typescript-config --save-dev

- Extend it from your `tsconfig.json`:

```json
{
  "extends": "@wewise/typescript-config/base.json",
  "compilerOptions": {
    "outDir": "dist",
    "rootDir": "src"
  }
}
```

Notes about publishing

- This package is scoped (`@wewise/`); when publishing to the public npm registry the package must be published with `access: public` (this is already set in `package.json`).
- If you are using a private registry (GitHub Packages, Nexus, Artifactory, etc.), make sure your consuming projects have the proper `.npmrc` or registry configuration.

Files

- `base.json` – the TypeScript configuration file shipped by this package.

Repository

The canonical source for this package is:

https://github.com/wewise/typescript-config

Contributing

If you want to update the shared config, edit `base.json` and open a PR. Make sure to bump the package `version` in `package.json` when publishing.

Publishing

You can publish this package to npm or GitHub Packages. Below are example workflows.

Public npm

1. Make sure you're authenticated (usually via `npm login`) and the `publishConfig.access` is `public` (already set in `package.json`).
2. Bump the version in `package.json`, commit, tag, then run:

```bash
cd typescript-config
npm publish --access public
```

GitHub Packages (npm registry)

1. Create a Personal Access Token (PAT) with `repo` and `write:packages` scopes and store it in your CI or local `.npmrc` as described below.
2. Example `.npmrc` to add to consuming projects or CI (replace OWNER/REPO and USER/TOKEN as appropriate):

```
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
@wewise:registry=https://npm.pkg.github.com
```

Local validation

You can test what will be published using `npm pack` from the package directory. This will create a tarball of the package contents.

```bash
cd typescript-config
npm pack
```

This tarball can be installed in another project using `npm install <tarball-file>`.
