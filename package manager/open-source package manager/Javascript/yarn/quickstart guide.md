# yarn
## [intro](https://yarnpkg.com/getting-started)
yarn is an established open-source package manager used to manage dependencies in `JavaScript` projects.

## [installation](https://yarnpkg.com/getting-started/install)

> [!Tip]
> The preferred way to manage yarn is by-project and through `Corepack`[^1], a tool shipped by default with Node.js. Modern releases of yarn aren't meant to be installed globally, or from npm.

1. To start by enabling `Corepack`[^1], if it isn't already; this will add the yarn binary to your environment variable `PATH`. Run these commands with `administrator permission`. 

```
corepack enable
```

> [!CAUTION]
> Open the terminal with `administrator permission`.
>
> Otherwise, you will see a strange error -- EPERM.
>
> Look like this.
>
> ```
> Internal Error: EPERM: operation not permitted, open 'C:\Program Files\nodejs\pnpm'
> Error: EPERM: operation not permitted, open 'C:\Program Files\nodejs\pnpm'
> ```

2. To initialize a new project. Run these commands.

```
yarn init -2
```

## [update](https://yarnpkg.com/getting-started/install#updating-yarn)
Any time you'll want to update Yarn to the latest version, just run these commands.

```
yarn set version stable
```

```
yarn install
```

> [!TIP]
> yarn also frequently ships Release Candidate builds.
>
> Run `yarn set version canary` should you need a feature not released on the stable channel yet.
> 
> Those builds are very stable, the only difference with the regular channel being a more staggered migration between major as we implement new breaking changes.

## [Installing the latest build fresh from master](https://yarnpkg.com/getting-started/install#installing-the-latest-build-fresh-from-master)

You may want to test a version of Yarn so recent it hasn't been released in a Release Candidate yet, or even not merged. 

To clone, build, and install yarn in your project, straight from our repository, run these commands.

```
yarn set version from sources
```

> [!TIP]
> To test specific `PRs`,
>
> use `--branch` flag
>
> such as
> 
> ```
> yarn set version from sources --branch 1211
> ```

> [!WARNING]
> Unlike the stable and canary channels,
>
> `yarn set version from sources` command can't leverage `Corepack`[^1] and
>
> it will need to store the yarn binary inside the `.yarn/releases` folder and reference it from your project's `.yarnrc.yml` file.

## commands
See [CLI commands in yarn](https://yarnpkg.com/cli)

[^1]: [`Corepack`](https://yarnpkg.com/corepack)

