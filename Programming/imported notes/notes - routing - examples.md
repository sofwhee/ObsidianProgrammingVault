Examples for how to generate paths and URLs:

For a URL/path that goes like
"www.hospital.com/patients/12"
Your router (config/routes.rb) will need something like...

route: (in config folder)
  get '/patients/:id', to: 'patients#show', as: 'patient'
  (if the URL contains this...)
  (run the method 'show' in Patients class AKA controller)
controller:
  @patient = Patient.find(params[:id])
  (define variable patient as...)
  (return Patient with this id)
view:
  <%= link_to "Patient Record', patient_path(@patient) %>
  (Helper Generate a link to...)
  <><>Patient Record??? Generate a URL maybe??<><>
  (Helper Generate path "/patient/12")

Summary:
  This generates all the text for you!


--- Syntax ---
get 'string', to: 'users#show' ==
get 'string', action: :show, controller: 'users'

--- Resourceful route ---
resource :geocoder
resolve('Geocoder') { [:geocoder] }

Creates six different routes mapped to Geocoders controller...

GET	      /geocoder/new	  geocoders#new
POST	    /geocoder	      geocoders#create
GET	      /geocoder	      geocoders#show
GET	      /geocoder/edit	geocoders#edit
PATCH/PUT	/geocoder	      geocoders#update
DELETE	  /geocoder	      geocoders#destroy