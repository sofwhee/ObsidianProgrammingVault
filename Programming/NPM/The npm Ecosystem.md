1. Packages (`package.json` files) exist 
2. They are "installed" and "consumed" by 
	1. `require`ing them in files
	2. `import`ing them in files
	3. `run` in the `command-line` as `binaries`. 
3. Ensure all required `package.json` files are present in `dependencies`
4. Application is fed into Webpack or Rollup (module bundlers) 
5. All required dependencies are pulled together and bundled (as the name suggests)

`package.json`

if you ran `npm install` npm would read this file and see it needs to install the `markdownlint-cli2` package.

```json
{
  "name": "curriculum",
  "version": "1.0.0",
  "description": "[The Odin Project](https://www.theodinproject.com/) (TOP) is an open-source curriculum for learning full-stack web development. Our curriculum is divided into distinct courses, each covering the subject language in depth. Each course contains a listing of lessons interspersed with multiple projects. These projects give users the opportunity to practice what they are learning, thereby reinforcing and solidifying the theoretical knowledge learned in the lessons. Completed projects may then be included in the user's portfolio.",
  "scripts": {
    "lint:lesson": "markdownlint-cli2 --config lesson.markdownlint-cli2.jsonc",
    "lint:project": "markdownlint-cli2 --config project.markdownlint-cli2.jsonc",
    "fix:lesson": "markdownlint-cli2 --fix --config lesson.markdownlint-cli2.jsonc",
    "fix:project": "markdownlint-cli2 --fix --config project.markdownlint-cli2.jsonc"
  },
  "license": "CC BY-NC-SA 4.0",
  "devDependencies": {
    "markdownlint-cli2": "^0.12.1"
  }
}
```

# Downloading and installing packages locally

You can [install](https://docs.npmjs.com/cli-documentation/install) a package locally if you want to depend on the package from your own module, using something like Node.js `require`. This is `npm install`'s default behavior.

**Note:** If there is no `package.json` file in the local directory, the latest version of the package is installed.

If there is a `package.json` file, npm installs the latest version that satisfies the [semver rule](https://docs.npmjs.com/about-semantic-versioning) declared in `package.json`.

## [Installing a scoped public package](https://docs.npmjs.com/downloading-and-installing-packages-locally#installing-a-scoped-public-package)

[Scoped public packages](https://docs.npmjs.com/about-scopes) can be downloaded and installed by anyone, as long as the scope name is referenced during installation:

`npm install @scope/package-name`

## [Testing package installation](https://docs.npmjs.com/downloading-and-installing-packages-locally#testing-package-installation)

To confirm that `npm install` worked correctly, in your module directory, check that a `node_modules` directory exists and that it contains a directory for the package(s) you installed:

`ls node_modules`