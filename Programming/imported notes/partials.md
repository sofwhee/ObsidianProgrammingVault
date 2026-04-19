Helps organize your code.

Break down your view file into different files so it's easier to read and work on.

call a partial:
 # app/views/users/new.html.erb
  <div class="new-user-form">
    <%= render "user_form" %>
  </div>

Sometimes it makes sense to share partials across multiple view templates that are in multiple controllers, so you save them in their own folder called app/views/shared and would then render them using the code 
  <%= render "shared/some_partial"%>

--- send vars to partial ---
    <%= render partial: "shared/your_partial", :locals => { :user => user } %>
(or <%= render "shared/your_partial", :user => user %> )
Then, inside partial...
  @user (to call it) 

--- implicit partials ---
A reusable partial.

  # app/views/index.html.erb
  <h1>Users</h1>
  <ul>
    <% @users.each do |user| %>
      <%= render "user", :locals => {:user => user} %>
    <% end %>
  </ul>
And in the partial...
  # app/views/_user.html.erb
  <li><%= "#{user.first_name} #{user.last_name}, #{user.email}" %></li>

Or, instead...

  # app/views/index.html.erb
  <h1>Users</h1>
  <ul>
    <% @users.each do |user| %>
      <%= render user %>     <!-- Lots less code -->
    <% end %>
  </ul>

Or...
  # app/views/index.html.erb
  <h1>Users</h1>
  <ul>
    <%= render @users %>
  </ul>

In that situation, Rails not only finds the _user.html.erb file and passes it the correct user variable to use, it also loops over all the users in your @user collection for you.