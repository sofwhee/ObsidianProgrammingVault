-- Methods --

.exists? # returns true/false
.any?    # any records match criteria
.many?   # multiple records match criteria

-- Same Arguments --

User.where(email: "foo@bar.com")
User.where("email" => "foo@bar.com")
User.where("email = 'foo@bar.com'")
User.where("email = ?", "foo@bar.com")
User.where("users.email" => "foo@bar.com")

-- Large queries --

Batch into lots of subqueries for efficiency.

.find_each 
  # chunks query into pieces
  # loads first piece, evaluates, then moves on to next...

.where
  # exact value to find
  # range of values to find
  # several values to find
  # returns Relation, so grab record with .first
  # User.where(email: "foo@bar.com").first

.find_by
  # build your own finder method
  # alternative to .where
  # User.find_by(email: 'foo@bar.com')

.select
  # User.select(:id)
  # @users = User.select("users.id AS user_id")
  # (now you can do @users.first.user_id)

-- Aggregations --

Just like with SQL, you often want to group fields together.
(or “roll up” the values under one header)

  Post.joins(:tags).group("tags.name").count
  # => {"tag1" => 4, "tag2" => 2, "tag3" => 5}

.count
.max
.having 
  # like a .where clause for grouped queries

-- Joins --

Rails associations usually do the heavy lifting here,
  you probably won't need to use a .join usually.

-- N+1 queries --

The N+1 query problem:

  (Tables User and City exist)
  (User belongs_to a City)

  User.all.each do |user|
    puts user.city
  end

  User.all -> one query
  user.city -> one query

It's fine to grab a User attribute like "user.name"
Reaching through City association causes another query...

-- Eager Loading --

Rails' solution to the N+1 query problem!

  User.all.includes(:city).each do |user|
    puts user.city
  end

Grab + Store Users and Cities at the same time!
user.city = user.name (no query run)

.includes
  # takes name of associations you wanna eager load
  # User.all.includes(:city).each do |user|
  # eager loading done
  # chain with .where, .order
  # cannot be witnessed in server output

.pluck
  # Just gives resulting array from all that ^
  #  User.pluck(:name) # => ["Foo", "Bar", "Baz", "Jimmy-Bob"]

-- Scopes --

scope :important, -> { where(is_important: true) }
(allows you to do this)
if params[:important] == true

Scopes return Relations!

Can also be done as a class method:

  # app/models/post.rb
  ...
  def self.important
    self.where(is_important: true)
  end
  ...

Prefer using Scopes unless it gets too complex 'v'

-- Bare-metal SQL --

.find_by_sql
  # Last resort, it's basically hard-coding.