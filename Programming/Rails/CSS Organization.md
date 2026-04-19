The asset pipeline in [Ruby on Rails](https://railsware.com/blog/ruby-on-rails-guide/) is a very powerful, but somewhat confusing feature. By default, Rails scaffold generates a stylesheet per controller so that your styles were organized according to your application’s domain model. Which is not really convenient when you are building a modular codebase and reusable components. We need to come up with some custom CSS architecture that will allow us easily create, modify and reuse elements.

The asset pipeline basically performs the following: precompiles, concatenates, minifies assets and places them in the public/assets folder. The asset pipeline is powered by the two technologies: [Sprockets](https://github.com/sstephenson/sprockets) and [Tilt](https://github.com/rtomayko/tilt).

**Tilt** is the template engine that is used by Sprockets. It allows file types like sass, erb, coffee, etc. to be used in the asset pipeline.

**Sprockets** itself performs the asset packaging, i.e. takes the assets from all the specified paths, compiles them together and places them in the public/assets folder.  
How does Sprockets know which files to concatenate and in which order? Here comes a keystone of the asset pipeline – a manifest file. It uses directives to declare the files to be included and an order of inclusion. You can have as many manifest files as you need – one per layout or one pre page, that’s entirely your choice.

## CSS Preprocessing

Asset pipeline makes it easy to use any CSS preprocessors like [LESS](http://lesscss.org/), [SASS](http://sass-lang.com/) or [Sylus](http://learnboost.github.io/stylus/). We usually work with SASS because it’s awesome and it comes with a Rails app from the start.

Every CSS preprocessor allows you to use functions, variables, mixins and other useful stuff that is shared across all modules and files. But in order to use them, SASS source code should be first combined and then compiled to CSS.

In this case, there is an issue with using Sprockets _//=require_ syntax to specify which files should be combined together. Sprockets compiles your Sass source code first as independent stylesheets, and then merges the resulting CSS into a single file. That’s why you need to import your mixins.sass at the top of each file, otherwise you’ll see an exception if you try to use any mixin. By using the _@import_ syntax, you are instructing the Sass compiler to combine the Sass source code first, and then perform the compilation.

## File organization

In most Rails projects, there are several layouts that have different styles, but there’s still common codebase that should be shared. So, here are some guidelines on how to organize you assets files and directories, so that they were easily extendable and had a flexible and well defined structure.

**Base styles.**  
All base styles that will never be changed – i.e. reset, grids, spaces and helpers – go to the base folder and are added to every manifest.

**Manifests files per layout.**  
First of all, you should create one manifest file per layout (if these layouts have different styles). By manifest I mean not sprockets manifest, but .sass file with all @imports of necessary files (variables, mixins, objects and modules).

  // Base styles
  @import "base/mixins"
  @import "base/reset"
  @import "base/grids"
  @import "base/spaces"
  @import "base/helper"

  // Layout specific styles
  @import "application/typography"
  @import "application/layout"

  // Objects
  @import "application/objects/buttons"
  @import "application/objects/inputs"
  .......................

  // Modules
  @import "application/modules/profile"
  @import "application/modules/dashboard"
  .......................

**Folder for each manifest.**  
There should be one folder for each manifest file with the same name. _application_ folder for _application.sass_ file as a default layout. This folder will contain layout styles, typography, all objects and modules that are used in this particular layout.

stylesheets
  ├── base
  │   ├── mixins.sass
  │   ├── reset.sass
  │   ├── grids.sass
  │   ├── spaces.sass
  │   └── helpers.scss
  ├── application.sass
  ├── application
  │   ├── layout.sass
  │   ├── typography.sass
  │   ├── objects
  │   |   ├── buttons.sass
  │   |   ├── inputs.sass
  |   |   └── ..........
  │   ├── modules
  │   |   ├── profile.sass
  │   |   ├── dashboard.sass
  |   |   └── ..........
  │   └── responsive
  │       ├── tablet.sass
  │       ├── mobile.sass
  |       └── ..........
  └── shared
      ├── popup.sass
      ├── markdown.sass
      └── ..........

Inside every manifest folder you can put responsive styles under _responsive_ folder, divide your interface into objects and modules and put them inside the proper folder. This keeps your styles independent and modular. If you need to reuse some styles of different manifest folder – move them to a shared folder that is located on the same level as manifests.