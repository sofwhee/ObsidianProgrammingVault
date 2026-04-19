REST in rails code...
get "/posts",           to: "posts#index"
get "/posts/:id",       to: "posts#show"
get "/posts/new",       to: "posts#new"
post "/posts",          to: "posts#create" (form)
get "/posts/:id/edit",  to: "posts#edit"
put "/posts/:id",       to: "posts#update" (form)
delete "/posts/:id",    to: "posts#destroy"

Each of these routes is basically a Ruby method that matches that particular URL and HTTP verb with the correct controller action. Two things to notice:

The first key thing to notice is that several of those routes submit to the SAME URL… they just use different HTTP verbs, so Rails can send them to a different controller action. That trips up a lot of beginners.

The other thing to notice is...
"/posts/:id/edit"
...the “id” field is prepended by a colon… 
“Look for anything here and save it as the ID in the params hash"

That lets you submit a GET request for the first post and the fifth post to the same route, just a different ID:
  /posts/1  # going to the #show action of the PostsController
  /posts/5  # also going to the #show action of PostsController
It works exactly as you would expect it to!

--- The Rails way to write RESTful routes ---
...index show new create edit update destroy...

Rails knows you want to use those seven actions all the time… so they came up with a handy helper method which lets you do in one line what we just wrote in seven lines in our resources file:

(in config/routes.rb)
  resources :posts

That’s it. That is a Ruby method which basically just outputs those seven routes we talked about before. No magic. You see it a whole lot, now you know what it does.

-- My paraphrase --
"resources :posts"
there are basically seven main types of actions that you can (and should) do to a “resource”, or an object like a blog post or user… something with its own database model.

This basically creates 7 URLS for posts corresponding to each action. 
(...souljourney.com/posts/new) 
(...souljourney.com/posts/:id/edit)

If you don't need all seven...
  "resources :posts, only: [:index, :show]"
  "resources :users, except: [:index]"

And non-RESTful routes...
  get '/somepath', to: 'somecontroller#someaction'


--- breakdown of REST if you forgot --
REST in Rails
index -   GET all the posts
show -    GET just one specific post
new -     GET the page that lets you create a new post
create -  POST the data you just filled out for a new post back to the server so it can create that post

edit -    GET the page that lets you edit an existing post
update -  PUT the data you just filled out to edit the post back to the server so it can actually perform the update

destroy - DELETE one specific post by sending a delete request to the server