#Devise #Rails #controllers #generator
1. If you want to adjust the controllers, use this generator:
`rails generate devise:controllers [scope]`

`users` scope:
```
class Users::SessionsController < Devise::SessionsController
  # GET /resource/sign_in
  # def new
  #   super
  # end
end
```

2. Tell the router to use this controller:
`devise_for :users, controllers: { sessions: "users/sessions" }`

3. Copy the views from `devise/sessions` to `users/sessions`. Since the controller was changed, it won't use the default views located in `devise/sessions`.

4. Done.