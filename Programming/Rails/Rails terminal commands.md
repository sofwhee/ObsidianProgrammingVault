
`rails new app-name` this command will create a new app.
`rails new app-name -d postgresql` specify postgresql as the database of the app.
`rails new app-name –api` creates only API application.

`rails s` which is short for `rails server` will run the server and open [http://localhost:3000](http://localhost:3000/)

## Rails Generator commands

`rails generate -h` gives full list of commands.
`rails g model | more`   will show how to use the generator on the model or controller or task etc.

`rails g scaffold book name price:decimal` makes scaffold.

`rails g model ModelName column_name:datatype column_name2:datatype2` generates a model. 

### Controller Generator

`rails g controller ControllerName action1 action2`

### Migration Generator for adding columns

`rails g migration add_name_of_column_to_table_name name_of_column:datatype`

### Migration Generator for Removing columns

`rails g migration remove_column_name_from_table_name name_of_column:datatype`

#####  Remember to run `rails db:migrate` after all of these commands

[Here](https://learn.co/lessons/rails-generators-readme) is a more in-depth discussion of what files each of these generators create, and when they are the most useful.

4- Opening Rails console

### rails console` or `rails c`

The command let us interact with the application from the command line.  
the rails console uses IRB.  
This is very useful for testing out quick ideas with code and changing data server-side without touching the website.

## 5- Rails destroy command

`rails destroy` or `rails d` command is the opposite of generate.  
It'll figure out what generate did, and undo it.  
for example this command `rails g model ModelName` will generate the model and to destroy this model all we do is `rails d model ModelName`

## 6- Rails about command

`rails about` command will give us all the information we need about the current application as Ruby, RubyGems, Rails, the subcomponents, application's folder, the current environment name, Middleware, app's database adapter, and schema version.

## 7- Rails db commands

`rails db` we use this command to create, reset, drop, run the migration and more, checkout the migrations guide [Here](https://guides.rubyonrails.org/active_record_migrations.html)

## 8- Displaying all Rails routes

`rails routes` command will list all of your defined routes in a nicely organized way, and that is really useful for tracking down routing problems in the application, or giving you a good overview of the URLs in an app you're trying to get familiar with.

## 9- Running Rails test

As we know Rails comes with a test framework called minitest. The `rails test` will run the different tests in the app.

## 10- bundle update

`bundle update` command will update all of your Gems to match the Gemfile, If you modify the Gemfile in a project in order to include new or different Ruby Gems.

The Rails Command Line [Guide](https://guides.rubyonrails.org/command_line.html#rails-generate)