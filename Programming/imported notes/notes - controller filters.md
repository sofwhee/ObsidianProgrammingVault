Controller filters
- run some code in controller at specific times
- (ie before any other code has been run)
- Useful for "filtering out" unauthorized stuff (!!!!)

--- Before filter ---
  before_action :require_login
  before_action :do_something_cool

  private (so they can only be used by controller)

  def require_login
    if current_user.logged_in?
      # allow user to perform action
    else
      redirect_to login_path
    end
  end

  def do_something cool
    # do stuff here
  end

-- other stuff --
  before_action :require_login, only: [:edit, :update]
    or
  before_action :require_login, except: [:edit, :update]

Filters are inherited.
If you'd like a filter to apply to every controller action,
put it in app/controllers/application_controller.rb
