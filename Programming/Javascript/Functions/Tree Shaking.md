_Tree shaking_ is a term commonly used in the JavaScript context for dead-code elimination.

You can imagine your application as a tree. The source code and libraries you actually use represent the green, living leaves of the tree. Dead code represents the brown, dead leaves of the tree that are consumed by autumn. In order to get rid of the dead leaves, you have to shake the tree, causing them to fall.

First, you mark files to be kept and removed.
Then, you use `import` and `export` to drop the cued-up "dead code".

- Use ES2015 module syntax `import` and `export`
- Prevent compilers from transforming ES2015 module syntax into CommonJS modules
- Add a `sideEffects` property to `package.json`
- Config optimizations like minification and tree-shaking in your Production Mode config options
- Make sure your `devtool` isn't using a value that can't be used in Production Mode.
