#Rails 

## syntax

(in layout)
`yield`
`yield :stuff_for_yield`

(in view)
```
<% content_for :stuff_for_yield do %>
	(stuff)
<% end %>
```

(in controller)
```
class CharactersController < ApplicationController
	def index
		render layout: 'layout_name'
	end
end
```