**Pros**
- Helps with downloading a large number of module files.
- Helps process and optimize code

**Cons**
- Need to configure a bundler.

Order of operations with bundlers:
1. Provide the bundler an entry point
2. Bundler builds a dependency graph from that file
3. Bundler combines all relevant files together
4. Bundler output a single file with all the necessary code included

Optional things we could make it do:
- minifying code
- optimize images
- [“tree shaking”](https://developer.mozilla.org/en-US/docs/Glossary/Tree_shaking)

When dealing with bundlers, you have two dirs. A `src` (source) and `dist` (distribution).

`src`
- Keeps all website's source code
- Where all work will be done
- Exception: altering config files in project root
`dist`
- Webpack's output destination
- When you run Webpack, it puts bundled files here

The point is that if someone were to fork/clone the project, they don't need the `dist`. Or you!
Work inside `src`, build into `dist`, deploy from `dist`!