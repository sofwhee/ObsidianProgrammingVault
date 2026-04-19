To start Rails saying "Hello", you need to create at minimum a route, a controller with an action, and a view. 

A route maps a request to a controller action.
In other words, a route is what determines what starts 
when you enter a url like "http.../articles". 
It's a pointer. (points to a particular director)

A controller action performs the necessary work to handle the request, and prepares any data for the view.
In other words, this is the director, telling staff to
get in position and calling "action!".
It's the director.

A view displays data in a desired format.
This is the screen.

A model is a Ruby class that is used to represent data. Additionally, models can interact with the application's database through a feature of Rails called Active Record.
These are the pages. (for the actors)

---
model generator example:
"bin/rails generate model Article title:string body:text"
---
