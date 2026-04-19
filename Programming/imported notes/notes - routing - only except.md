only: and except: do exactly what you think they do.

all routes:
  index
  show
  new
  create
  edit
  update
  destroy

only create index and show...
  resources :photos, only: [:index, :show]
  
create all except destroy...
  resources :photos, except: :destroy

