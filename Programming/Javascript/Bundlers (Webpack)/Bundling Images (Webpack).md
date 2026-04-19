## Exceptions

(If your project does not have images with local file path sources in your HTML template, you do not need `html-loader` set up. If you aren’t using any local images in your JavaScript, you won’t need the image `asset/resource` rule set up.)

(You may end up working with things that need a special loader or plugin, such as custom fonts or preprocessors. You can always use Google or reference Webpack’s documentation for instructions on what you’d need when that time comes.)

## Guide

There are three different ways you could be dealing with local image files:

#### Image files used in our CSS inside `url()`
`css-loader` already handles this for us, so there’s nothing extra to do.

#### Image files we reference in our HTML template, e.g. as the `src` of an `<img>`

We need to install and tell Webpack to use something called `html-loader`, which will detect image file paths in our HTML template and load the right image files for us. 

Without this, `./odin.png` would just be a bit of text that will no longer reference the correct file once we run Webpack to build into `dist`. 

Let’s install it, then add the following object to the `modules.rules` array within `webpack.config.js`

```bash
npm install --save-dev html-loader
```

```javascript
{
  test: /\.html$/i,
  loader: "html-loader",
}
```

#### Images we use in our JavaScript, where we will need to import the files

If we need to use a local image file in our JavaScript (such as when manipulating the DOM to create or edit `img` elements and set their `src` attribute), we need to import the images into our JavaScript module.

Since images aren’t JavaScript, we need to tell Webpack that these files will be assets by adding an `asset/resource` rule.

No need to install anything here. Just add the following object to the `modules.rules` array within `webpack.config.js`:

```javascript
{
  test: /\.(png|svg|jpg|jpeg|gif)$/i,
  type: "asset/resource",
}
```

You can always edit the regex in the `test` property to remove any file extensions you don’t need or add any extensions you do need. What’s shown above is straight from [Webpack’s Asset Management guide](https://webpack.js.org/guides/asset-management/#loading-images) and will recognize most of the common image file extensions.

Then, in whatever JavaScript module we want to use that image in, we just have to default import it.

```javascript
import odinImage from "./odin.png";
   
const image = document.createElement("img");
image.src = odinImage;
   
document.body.appendChild(image);
```

We have to import it so that the `odinImage` variable contains the correct file path, even when we bundle into `dist`. 

If we just wrote `image.src = "./odin.png";`, then the “file path” would just be a plain string. 

When we bundle into `dist`, Webpack will not magically recognize that this string in our JavaScript references a file and so will not include it in the bundle. 

When we import it and set the correct `asset/resource` rule, Webpack will recognize the import, include the image file when we bundle, and also make sure the imported variable contains the correct file path at the end.

#### After all that...

If we added both `html-loader` and the image `asset/resource` rule, our `webpack.config.js` would look something like this:

```javascript
// webpack.config.js
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    filename: "main.js",
    path: path.resolve(__dirname, "dist"),
    clean: true,
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/template.html",
    }),
  ],
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.html$/i,
        loader: "html-loader",
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: "asset/resource",
      },
    ],
  },
};
```

You might notice that when images are included when bundling, the output image file in `dist` has a different file name (it will likely be some jumble of numbers and letters).

By default, Webpack gives your bundled image files a new name by hashing their contents.

You do not need to know how this works, nor do you need to dig into the details of why, nor how to change it.

 You just need to be aware that this is expected behavior (it’s to do with preventing issues with the browser cache and matching file names).