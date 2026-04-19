The official recommended gem is [dartsass-rails](https://github.com/rails/dartsass-rails). It's a wrapper around the sass utility written in Dart. dartsass-rails is maintained by the Rails organisation.

It requires running a separate process to convert SASS into CSS. In development, this is done by running a watch process in addition to the Rails server. In production, the build process is automatically attached to assets:precompile.

Add the gem to your Gemfile and install it:

`./bin/bundle add dartsass-rails`
  

Then run the installer:

`./bin/rails dartsass:install`
  

That installs the foreman gem and creates a Procfile.dev file which contains this:

`web: bin/rails server -p 3000`
`css: bin/rails dartsass:watch`
  

foreman runs those two processes - the Rails server and dartsass for processing .scss files. It's run in watch mode, so any changes to the .scss files are picked up immediately and processed automatically.

The output CSS files are stored in app/assets/builds/, which is also linked to from the manifest.js file.

A new file app/assets/stylesheets/application.scss is created, where you can write your SASS code.

By default, this gem only builds application.scss. If you want to change or add to this, you need to modify Rails.application.config.dartsass.builds. For example:

Rails.application.config.dartsass.builds = {
  "app/index.sass"  => "app.css",
  "site.scss"       => "site.css"
}
  

When you run bin/dev, it starts the Rails server and dartsass:watch:

$ bin/dev
07:06:36 web.1  | started with pid 39159
07:06:36 css.1  | started with pid 39160
07:06:38 web.1  | => Booting Puma
07:06:38 web.1  | => Rails 7.1.3 application starting in development 
07:06:39 css.1  | Sass is watching for changes. Press Ctrl-C to stop.
07:06:39 css.1  | 
  

When you make a change to application.scss and save it, you'll see a compilation confirmation in the logs:

07:10:17 css.1  | [2024-02-01 07:10:17] Compiled app/assets/stylesheets/application.scss to app/assets/builds/application.css.