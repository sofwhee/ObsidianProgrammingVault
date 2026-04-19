http://localhost:3000/rails/info/routes
OR
bin/rails routes

Complete list of all available routes!

Try --expanded for this format:
$ bin/rails routes --expanded

--[ Route 1 ]----------------------------------------------------
Prefix            | users
Verb              | GET
URI               | /users(.:format)
Controller#Action | users#index
--[ Route 2 ]----------------------------------------------------
Prefix            |
Verb              | POST
URI               | /users(.:format)
Controller#Action | users#create
--[ Route 3 ]----------------------------------------------------
Prefix            | new_user
Verb              | GET
URI               | /users/new(.:format)
Controller#Action | users#new
--[ Route 4 ]----------------------------------------------------
Prefix            | edit_user
Verb              | GET
URI               | /users/:id/edit(.:format)
Controller#Action | users#edit