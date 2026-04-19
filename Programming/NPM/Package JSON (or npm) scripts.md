Package JSON scripts, often referred to as npm scripts, are custom commands defined in the package.json file of a [Node.js](https://www.upgrad.com/blog/node-js-tutorial-learn-node-js-from-scratch/) project.

These scripts automate terminal commands, making it easier to perform repetitive or complex tasks with simple keywords.

Resources: https://www.upgrad.com/blog/introduction-to-package-json-scripts-in-node-js/

If you don't wanna write long commands like `git subtree push --prefix dist origin gh-pages`
you can use scripts!

```json
{
  // ... other package.json stuff
  "scripts": {
    "build": "webpack",
    "dev": "webpack serve",
    "deploy": "git subtree push --prefix dist origin gh-pages"
  },
  // ... other package.json stuff
}
```

Now you write `npm run deploy`, `npm run build`, `npm run dev`...

# Use Cases

Here are some common tasks that can be automated using package JSON scripts in Node.js or npm scripts:

- **Running a linter**: Check your code for errors or enforce coding standards.
- **Starting a development server**: Launch your application in a local environment.
- **Minifying** [**JavaScript**](https://www.upgrad.com/tutorials/software-engineering/javascript-tutorial/) **or** [**CSS**](https://www.upgrad.com/blog/css-tutorial-learn-css-from-scratch/): Optimize assets for production.
- **Running tests**: Execute unit or integration tests.
- **Building a project**: Compile code from modern JavaScript (e.g., ES6+) to older versions.
- **Cleaning up builds**: Remove temporary or old files.

**Common Scripts**

- **start**: Launches the server or application.
- **test**: Executes test cases for your project.
- **build**: Compiles and prepares production-ready code.
- **dev**: Starts a development server with live reload or debugging.
- **lint**: Enforces code style guidelines by running a linter.

**Additional Scripts**:

- **clean**: Removes build artifacts or temporary files.
- **deploy**: Deploys the application to a server or cloud.