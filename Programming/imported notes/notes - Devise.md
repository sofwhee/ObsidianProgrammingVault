Devise:
10 modules, prepackages a bunch of signin/signup forms 
with methods to help implement them.

to start with devise on a project:
  bundle add devise
  rails generate devise:install
  config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
(change host to actual host in production)

  rails generate devise MODEL (User or Admin or whatever)
(will create controller, model, and configure it
 with default Devise modules. Also will route index with it)
  
  rails db:migrate

-- Controller filters and helpers --
(if Devise model is "Member", it'll be "member_signed_in?" etc)

  before_action :authenticate_user!
(sets up a controller with user authentication)

  user_signed_in?
(verifies a user is signed in)

  current_user
(gives current user)

  user_session
(access session for this scope)

After signing in a user (or other user auth stuff)
Devise will look for a scoped root path (user_root_path)
Otherwise, default root_path.

-- Configuring models --
  devise :database_authenticatable, :registerable, :confirmable, 
         :recoverable, stretches: 13

  (:pepper, :encryptor, :confirm_within, 
   :remember_for, :timeout_in, :unlock_in)

  (see /config/initializers/devise.rb)

-- Strong Parameter Sanitation --
  sign_in (Devise::SessionsController#create)
(Permits only the authentication keys (like email))

  sign_up (Devise::RegistrationsController#create) 
(Permits authentication keys plus password and password_confirmation)

  account_update (Devise::RegistrationsController#update) 
(Permits authentication keys plus password, 
 password_confirmation and current_password)

-- Lazy Way tm --

Use a before action to permit additional params:

  class ApplicationController < ActionController::Base
    before_action :configure_permitted_parameters, if: :devise_controller?

    protected

    def configure_permitted_parameters
      devise_parameter_sanitizer.permit(:sign_up, keys: [:username])
    end
  end

Nested attributes version: (tell Devise about these nesting and types)

  class ApplicationController < ActionController::Base
    before_action :configure_permitted_parameters, if: :devise_controller?

    protected

    def configure_permitted_parameters
      devise_parameter_sanitizer.permit(:sign_up, keys: [:first_name, :last_name, address_attributes: [:country, :state, :city, :area, :postal_code]])
    end
  end

Permit simple scalar values for username and email:

  def configure_permitted_parameters
    devise_parameter_sanitizer.permit(:sign_in) do |user_params|
      user_params.permit(:username, :email)
    end
  end

Permit array for Devise:

  def configure_permitted_parameters
    devise_parameter_sanitizer.permit(:sign_up) do |user_params|
      user_params.permit({ roles: [] }, :email, :password, :password_confirmation)
    end
  end

List of permitted scalars. How to declare permitted keys in nested stuff:
  https://github.com/rails/strong_parameters#nested-parameters


-- View authorization --

If you want to change default Devise views...
  rails generate devise:views
(set config.scoped_views = true in /config/initializers/devise.rb)
(After doing so, you will be able to have views based on the role 
 like users/sessions/new and admins/sessions/new)

-- Hotwire/Turbo --
In order to get Devise to play nicely with Turbo do the following...
  
  Install responders gem
(allows configuring the status used for validation error responses (error_status))
(and for redirects after POST/PUT/PATCH/DELETE requests (redirect_status))

  gem install responders
  bundle install
  rails g responders:install


  data-confirm needs to change to data-turbo-confirm
  data-method to data-turbo-method
If you're setting up Devise to sign out via :delete, and you're using links 
(instead of buttons wrapped in a form) to sign out with the method: :delete option, 
they will need to be updated as described above. 
(Devise does not provide sign out links/buttons in its shared views.)

Make sure to inspect your views looking for those, and change appropriately.

--- normal way ---

1. Start by generating a controller!
    bin/rails generate controller [controller name] <routes i.e. "index">
2. Add a root route
    root "articles#index"
3. Generate a model
    bin/rails generate model Article title:string body:text blah:integer
5. Do validations and such
    class User < ApplicationRecord
      has_many :posts
      has_many :comments

      validates :name, presence: true, uniqueness: true
      validates :password, presence: true, length: { in: 6..20 }
      validates :email, presence: true, uniqueness: true, format: URI::MailTo::EMAIL_REGEXP
    end
6. Migrate database for the models generated
    bin/rails db:migrate
7. Test validations with IRB
    bin/rails console OR bin/rails c

    userthing = User.new(param: "blah blah", param2: 2)
    userthing.valid?
    userthing.create
    User.find(1)
    Users.all
8. Set up error messages for validations
    @article.errors.full_messages_for(:title).each do |message|
    @article.errors.full_messages_for(:title).each do |message|
    (Put these somewhere in your view html)
9. Add private method in controller actions for strong params
    private
      def article_params
        params.require(:article).permit(:title, :body)
      end
10. Do all your logic this way in views and controllers and routes
11. Make partials to make everything more legible and follow DRY



--- Devise way ---

2. set up data?
  1. generate models? 
  (look up if you generate models or controllers first)
  (look up when you do database migration)
  (look up how to do authentication, in case you gotta change your database for it)
  (look up how to do authorization, same reason)
  (rewrite the following model tables to accomodate)
    1. User: username string, password string, email string
    2. Post: user_id integer, title string, body text
  2. set up validations
  (double check what validations are needed for auth/auth)
  3. set up active record dependencies or whatever (has_one, has_many)
  4. complete migration now? or earlier? idk

3. set up routing? (do you do this before or after setting up views?)
  1. "resources:" for user and posts?

4. set up views now?
  1. index view...
  (check if it works automatically)
  (find out...)
  (how to show all posts down the page?)
  (how to add create post button?)
  2. create post view...
  (how to make a form you can type in and submit?)
  (make it so submitting adds to database?)
  (show errors if form wrong?)
  (show success if succesful?)
  (create post view?)
  3. post view
  (check if it works automatically)
  (how to make it show a post?)
  (how to let you edit the post?)
  (how to let you destroy the post?)
  (how to redirect?)
  (redirect create post submit to post view)
  4. edit post view...
  (how to make it so form is autofilled with post info on page load?)
  (so form behaves just like creating post?)
  (submit button edits/updates instead of creates new?)
  5. post view again...
  (add destroy button?)
  (make button destroy from database?) 
  redirect to index

5. make sign up system
  1. How to add sign up button? (create user)
  2. How to create sign up form?
  3. how to validate sign up info?
  4. error messages? success message?
  5. redirect?
  6. how to keep password safe?

6. make signed in system
  1. sign in button?
  2. sign in form?
  3. validate sign in form info?
  4. error messages? success?
  5. redirect?
  6. save signed in state to browser? Cookies? session?
  7. sign out button on index?
  8. how to remove signed in state on browser?

7. make authorized system
  1. how to check if signed in?
  2. how to change info presented if not signed in?
