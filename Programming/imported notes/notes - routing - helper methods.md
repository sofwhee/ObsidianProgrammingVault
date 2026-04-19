Helper methods.

Basically, they're how you avoid hardcoding in URLS in your application. (You never wanna hardcode URLs ok?)

Helper methods basically just generate URLs for you, whether the whole URL or just a portion of it. If your URL changes for any reason, you don't have to manually retype it everywhere in your code since it's being generated automatically.

They end in "_path" or "_url".
"path" -> path portion of URL
"url"  -> whole URL enchilada

  edit_post_path(3) ---> /posts/3/edit

You can also feed pipe in parameters with a colon. Like so...

  post_path(3, :referral_link => "/some/path/or/something")


--- Examples ---
Creating
  resources :photos
will expose a number of helpers to your Photos controller!

  photos_path           returns /photos
  new_photo_path        returns /photos/new
  edit_photo_path(:id)  returns /photos/:id/edit 
  photo_path(:id)       returns /photos/:id

Each of these helpers has a corresponding _url helper (such as photos_url) which returns the same path prefixed with the current host, port, and path prefix.

You can make multiple.
  resources :photos, :books, :videos