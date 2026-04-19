The most important route in your file is the root URL… where should users be deposited when they land on http://supercutekittenphotos.com? Just tell Rails which controller and action to map that route to, and it is so:

  root to: "kittens#index"  #kittens controller, index action (method)

Remember, when we say “action” we really mean “the method inside the controller that is called that”, e.g. the index action is just the index method that’s defined in the KittensController*

--- my paraphrase ---
it's like doing this in python:

kittens(class) .index(method in kittens)
root to: "kittens#index" is calling the index method.
---