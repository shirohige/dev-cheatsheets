---
description: About the `npm version` command and how to use it
---
# version



## Purpose

This NPM command allows easy incrementing in both package files and git tags, with a given tag or increment level.

- [npm-version](https://docs.npmjs.com/cli/version) docs
    > Run this in a package directory to bump the version and write the new data back to package.json, package-lock.json, and, if present, npm-shrinkwrap.json.
    >
    > ...
    >
    > If run in a git repo, it will also create a version commit and tag.

This command will bump the version in `package.json` and tag that commit.


## Warning notes

- This requires Node.js / NPM to be installed.
- This only works if a project with a `package.json` file.
- This does not fetch remote tags, so you have to ensure yourself that you don't duplicate a remote tag.



## CLI

```sh
$ npm version --help
```
```
npm version [<newversion> | major | minor | patch | premajor | preminor | prepatch | prerelease [--preid=<prerelease-id>] | from-git]
(run in package dir)
'npm -v' or 'npm --version' to print npm version (6.14.4)
'npm view <pkg> version' to view a package's published version
'npm ls' to inspect current package/dependency versions
```


## Example use

Create a target version.
TODO check if v is needed.

```sh
$ npm version 0.1.0
```

Increment by a given level.

```sh
$ npm version major

$ npm version minor

$ npm version patch
```

There are other options as well but those are the most common.


## Configuration

This also allows setting commands to run when you run `npm version [options]`.

From [npm-run-scripts](https://docs.npmjs.com/misc/scripts) doc:

> - preversion: Run BEFORE bumping the package version.
> - version: Run AFTER bumping the package version, but BEFORE commit.
> - postversion: Run AFTER bumping the package version, and AFTER commit.

Example tasks:

- Ensure tests pass _before_ a tag is generated.
- Run a build command to output to `dist` directory and stage the directory, if relevant to your flow (I find this part is not needed for the projects I work in).
- Push the commits and tag and the clean build directory (I prefer to run clean before the build step and I don't know why temp is used here but I just copied that line).

Example configuration to match that:

- `package.json`
    ```json
    {
      "scripts": {
        "preversion": "npm run lint:check && npm test",
        "version": "npm run build && git add -A dist",
        "postversion": "git push --follow-tags && rm -rf build/temp"
      }
    }
    ```

### Warnings

Note for `--follow-tags` the help says:

```
    --follow-tags         push missing but relevant tags
```

I'm not confident in that description, as in my experience it only pushes the **current tag**, so any older commits that I had tagged didn't have tags pushed. So for the scripts command it is okay, but for general git use I still prefer `git push && git push --tags`, to be safe.

I recommend that you run `git fetch --tags` _before_ running `npm version`. To make sure you don't increment to a tag which already exists on the remote. So adding that logic into `preversion` can make that safer.

So here is a safer setup. Simplified to exclude the `add` and `rm` commands from above.

- `package.json`
    ```json
    {
      "scripts": {
        "preversion": "git fetch --tags && npm run lint:check && npm test",
        "version": "npm run build",
        "postversion": "git push --follow-tags"
      }
    }
    ```

If you use TypeScript, you must run your tests after the build step rather.


## Resources

- [semvar](https://docs.npmjs.com/misc/semver) NPM package.
- [About semantic versioning](https://docs.npmjs.com/about-semantic-versioning) in NPM docs.
