
email

	- Actionmailer gem. (Rails is made of 7 core gems, this is one of them)
	- mailer = model + controller combined (data structure + actions)
	- controller actions = Welcome, Followup, Thanks For Purchase...
	- Email itself -> just a view (app/views/[mailer_subfolder])
	- mailer views have two formats: HTML and text. (helps bypass SPAM filters)

set up view (views/mailer/welcome_email.html.erb + ...text.erb)
variables_in_mailer -> mailer_view (erb/haml)

first, build email itself
then, call #deliver_now to send it

UserMailer.welcome_email(@user)		     => (email object)
UserMailer.welcome_email(@user).deliver_now => delivers email object! simple.

Make sure to name view files (HTML/text) same as mailer methods. Rails won't work otherwise.

Callback?
(just like a normal controller, callbacks can be used in Mailers. I guess it's stuff like "before_action".)

after_action 
	- A "callback". Allows you to modify parts of the email if you need to, with access to instance variables of the mail instance (so you can use @user for example). It runs after email is *generated*, not after it is *sent*.

Providers: SendGrid (Heroku), free up until a certain usage tier. MailGun, Mailchimp, Postmark.

Testing:

- Letter Opener gem.
 (place in development group of Gemfile. Just switch a config setting in config/environments/development.rb file. Will take your emails and display them in the web browser for you instead of sending.)

Production

- If you're sending a whole bunch of them, don't make main application do it. Anyone trying to access it will be shut out.
- Full URLS for links in mailer, no _url or _path helper methods. (user will be opening email at an external source)
- config/environments/production.rb, specify website's host name. (config.action_mailer.default_url_options = { :host => 'yourapp.com }. If it isn't set, you may get a host error message or strange looking links.
- Email html can't use stylesheets, you do it inline or using <style> tags.
- Attaching images to emails is hard...

---

Mailers summary:

Form
- app/mailers
- #Actions connected to Views (app/views)
- layouts + partials
- can access a "params hash"

Walkthrough

Create the Mailer
	bin/rails generate mailer User
Add a method 
	(app/mailers/user_mailer.rb)

	class UserMailer < ApplicationMailer
	  default from: 'notifications@example.com'  
	   (#sets default values for all emails sent from this mailer. This is setting the ":from" header value for all messages in this 	    class. You can also do this on a per-email basis)

	  def welcome_email
	    (#set params to be used in email)
	    
	    @user = params[:user]
	    @url  = 'http://example.com/login'

	    mail(to: @user.email, subject: 'Welcome to My Awesome Site')
	     (#mail method creates the actual email message. We use it to specify the values of headers like ":to" ":subject")
	  end
	end
Create a Mailer view
	(This will allow mail method to detect the two templates and automatically generate a "multipart/alternative" type email)

	(app/views/user_mailer/welcome_email.html.erb)
	
	<!DOCTYPE html>
	<html>
	  <head>
	    <meta content='text/html; charset=UTF-8' http-equiv='Content-Type' />
	  </head>
	  <body>
	    <h1>Welcome to example.com, <%= @user.name %></h1>
	    <p>
	      You have successfully signed up to example.com,
	      your username is: <%= @user.login %>.<br>
	    </p>
	    <p>
	      To login to the site, just follow this link: <%= @url %>.
	    </p>
	    <p>Thanks for joining and have a great day!</p>
	  </body>
	</html>


	(app/views/user_mailer/welcome_email.text.erb)

	Welcome to example.com, <%= @user.name %>
	===============================================

	You have successfully signed up to example.com,
	your username is: <%= @user.login %>.

	To login to the site, just follow this link: <%= @url %>.

	Thanks for joining and have a great day!
Call the Mailer
	(As an example, imagine sending an email to a new user upon creation)
	(UserMailer.with(user: @user).welcome_email.deliver_later)
	  (".with" => with(user: @user, account: @user.account) => makes params[:user] and params[:account])
	  (".weekly_summary" returns ActionMailer::MessageDelivery object, which is a wrapper around a Mail::Message)
	  ("deliver_later" => controller doesn't have to wait for send to complete)
	  (deliver_later only makes sense in dev/test envs. For persistent backend in prod, use Sidekiq, Resque, etc)

	class UsersController < ApplicationController
	  # ...

	  # POST /users or /users.json
	  def create
	    @user = User.new(user_params)

	    respond_to do |format|
	      if @user.save
	        # Tell the UserMailer to send a welcome email after save
	        UserMailer.with(user: @user).welcome_email.deliver_later
	
	        format.html { redirect_to(@user, notice: 'User was successfully created.') }
	        format.json { render json: @user, status: :created, location: @user }
	      else
	        format.html { render action: 'new' }
	        format.json { render json: @user.errors, status: :unprocessable_entity }
	      end
	    end
	  end

	  # ...
	end
End of Walkthrough

Action Mailer Methods
- mail
	Create an email - either plain text or multipart - depending on what email templates were defined. 
	Pass headers to it as a hash.
- headers
	Specifies any header on email. Pass a hash of header field names and value pairs. Or "headers[:field_name] = value"
- attachments
	attachments['file-name.jpg'] = File.read('file-name.jpg)
- attachments.inline
	mailer controller:
	
	def welcome
	    attachments.inline['image.jpg] = File.read('/path/to/image.jpg')
	end

	mailer view:
	
	<p>Hi, this is our image</p>
	
	<%= image_tag attachemnts['image.jpg'].url, alt: 'My Photo', class: 'photos' %>
- layout
	class UserMailer < ApplicationMailer
	  layout 'awesome' # use awesome.(html|text).erb as the layout
	end
- format-exclusive layouts
	class UserMailer < ApplicationMailer
	  def welcome_email
	    mail(to: params[:user].email) do |format|
	      format.html { render layout: 'my_layout' }
	      format.text
	    end
	  end
	end

Preview Emails
	(test/mailers/previews/user_mailer_preview.rb)
	(To see the preview of welcome_email, implement a method that has the same name and call UserMailer.welcome_email)
	(Then the preview will be available in http://localhost:3000/rails/mailers/user_mailer/welcome_email.)
	(A list of previews are also available in http://localhost:3000/rails/mailers.)

	class UserMailerPreview < ActionMailer::Preview
	  def welcome_email
	    UserMailer.with(user: User.first).welcome_email
	  end
	end

  If you don't set :host globally, you'll have to specify the host any time you try to generate an url.

Set :host globally in config/application.rb
    config.action_mailer.default_url_options = { host: 'example.com' }

Because of this behavior, you cannot use any of the _path helpers inside of an email. Instead, you will need to use the associated_url helper.

    <%= link_to 'welcome', welcome_path %> (doesn't work)
    <%= link_to 'welcome', welcome_url %>    (works)

To add an image in an Action Mailer View, you'll have to provide the :asset_host parameter yourself. You can set it globally in config/application.rb
    config.action_mailer.asset_host = 'http://example.com/'

As the :asset_host usually is consistent across the application you can configure it globally in config/application.rb:
Sofi — Today at 11:56 AM
Send with Gmail

    config/environments/$RAILS.ENV.rb

config.action_mailer.delivery_method = :smtp
config.action_mailer.smtp_settings = {
  address:         'smtp.gmail.com',
  port:            587,
  domain:          'example.com',
  user_name:       '<username>',
  password:        '<password>',
  authentication:  'plain',
  enable_starttls: true,
  open_timeout:    5,
  read_timeout:    5 }

*Google blocks sign-ins from apps it deems less secure. You can change your Gmail settings here (https://www.google.com/settings/security/lesssecureapps) to allow the attempts. If your Gmail account has 2-factor authentication enabled, then you will need to set an app password(https://myaccount.google.com/apppasswords) and use that instead of your regular password.