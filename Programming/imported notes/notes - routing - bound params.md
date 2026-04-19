  get 'photos(/:id), to: 'photos#display'

The () around '/:id' mean that this is an optional parameter.

This makes whatever is put into :id (say, "1") available as
params[:id].

The 'display' method within class PhotosController will have that available to use!

--- dynamic segments ---

  get 'photos/:id/:user_id', to: 'photos#show'

params[:id] = "1" , params[:user_id] = "2"

(By default, dynamic segments don't accept dots - this is because the dot is used as a separator for formatted routes. If you need to use a dot within a dynamic segment, add a constraint that overrides this – for example, 
  id: /[^\/]+/ 
allows anything except a slash.)

--- static segments ---

  get 'photos/:id/with_user/:user_id', to: 'photos#show'

The "with_user" (notice the missing colon) makes it static. This responds to paths like "/photos/1/with_user/2" but not "/photos/1/2/3".

In this case, params would be 
  { controller: 'photos', 
    action:     'show', 
    id:         '1', 
    user_id:    '2'       }

--- query string ---

  get 'photos/:id', to: 'photos#show'

If '/photos/1?user_id=2' is given...

In this case, params would be
  { controller: 'photos',
    action:     'show',
    id:         '1',
    user_id:    '2'      }