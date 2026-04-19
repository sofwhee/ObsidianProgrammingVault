#Rails 

Form blueprint for Rails.

<%= form_with model: @users do |form| %>
  <%= form.label :username, "Username:" %>
  <%= form.text_field :username %><br><br>
  <%= form.label :password, "Password:" %>
  <%= form.password_field :password %><br><br>
  <%= form.label :email, "Email:" %>
  <%= form.email_field :email %><br><br>
  <%= form.submit %>
<% end %>

