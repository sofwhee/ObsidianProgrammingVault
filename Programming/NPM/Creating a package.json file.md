You can create a `package.json` file by running a CLI questionnaire or creating a default `package.json` file.

To create a `package.json` file with values that you supply, use the `npm init` command.

1. On the command line, navigate to the root directory of your package.
    `cd /path/to/package`
2. Run the following command:
    `npm init`
3. Answer the questions in the command line questionnaire.

## Creating a default `package.json` file

### Default values extracted from the current directory

- `name`: the current directory name
- `version`: always `1.0.0`
- `description`: info about the package, or an empty string `""`
- `scripts`: by default creates an empty `test` script
- `keywords`: empty
- `author`: empty
- `license`: [`ISC`](https://opensource.org/licenses/ISC)
- `bugs`: information from the current directory, if present
- `homepage`: information from the current directory, if present

To create a default `package.json` using information extracted from the current directory, use the `npm init` command with the `--yes` or `-y` flag. For a list of default values, see "[Default values extracted from the current directory](https://docs.npmjs.com/creating-a-package-json-file#default-values-extracted-from-the-current-directory)".

1. On the command line, navigate to the root directory of your package.
    `cd /path/to/package`
2. Run the following command:
    `npm init --yes`

```
> npm init --yes

Wrote to /home/monatheoctocat/my_package/package.json:
```

```javascript
{
  "name": "my_package",
  "description": "make your package easier to find on the npm website",
  "version": "1.0.0",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/monatheoctocat/my_package.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/monatheoctocat/my_package/issues"
  },
  "homepage": "https://github.com/monatheoctocat/my_package"
}
```
### [Customizing the `package.json` questionnaire](https://docs.npmjs.com/creating-a-package-json-file#customizing-the-packagejson-questionnaire)

If you expect to create many `package.json` files, you can customize the questions asked and fields created during the `init` process so all the `package.json` files contain a standard set of information.

1. In your home directory, create a file called `.npm-init.js`.
2. To add custom questions, using a text editor, add questions with the `prompt` function:
    `module.exports = prompt("what's your favorite flavor of ice cream, buddy?", "I LIKE THEM ALL");`
3. To add custom fields, using a text editor, add desired fields to the `.npm-init.js` file:
```javascript
    module.exports = {
      customField: 'Example custom field',
      otherCustomField: 'This example field is really cool'
    }
```

To learn more about creating advanced `npm init` customizations, see the [init-package-json GitHub repository](https://github.com/npm/init-package-json).

## [`package.json` fields](https://docs.npmjs.com/creating-a-package-json-file#packagejson-fields)

### [Required `name` and `version` fields](https://docs.npmjs.com/creating-a-package-json-file#required-name-and-version-fields)

The `"name"` field contains your package's name and _must_ be lowercase _without_ any spaces. May contain _hyphens_, _dots_, and _underscores_.

The `"version"` field must be in the form `x.x.x` and follow the [semantic versioning guidelines](https://docs.npmjs.com/about-semantic-versioning).

### [Author field](https://docs.npmjs.com/creating-a-package-json-file#author-field)

If you want inclusive package author information, in the `"author"` field use the following format (email and website are both optional):

`Your Name <email@example.com> (https://example.com)`

## Example

```javascript
{
  "name": "my-awesome-package",
  "version": "1.0.0",
  "author": "Your Name <email@example.com> (https://example.com)"
}
```

